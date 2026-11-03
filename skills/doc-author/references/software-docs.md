# Software documentation

Documentation that ships with software, read from the docs skill when the
document kind is a README, a tutorial, a how-to guide, a reference page, an
explanation page, an ADR, a changelog, a contributing guide, or a doc
comment. Its home is the repository; the workflow below places it there.

## Contents

- Why content, not presentation, decides
- Workflow: reader and kind; source of truth; placement; the kind's contract; verify; report
- Reviewing an existing docs tree
- Bounds
- Failure modes

What blocks a developer in documentation is content, not presentation:
surveys of professional developers (IBM 2015, ABB 2020) rank ambiguity,
incompleteness, incorrectness, and staleness as the problems that made them
abandon an API, and no presentation problem ever did. Incorrect documentation
is worse than none. Developers of every style start a task from a code
example and read it as a recommendation. And a document that mixes kinds (a
tutorial that explains, a reference that instructs) serves neither reader.
This reference exists to make those four facts the defaults.

Scope boundaries: sentence-level style and reader-facing structure (answer
first, labels, signal budget) are not this skill's job; a loaded style
rule or structure skill, where one exists, governs them. This reference adds
what software documentation needs: the document kind and its contract, the
source of truth, the conventions of developer docs, and the verification
loop.

## Workflow

Copy this checklist into the response and check items off as you go:

```
- [ ] 1. Name the reader, the task, and the document kind
- [ ] 2. Read the source of truth before writing a claim
- [ ] 3. Survey what exists; decide where this lives and what owns each fact
- [ ] 4. Draft to the kind's contract
- [ ] 5. Verify: run every example, check every link and name, compare
- [ ] 6. Report what was verified, what was not, and what the code got wrong
```

Scale it to the request. A docstring needs steps 2, 4, and 5 in a few tool
calls; a docs tree needs all of it, page by page.

### 1. Name the reader, the task, and the kind

Write one line for yourself: who reads this, what they are trying to do, and
how much they already know. Then classify the content with two questions:
does it serve **action** or **cognition**, and does it serve the reader's
**acquisition** of skill (study) or **application** of skill (work)?

| The content informs | and serves | so it is | and answers |
|---|---|---|---|
| action | acquisition | a **tutorial**: a lesson | "Can you teach me to…?" |
| action | application | a **how-to guide**: steps to a goal | "How do I…?" |
| cognition | application | **reference**: dry description | "What is…?" |
| cognition | acquisition | **explanation**: discussion | "Why…?" |

Map the user's words onto the kinds rather than onto page titles: "getting
started" is a tutorial unless the readers are already competent, in which
case it is a quick how-to; "document the flags / the API / the config" is
reference; "how it works / why we did it this way" is explanation; a page
written because people keep asking one question ("which setting wins?")
is a how-to or a short explanation that answers that question first and
links to the reference for the key-by-key detail, not a second reference.
READMEs, changelogs, ADRs, and doc comments are composite artifacts with
their own contracts; [doc-types.md](doc-types.md) has
all of them.

One document, one kind. The README is the exception: it is a landing page
that holds a miniature of each kind and links out when the project has more.
Do not build empty structure. Write the smallest set of pages that serves the
named reader; for a small tool that is often the README alone.

### 2. Read the source of truth before writing a claim

Every stated behavior comes from something you read or ran, never from what
the project "probably" does. Before drafting, read what the document will
describe:

- The code that implements it, and its tests. Defaults, precedence rules,
  error paths, and exit codes live in the config loader, the argument parser,
  and the tests, not in the function you were pointed at.
- The tool's own output: `--help`, `--version`, a schema, an OpenAPI file,
  generated docs.
- The project's history where the document is about change: tags, the
  changelog, the commits since the last release, the issue that prompted the
  request.
- The existing docs, so you can find what is already stated and what is
  stale.

Collect the facts the kind needs (every flag, key, default, environment
variable, exit code, error message, version, and the install command that
works) before you write prose around them. When the code and the existing
docs disagree, the code wins and the disagreement is a finding for step 6.
When you cannot read or run the thing a sentence describes, leave the
sentence out rather than guess; a gap the reader can see is safer than a
confident error.

### 3. Survey what exists; decide placement and ownership

- Find the project's documentation conventions and match them: heading case,
  placeholder style, admonition syntax, the docs generator and its config
  (`mkdocs.yml`, `conf.py`, `docusaurus.config.*`), linters (`.vale.ini`,
  `.markdownlint*`), where pages live, how they are linked, whether a
  `CHANGELOG.md` or `docs/decisions/` exists. A second convention in one repo
  is a defect.
- Decide which page owns each fact. A fact lives in one place and other
  pages link to it; the CLI reference does not re-document the config file
  if a configuration page exists. Accept repetition only where a reader
  would otherwise have to leave the page in the middle of a task, and then
  repeat the critical sentence, not the section.
- Place documentation next to what it documents: README at the repository
  root, reference beside the code or in the project's docs tree, doc
  comments on the public symbols, ADRs in the decisions folder the project
  already uses. Docs under source control, reviewed with the code they
  describe, are the ones that stay current.

### 4. Draft to the kind's contract

Read [doc-types.md](doc-types.md) for what the kind
must contain and must not, and
[style-rules.md](style-rules.md) for the conventions
developer-documentation style guides agree on: person, tense, headings,
steps, code samples, command-line syntax, placeholders, link text, notices.
The rules that most often decide whether a page works:

- **Examples are the entry point.** Make each one complete and copy-paste
  runnable, show the real output it produces, and prefer a small example that
  demonstrates a usage pattern (two or three calls that go together) over a
  one-call snippet. Readers treat an example as the recommended way, so show
  best practice, and explain it: an example with no explanation was a top
  complaint in every survey.
- **A tutorial is reproducible.** It uses an input the reader has (a file in
  the repository, or one the page tells them to create), every shown output
  comes from that same input, each step produces a visible result, and the
  path has no choices and no explanation. The author carries the
  responsibility for the reader's success.
- **Reference is complete and austere.** It describes; it does not instruct
  or opine. It mirrors the structure of the thing (one entry per flag,
  option, key, endpoint, or symbol, in the order the code or the help
  output uses) and states the default, the type, and the constraints of
  each.
- **A how-to assumes competence.** Steps toward one goal, written from the
  reader's situation, with the prerequisites first and the verification at
  the end; usability over completeness.
- **Timeless wording.** No "currently", "new", "now", or "soon"; no future
  or unreleased features. Anchor anything time-bound to a version or a date.
- **Doc comments document the public API,** one summary line first, what
  the symbol does and returns rather than how, in the language's own
  convention (the reference file has them).

### 5. Verify: run, check, compare

A verification loop, repeated until clean, is what separates documentation
from plausible prose:

1. Run every command and code example in the document, from the directory
   the reader would be in, and paste the real output where the document
   shows output. Where they differ, fix the document, or record a code
   problem for step 6 if the code is what is wrong. Where the language has
   executable documentation tests (Python doctest, Rust doc tests, Go
   example functions) and the project uses them, write the example in that
   form so the test suite keeps it true.
2. Check every name against the source: each documented flag, option, key,
   function, exit code, and error message exists, with the stated default,
   in the code you read. Search the code for it.
3. Check the mechanics: every link and anchor resolves (relative links
   inside the repository), every code fence has a language tag, headings do
   not skip levels, the page builds without warnings in the project's docs
   tool if there is one, and the project's own linters pass on it.
4. State the version or commit a reference page describes when the project
   has versions; the page is a claim about one version of the software.

When a run needs something you do not have (credentials, a network, a
service, a long build), write the example from the code, run what you can,
and name the unrun examples in the report. Do not silently skip a run, and
do not refuse to write because a run is impossible.

### 6. Report

Say what you wrote and where; what you ran and what you could not; every
disagreement between the code and its documentation, and every code problem
the writing uncovered (a crash, a missing error message, an undocumented
default), left in the code for the user to decide on; and the judgment calls
you made (the kind, the placement, which page owns a fact). Offer, rather
than add unasked, the maintenance that would keep the docs true: a link
check or prose lint in CI, a doctest, a freshness line.

## Reviewing an existing docs tree

When the request is to assess or restructure documentation rather than
write a page, classify before you move anything: for each page, ask the two
compass questions and note where a page mixes kinds (the option table in
the tutorial, the reasons in the reference), where two pages own the same
fact, and where a stated behavior no longer matches the code. Report that
map with the smallest set of moves that fixes it, in the order a reader
would feel them. Improve iteratively: pick one page, assess it, decide the
single next action, do it, publish, repeat. Do not propose a four-folder
reorganisation of a docs set that only needs its tutorial split from its
reference.

## Bounds

The defaults above overshoot in predictable ways; stop short of these:

- Verification gates publishing, not writing. Write from the code and label
  what you could not run; never return nothing because a run was blocked.
- Kind discipline is not a folder structure. Four empty directories are
  worse than one good README; split a page only when a reader of one kind
  would have to skip past material of another.
- Reference austerity does not strip examples; it strips opinion and
  instruction. Explanation and ADRs are where the reasons go.
- Match the length to the kind: a how-to is as short as the task allows; a
  reference is as long as completeness requires.
- Change what was asked. Stale pages, crashes, and missing docs you found
  elsewhere are findings in the report, not edits.

## Failure modes

| Symptom | Fix |
|---|---|
| Tutorial commands use a file the reader does not have | Use the repository's sample input or tell the reader to create one; regenerate every shown output from it |
| Option table or format spec inside a getting-started page | Move it to the reference page; link from the tutorial |
| The same config keys documented on two pages | Pick the owning page; replace the copy with a link and one sentence |
| Shown output written by hand | Run the command; paste what it printed |
| Flag, key, or default stated from memory | Search the parser or loader; correct or remove |
| "Currently", "new", "will soon", a roadmap item | Delete, or anchor to a version |
| Prerequisite or required step inside a note | Move it before the steps as plain text |
| Reference page that explains why or recommends | Move the reasoning to an explanation page or an ADR |
| Changelog pasted from `git log` | Curate: notable changes, grouped by type, deprecations and breaking changes first |
| Docstring restating the signature or the algorithm | Say what it does and returns, the contract, the exceptions |
| README with empty Contributing, Roadmap, badge rows | Delete sections with nothing to say |
