# Document kinds and their contracts

What each kind of software documentation must contain and must not, drawn
from the Diátaxis framework, the Good Docs Project templates, Write the
Docs, Google's engineering practice, and the conventions that maintainers
check for in a repository. Read the section for the kind you are writing;
the SKILL.md workflow decides which kind that is.

## Contents

- The four kinds at a glance
- Tutorial
- How-to guide
- Reference (general; CLI; configuration; HTTP API)
- Explanation
- README
- Changelog and release notes
- Architecture decision record (ADR)
- Contributing, security, and other community files
- Doc comments and docstrings, by language
- Files that are not this skill's: CLAUDE.md, AGENTS.md, llms.txt

## The four kinds at a glance

| | Tutorial | How-to guide | Reference | Explanation |
|---|---|---|---|---|
| Oriented to | learning | a goal | information | understanding |
| Form | a lesson | a series of steps | dry description | discussion |
| Reader is | at study, a beginner | at work, competent | at work, looking something up | at study, away from the keyboard |
| Must contain | a single reproducible path to a visible result | prerequisites, ordered steps, a check | every element, its type, default, constraints | context, alternatives, reasons, connections |
| Must not contain | explanation, choices, abstraction, extra information | teaching, digression, completeness for its own sake | instruction, opinion, speculation | steps, facts that belong in reference |
| Title form | "Getting started with X", "Your first X" | "How to <do the thing>" | the name of the thing | passes the test "About <topic>" |

Blurring these boundaries is where most documentation problems start.
Reference and explanation are both theory; a reference page that keeps
digressing into reasons and an explanation that keeps dropping into facts
each damage the other. Tutorials and how-tos are both practice; a how-to is a
recipe, not a cooking lesson.

## Tutorial

Purpose: give a beginner a learning experience that ends in basic
competence and confidence. The author, not the reader, is responsible for
the outcome, so the path must be safe and reliable.

Contract:

- Show the destination first: one sentence on what the reader will have
  built or done at the end, and roughly how long it takes.
- State prerequisites up front (tools, versions, accounts), then assume
  nothing else. An error on step four because step one forgot to mention a
  login is the classic tutorial failure.
- Use an input the reader has: a sample file in the repository, or one the
  tutorial tells them to create verbatim. Every shown output is produced
  from that input. Never show output from one file next to a command on
  another.
- Number only the reader's actions, one action per step; describe what the
  system does in prose under the step that caused it. Combine atomic
  actions that belong together into one step.
- Deliver a visible result early and after every step, and tell the reader
  what to notice ("the second line now reads…").
- One path, no choices, no alternatives, no options. Resist abstraction,
  generalisation, explanation, and extra information; link to the
  explanation and reference instead.
- Keep it to a session: somewhere under an hour and under about seven
  primary steps. Longer than that is two tutorials.
- End with what was learned and where to go next.

The tone may be warmer than other kinds, and "you will" is acceptable when
introducing a step.

## How-to guide

Purpose: directions that take an already-competent reader through a
real-world task to a result.

Contract:

- One goal per page, named in the title in the form "How to <verb> <thing>".
- Written from the reader's situation, not the product's structure:
  "How to rotate the signing key" rather than "The key subsystem".
- Prerequisites first, as a plural, bulleted "Prerequisites" section, never
  inside a note.
- Steps in a logical sequence, each an imperative, each one action; the
  guide may branch ("If you use X, do Y") where real tasks branch.
- A verification step at the end that shows the reader the task worked.
- Usability over completeness: omit what the task does not need. Give the
  primary way to do a thing; if a second way is needed, it gets its own
  section or page.
- No teaching, no digression; link to the explanation for the why.

## Reference

Purpose: neutral technical description of the machinery, consulted rather
than read. Reference is the most-used documentation in observation studies
and the kind developers judge by completeness and accuracy.

Contract for all reference pages:

- Describe and only describe. No instructions, no opinion, no speculation,
  no reasons; those go to how-tos and explanation.
- Complete: every element that exists is listed, including deprecated ones
  (marked, with the replacement named).
- Consistent: the same entry structure for every element, in a scannable
  form (table or definition list), in an order that mirrors the product
  (the order of the help output, the order of the schema, alphabetical
  when nothing else is natural).
- Each entry states type, default, allowed values or constraints, and
  effect. Say what happens on an invalid value when the code defines it.
- Examples are welcome; they illustrate an entry and stay short.
- State the version the page describes.

CLI reference, in addition:

- A synopsis line in the project's syntax notation: `[optional]`,
  `{a|b}` for a required choice, `...` for repeatable; then one entry per
  command, then per option with its short and long form, argument
  placeholder, default, and effect.
- Global options separate from command options; environment variables and
  config-file precedence in their own section or on the configuration page.
- Exit codes, with meanings. The conventions for reading standard input
  and several inputs, and the behavior when nothing matches.

Configuration reference, in addition:

- The resolution order (flag, environment variable, project file, user
  file, built-in default), stated once near the top, with whether sources
  merge or the first found wins.
- A complete example file that parses, then one entry per key with type,
  default, and effect.
- What happens on an unknown key, a missing file, and an invalid value.

HTTP API reference, in addition, per endpoint:

- What it does, in plain language, first.
- Authentication and required headers.
- Every parameter with type, required or optional, allowed values, and
  format (dates, arrays, enums); the error cases it can return.
- A full example request and response, with real-looking values that
  satisfy the constraints; where a call depends on a value from another
  call, show how to get it. Controlled studies find that without such
  examples professional engineers mis-type parameters and omit required
  headers at high rates.
- Generate from the OpenAPI description when one exists; a hand-written
  copy drifts.

## Explanation

Purpose: a discursive treatment of a topic that gives understanding and can
be read away from the product.

Contract:

- Title passes the test of an implicit "About…" in front of it.
- Provide context and background; make connections, including to things
  outside the immediate topic; consider alternatives and counter-examples;
  admit opinion and perspective, labelled as such.
- No instructions and no reference facts beyond what the discussion needs.
- Keep it bounded: explanation tends to absorb everything; when it starts
  describing the machinery, that part belongs in reference.
- Architecture overviews, design rationale, and "how it works" pages are
  explanation. A design document that proposes a decision is an ADR or a
  design doc, below.

## README

The README is the project's landing page: the first file read and, for a
small project, the only documentation. It is a composite that holds a
miniature of each kind and links out when the project has more.

Contract (the five things readers look for, in this order):

1. **What it is and who it is for.** A short description first (under about
   120 characters), then the problem it solves and why someone would use
   it. State value before technology.
2. **Install.** A code block with the command that works for the common
   case; keep it to a few lines and link to a page for the rest.
3. **Usage.** A code block with a common example and its expected output;
   a quick start the reader can reproduce. Show the gotcha a new user hits
   first (a default they will not expect) here, in plain text, not in a
   note.
4. **Where to get help and more docs.** Links to the docs tree, issue
   tracker, support channel.
5. **Who maintains it and how to contribute**, with the license last.

Rules:

- Drop every section that has nothing to say. No empty Contributing, no
  Roadmap of wishes, no badges that assert nothing the project checks.
- Relative links to files in the repository; they survive clones and forks.
- The title matches the repository, directory, and package name.
- Keep the README itself short and link out; a README past a few screens
  is a docs tree that has not been split yet.
- A paused or abandoned project says so at the top.
- Configuration, full option tables, and architecture go to their own pages
  once they exceed a short section.

## Changelog and release notes

A changelog is a curated, reverse-chronological list of notable changes per
version, written for humans. It is not a commit log.

Contract:

- File `CHANGELOG.md` at the repository root, header "All notable changes
  to this project will be documented in this file", a statement of the
  format followed and whether the project uses semantic versioning.
- An `Unreleased` section at the top that collects changes until a release;
  at release time it becomes the new version's section (heading and date)
  and a fresh empty `Unreleased` section goes above it.
- One section per version, latest first, heading `[x.y.z] - YYYY-MM-DD`,
  linkable; a yanked release stays, marked `[YANKED]`.
- Within a version, group entries by type, in this set: `Added`, `Changed`,
  `Deprecated`, `Removed`, `Fixed`, `Security`.
- If nothing else, list every deprecation, removal, and breaking change,
  with what to do instead. Upgrading must be painless to assess.
- Write each entry as the noteworthy difference for the user, often one
  entry for several commits; link the entry to its pull request or issue
  where the project does that.
- Every version gets an entry; a partial changelog misleads more than none.

When commits follow Conventional Commits (`feat:`, `fix:`, `BREAKING
CHANGE:`), use them as the raw material for the curated entries, not as the
entries.

Release notes are a different artifact: customer-facing, plain language,
per release, with a summary, new features, improvements, fixes (what was
fixed and why it matters, not how), known issues, and deprecations with
dates. Write both only when the project publishes both.

## Architecture decision record (ADR)

An ADR captures one architecturally significant decision and its reasoning
for a future reader: a change to structure, dependencies, interfaces,
non-functional properties, or construction techniques, or anything hard to
reverse.

Contract:

- One decision per record; one or two pages; numbered monotonically in the
  project's decisions folder (`docs/decisions/0007-short-title.md` or the
  existing convention); numbers never reused.
- Title: a short noun phrase naming the decision.
- Status and date: proposed, accepted, rejected, deprecated, or superseded
  by a named record.
- Context: the forces in play (technical, organisational, project), stated
  neutrally, including the ones in tension.
- Decision: "We will…", in full sentences, active voice.
- Options considered, with the reasons for and against each, when more than
  one was live.
- Consequences: the resulting situation, all of it, the bad with the good;
  what becomes easier and harder; follow-up work it creates.
- Accepted records are immutable. A reversal is a new record that
  supersedes the old one, linked both ways; the old record stays.
- Record the why, not the how; an ADR is not a design guide or an
  implementation plan.

## Contributing, security, and other community files

- `CONTRIBUTING.md` (root, `docs/`, or `.github/`): how to set up a
  development environment, run the tests, and submit a change; what makes
  a good issue or pull request; where to ask; links to the code of conduct.
  Hosting platforms link it when someone opens an issue or pull request.
- `SECURITY.md`: supported versions and how to report a vulnerability
  privately.
- `LICENSE`: one standard license; the single item most decisive for
  adoption and contribution in open source.
- `CODE_OF_CONDUCT.md` only with the intent and ability to enforce it.

## Doc comments and docstrings, by language

Common contract: the public API gets a doc comment; the first line is a
one-line summary that tools reuse in indexes; the body says what the symbol
does, its arguments, return value, side effects, errors raised, and the
constraints on calling it; implementation details go in comments inside the
body, not in the doc comment; never restate the signature or describe the
code line by line. Where the toolchain can run examples in doc comments,
write them to run.

- **Python** (PEP 257, Google style): triple double quotes; a one-line
  summary ending in a period, phrased as a command ("Return the user's
  display name.") or descriptively, consistent within a file; a blank line; then
  `Args:`, `Returns:` (omit when the function returns only `None`),
  `Raises:`, and for classes `Attributes:`. Mandatory for public API,
  anything nontrivial in size, and non-obvious logic. Module docstring
  first in the file describing contents and usage. Examples as doctests
  when the project runs them.
- **Go**: every exported name gets a doc comment, a complete sentence that
  starts with the symbol's name ("Open returns…"); package comment
  starts "Package foo …"; a paragraph starting `Deprecated:` marks
  deprecation and names the replacement; `ExampleXxx` functions with
  `// Output:` comments are compiled and run with the tests.
- **Rust**: all public items; summary line, blank line, details, at least
  one example; standard headings `# Examples` (plural even for one),
  `# Panics`, `# Errors`, `# Safety`; summary in third-person present
  ("Returns the…"); examples are compiled and run by `cargo test`.
- **Java** (Javadoc): the first sentence is the summary; main description
  then block tags `@param`, `@return`, `@throws`, `@deprecated` with when
  and what to use instead.
- **TypeScript and JavaScript** (TSDoc, JSDoc): `/** … */` immediately
  before the declaration; summary, then `@remarks` for detail, `@param`,
  `@returns`, `@throws`, `@example`, `@deprecated`.
- **C and C++** (Google style): declaration comments describe what and how
  to use, including whether pointers may be null and ownership;
  definition comments explain the tricky parts; prefer the why over the
  what.

## Files that are not this skill's: CLAUDE.md, AGENTS.md, llms.txt

- `CLAUDE.md` and `AGENTS.md` are instruction files for coding agents, not
  documentation for people: build commands, conventions, layout, standing
  rules, kept short. Do not apply this skill's contracts to them; a
  request to write or change one is not documentation work.
- `llms.txt` is a proposed root-level Markdown index of a docs site for
  language-model readers, with `.md` variants of pages. Several large
  vendors publish one; measured use by crawlers and agents is near zero in
  every log study to date, and no study measures coding agents reading
  `.md` page variants during a session. Add one only when the user asks or
  the docs generator already produces it; claim no benefit for it.
