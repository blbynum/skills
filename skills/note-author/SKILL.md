---
name: note-author
description: Captures, retrieves, and maintains durable notes as atomic, greppable markdown. Notes about a project live in that project's own notes/ directory; notes with no project live in the personal vault, the configured vault directory (`vault-dir`). Use when the user asks to note, jot, save, write up, or capture something; when they ask what they know or wrote about a topic, or to look something up in their notes; and when they ask to review, clean up, merge, or re-index notes. Use when starting work on an unfamiliar project or question, to check whether notes already answer it. Use proactively at the end of work that produced a durable, reusable fact — a resolved configuration, a decision and the reason behind it, a procedure that worked — and offer to record it. Not for a document a reader will act on, such as a plan, a design, a report or a runbook; the doc-author skill writes and files those. Does not apply to Claude's own auto-memory directory, or to temporary scratch files.
compatibility: Uses git to find a project root.
metadata:
  harness: portable
  export: portable
  last-verified: "2026-11-02"
---

# Notes

A note must be useful to a reader with no memory of the conversation that produced it —
which includes you, in a later session.

Two failure modes destroy a collection of notes. Both are cheap to prevent:

- **Duplication.** The same fact lands in four notes under four names. Prevented by
  searching before every write.
- **Rot.** A note records a fact that later changed, and nothing marks it stale.
  Prevented by the `updated` and `confidence` fields, and by editing notes in place.

## Config

| Key | Required | Default | Purpose |
|---|---|---|---|
| vault-dir | yes | | directory of the personal vault, where notes with no project live |

Read `config.local.yaml` in this skill's directory before anything else.
A key missing there takes its Default from the table. If a required key is
missing or empty, stop: name the key and its purpose, and offer to write
`config.local.yaml` with the values the user gives. If a configured
directory does not exist, stop and say so; do not create it.

## Note or doc?

Before a write, apply the table in
[references/note-or-doc.md](references/note-or-doc.md); the docs skill
carries the same table. A text that a reader will act on, or that records a
decision, is a doc: hand it to the docs skill and say so. One piece of work
can yield both: the write-up is a doc, the facts it settled are notes.

## Where a note goes

**Notes about a project live with that project.** Decide by what the note is about, not by
where you are:

| The note is about | Location |
|---|---|
| A specific project — its tools, decisions, open work | `<project-root>/notes/` |
| Anything with no project — a home network, an account, a general technique | the personal vault: the configured vault directory (`vault-dir`) |

A project root is the git root, or the top of the project directory when there is no git.

**A project's `notes/` directory must be gitignored.** These are working notes, not product
documentation, and they carry personal and dated content. Before the first write:

```bash
git -C "<project-root>" rev-parse --show-toplevel   # in a repo?
git -C "<project-root>" check-ignore -q notes/      # already ignored?
```

If the project is a repo and `notes/` is not ignored, add it to `.gitignore` with a comment
saying why, and say you did.

Both locations use the same layout and the same note format:

```
<root>/
  INDEX.md      Every note, one line each. Read this first.
  TAGS.md       The tag registry. Reuse these tags.
  <slug>.md     Atomic notes, flat, kebab-case filenames.
```

Keep it flat. A flat directory plus `INDEX.md` plus `grep` retrieves faster than a
hierarchy. The filename is a durable identifier: pick a slug that stays true.

## Note format

```markdown
---
title: Z-Wave JS UI runs on an external server
created: 2026-08-15
updated: 2026-08-15
tags: [homelab, home-assistant]
confidence: verified
sources:
  - ssh zwave-host
---

Home Assistant does not run its own Z-Wave add-on. It connects to a
standalone Z-Wave JS UI instance on the host `zwave-host`.

## Details

...

## Related

- [[home-assistant-upgrades]]
```

The first paragraph is a standalone summary. Write it so a reader who reads no further
still gets the fact. Copy it, shortened to one line, into `INDEX.md`.

`confidence` takes one of three values, and you must not guess it:

| Value | Meaning |
|---|---|
| `verified` | You ran the command, read the file, or saw the output. |
| `reported` | The user or a document stated it. You did not confirm it. |
| `assumed` | Inferred from other facts. Mark the inference in the body. |

## Workflows

### Read, before you work

When you start on a project or a question that notes might already answer, look before
asking the user or rediscovering it:

1. If the project has a `notes/INDEX.md`, read it.
2. Read the two to five notes that look relevant, in full.
3. When the index gives you nothing, search the notes directory for a keyword, for example
   `grep -ril "<keyword>"`.

Report the `confidence` and `updated` values with any fact you use. Verify a `reported` or
`assumed` fact before you act on it.

### Capture

```
- [ ] 1. Decide the location: project notes/ or the personal vault (`vault-dir`)
- [ ] 2. Search that location for an existing note on this subject
- [ ] 3. Decide: new note, or edit an existing one
- [ ] 4. Write the note in the style below
- [ ] 5. Set confidence honestly
- [ ] 6. Update INDEX.md, and TAGS.md if you added a tag
- [ ] 7. Add Related links in both directions
```

**Step 2 is not optional.** Search the location for two or three keywords, for example
`grep -ril "<keyword>"`, and read `INDEX.md`. A near-duplicate found here saves a merge later.

**Step 3.** Edit the existing note when the new fact refines, corrects, or extends it.
Create a new note when the fact stands on its own and a reader would look for it under its
own name. When you edit, set `updated` to today, and correct stale text in place rather
than appending a contradiction.

**Step 7.** A link in one direction only is half a link. Add the link back.

### Maintain

Run this when the user asks for a cleanup, or when you notice drift. See
[references/maintenance.md](references/maintenance.md) for the merge, prune, and re-index
procedures.

## Style

Notes use a controlled English derived from ASD-STE100. The rules serve retrieval: short
sentences chunk cleanly, repeated nouns make `grep` work, and named actors remove ambiguity.

1. **One idea per sentence.** Instructions: 20 words maximum. Descriptions: 25 words.
2. **Active voice. Name the actor.**
3. **Repeat the noun.** Never start a sentence with a bare "it", "this", or "that".
4. **One term per concept, every time.**
5. **No phrasal verbs when one verb exists.** Write "configure", not "set up".
6. **Noun clusters: three words maximum.**
7. **One topic per paragraph, six sentences maximum.**
8. **Use a vertical list for three or more items.**
9. **Write full sentences.** Telegraphic notes decay fastest.
10. **No semicolons.** Write two sentences.
11. **Put the warning first.** Start with the hazard, then the instruction.
12. **Write absolute dates.** "Last week" is ambiguous six months later. Write "2026-08-08".

Three deliberate deviations, because notes are records rather than procedures: perfect
tenses are allowed when event order matters; the verbs "verified", "reported" and
"assumed" keep their distinct meanings; and technical names — hostnames, flags, paths,
error strings — pass through verbatim, never simplified.

Full rules and rewrite examples: [references/style-ste.md](references/style-ste.md).

## What not to write

- Facts the source of truth already records — code structure, git history, a config file
  the note would only mirror. Note the location and the surprise instead.
- Anything specific to the current conversation and dead after it.
- Standing instructions for how to work on a project. Those belong in the harness's
  always-loaded rule files for that project. A note is read on demand; a rule is always in
  context. Do not put rules in notes, and do not put notes in rules.

This skill is separate from Claude's auto-memory. Auto-memory holds facts about how to work
with the user. Notes hold the user's own knowledge.
