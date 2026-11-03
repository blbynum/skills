---
name: doc-author
description: >-
  Writes, files and maintains documents for a reader: plans, design docs,
  PRDs, reports, research write-ups, runbooks and guides on the configured
  document platform, and the documentation that ships with software
  (READMEs, guides, reference pages, ADRs, changelogs, doc comments) in its
  repository. Decides doc or note, picks the kind, drafts to its contract,
  verifies, then files it with a home, an owner and a status; or rewrites,
  restructures and retires an existing doc. Use when asked to write, file, publish, rewrite,
  restructure or retire a doc, plan, design, PRD, report, runbook or
  README; to document a module, flag or config file; to add docstrings; or
  to review a docs tree. Use proactively when work produced a document for
  a reader, to offer to file it. Not for a note (the note-author skill), for a
  small edit to a document already on the platform (the platform skill
  makes it), for the structure of a chat reply, for a project-directory
  README written for agents, for CLAUDE.md or AGENTS.md, or for a diagram.
compatibility: Needs no command-line tool. Needs a skill that implements the platform contract, named by doc-platform.
metadata:
  harness: portable
  last-verified: "2026-11-02"
---

# Documents

A document is a text that someone other than its author acts on, or that
records a decision. What makes it a document is not polish: it is a home,
an owner, a status and a reader. Every document passes through this skill
once, on the way to its home, so that no document ends as a dated loose
file in a project directory, and no second document grows beside the
first.

The craft of writing comes from the references and from whatever structure
skill and style rule are loaded. This skill adds the decisions around the
writing: doc or note, which kind, which home, what exists already, and the
hand-off to the platform.

## Config

| Key | Required | Default | Purpose |
|---|---|---|---|
| doc-platform | yes | | skill that implements the platform contract in `references/platform-contract.md`; where documents that do not ship with code are filed |

Read `config.local.yaml` in this skill's directory before anything else.
A key missing there takes its Default from the table. If a required key is
missing or empty, stop: name the key and its purpose, and offer to write
`config.local.yaml` with the values the user gives. If a configured
directory does not exist, stop and say so; do not create it.

## Workflow

Copy this checklist into the response and check items off as you go:

```
- [ ] 1. Doc or note? Apply the table; hand a note to the note-author skill
- [ ] 2. Name the reader, the task, and the kind
- [ ] 3. Decide the home: the repository, the platform, or the private area
- [ ] 4. Find what exists there before you write
- [ ] 5. Draft to the kind's contract; verify every claim and example
- [ ] 6. File it: the platform skill, or a place in the repository
- [ ] 7. Report: link, breadcrumb, status; what was verified and what was not
```

Scale it to the request. A one-line fix to an existing doc needs steps 4,
5 and 7 in a few tool calls. A new design doc needs all of it.

### 1. Doc or note?

Read [references/note-or-doc.md](references/note-or-doc.md) and apply its
table. Three cases come up often:

- A research write-up with a recommendation is a doc; the facts it settled
  are notes. Write the doc here, then hand the facts to the note-author skill.
- An assessment, a plan or a report that the user will read later as "the
  team" is a doc, however rough.
- Session progress is scratch. It is neither, and it is not filed.

When the text is a note, hand it to the note-author skill and say so.

### 2. Name the reader, the task, and the kind

Write one line for yourself: who reads this, what they will do with it,
and how much they know. Then pick the kind. Two families:

**Documentation that ships with software.** README, tutorial, how-to
guide, reference, explanation page, ADR, changelog, contributing guide,
doc comment. Read [references/software-docs.md](references/software-docs.md),
[references/doc-types.md](references/doc-types.md) and
[references/style-rules.md](references/style-rules.md), and follow the
workflow in the software-docs reference from there; it covers the rest of
this checklist for that family, and its home is the repository.

**Documents on the platform.** Each kind has a contract: what the reader
must find, in this order.

| Kind | The reader must find |
|---|---|
| Plan | The goal and what done looks like; the facts it rests on; the steps in order, each with its owner and date where one exists; what is out of scope |
| Design doc | The problem and its constraints; the options considered; the decision and why; the consequences; what is still open |
| PRD | The problem and who has it; the users; the requirements, each testable; what is out of scope; how success is measured |
| Report, research write-up | The bottom line first, with its confidence; the findings, each with its evidence; disagreements; what remains unknown; sources |
| Runbook | When to use it; preconditions; the steps, one action each, with the check after each; rollback; who to tell |
| Guide | What the reader will be able to do; prerequisites; the path, with no choices; verification; where to go next |
| Decision record | The decision in one sentence; the context; the alternatives; the consequences; the date and who decided |

A document is one kind. A page that mixes a plan with a report serves
neither reader; split it, and link the two.

### 3. Decide the home

A document that must stay in step with a version of the code lives in the
repository, with the code, reviewed with it. Everything else lives on the
platform.

| The document | Its home |
|---|---|
| README, tutorial, how-to, reference, explanation page, ADR, changelog, contributing guide, doc comment | The repository: README at the root, pages in the docs tree, ADRs in the decisions folder, comments on the symbols |
| Plan, design doc, PRD, wireframe notes, report, research write-up, runbook, guide, decision record outside code | The platform: the container for its subject, under the group its family lives in |
| A document only the author should see | The platform's private area |

A PRD or a design precedes the code and does not version with it, so it
goes to the platform even for a software project. When the project later
has a repository and the design becomes an ADR, that is a new document in
the repository, linked from the old one.

### 4. Find what exists

Before you write, look for the document that already covers the subject:
on the platform, ask the platform skill to find by title and by text; in a
repository, survey the docs tree as the software-docs reference says. When
one exists, update it in place and correct stale text rather than append a
contradiction. Create a second document beside it only when the reader
would look for the new one under its own name, and then link both ways.

### 5. Draft and verify

Draft to the kind's contract. Every stated fact comes from something you
read or ran in this session, or from the user; a sentence you cannot
ground is left out, and the gap is named in the report. Dates are
absolute. Nothing is "currently" or "soon". Every example runs. Every link
resolves. The body starts below the title: no level-1 heading, since the
platform and most repositories carry the title as a field.

Then read the draft as the named reader, with the task in hand, and remove
what the task does not need. Depth goes behind the main path: a later
section, or a linked document.

### 6. File it

For a repository document, place it as the software-docs reference says.

For a platform document, hand it to the platform skill (`doc-platform`)
with what [references/platform-contract.md](references/platform-contract.md)
lists: the title, the body, the home as a container and a parent or as a
description of where it belongs, the status (published unless the user
asked for a draft), the owner where the platform records one, and the
related documents to link. The platform skill proposes the breadcrumb
before it files, when the home was a description; confirm it with the
user when it is not obvious.

When the new document replaces an old one, archive the old one and put a
link to the new one in its first line; never leave two current documents
on one subject.

### 7. Report

Say what you wrote, the link and the breadcrumb, the status and the owner;
what you ran or checked and what you could not; what the read-back
changed; and the judgment calls: the kind, the home, and any document you
updated instead of creating. When the work also produced facts worth a
note, say so and offer the note-author skill.

## Maintaining documents

A small addition or correction to a document already on the platform can
go straight to the platform skill, which finds the document and patches
the passage. This skill handles the changes that touch the kind, the home
or the status, or that rewrite a section: they go through steps 4, 6 and
7. Update in place. Move when the home was wrong, and say the old and the
new breadcrumb. Archive when the document is no longer current, and link
its replacement; archiving keeps it searchable with a marker, which is the
end state a document should reach. Delete only when the user asks for
that document to be deleted.

A review of a whole docs tree, or of a collection, follows the "Reviewing
an existing docs tree" section of the software-docs reference: classify
every page before anything moves, report the map, and make the smallest
set of moves that fixes it.

## Receiving a document from another skill

A skill that produces a document hands it here with its kind, its reader,
its title, its body, and the project it belongs to. Start at step 3; the
producing skill has done steps 1 and 2. Report back the link and the
breadcrumb so the producing skill can cite them.

## Bounds

- Verification gates filing, not writing. Write from what you read and
  label what you could not check; never return nothing because a run was
  blocked.
- Kind discipline is not a tree. Split a page only when a reader of one
  kind would have to skip past material of another.
- Change what was asked. Stale documents and gaps you find elsewhere are
  findings in the report, not edits.
- Never file scratch, and never paste a secret into a document: name where
  it lives instead.
- A new container on the platform is a structural change: the platform
  skill asks before it creates one.

## Failure modes

| Symptom | Fix |
|---|---|
| A report saved as a dated loose file in the project directory | File it on the platform under a stable title; the date goes in the body |
| An assessment or a plan offered as "a note" | It has a reader; it is a doc. File it, then offer notes for the facts |
| A second document on a subject that already has one | Find first; update the existing one, or link both ways |
| A level-1 heading at the top of the body | The title is a field; start the body with text or a level-2 heading |
| A document with no owner or status | Set both when you file; ask when the owner is not the user |
| A document that links to the notes store | Compose the content into the document; notes are not for readers |
| Two current documents on one subject after a rewrite | Archive the old one and link forward from its first line |
