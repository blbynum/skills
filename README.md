# skills

Two Agent Skills for writing documents and keeping notes. `doc-author`
writes, files, and maintains documents for a reader. `note-author` records
durable facts as small Markdown files that you can search.

Each skill is a directory in `skills/` with a `SKILL.md` under the
[Agent Skills standard](https://agentskills.io/). The repository is not
installed into a harness. `link.sh` links it into one.

## Contents

- [Install](#install)
- [Set the config](#set-the-config)
- [Update](#update)
- [What is here](#what-is-here)
- [Portability](#portability)
- [The provenance ledger](#the-provenance-ledger)
- [Requirements](#requirements)
- [Versioning](#versioning)

## Install

1. Clone the repository to a location that stays. The links point into
   the clone, so they break if you move or delete it.

   ```sh
   git clone git@github.com:blbynum/skills.git ~/src/skills
   cd ~/src/skills
   ```

2. Run the link script for your harness:

   ```sh
   ./link.sh --harness claude-code
   ```

   Output for a clone at `~/src/skills`:

   ```text
   Repository: /Users/you/src/skills
   Harness:    Claude Code (claude-code)
   Skills:     /Users/you/.claude/skills
     linked doc-author
     linked note-author

   The links point into /Users/you/src/skills.
   The files stay there; the harness reads them through the links.
   To change a skill's settings on this machine, edit config.local.yaml in
   the skill's directory, /Users/you/src/skills/skills/<name>/. Git ignores that file.
   To get updates, run "git pull" in /Users/you/src/skills, then run this command again:
     /Users/you/src/skills/link.sh --harness claude-code
   It links added skills and rules, and removes the links to deleted ones.
   ```

3. Set the config, as the next section says. Both skills stop until their
   required key has a value.

`./link.sh --list` shows the other harness ids. To link the skills into
one more harness, run the script again with that id.

To unlink, delete the symlinks in the harness's skills directory. The
clone does not change.

## Set the config

Each skill reads `config.local.yaml` in its own directory. Git ignores
that file, so each machine keeps its own values and a pull does not change
them. If a required key is absent, the skill stops and offers to write the
file with the values that you give.

`skills/note-author/config.local.yaml` names the directory of your notes:

```yaml
vault-dir: ~/notes
```

Create the directory first. The skill stops if the directory does not
exist.

`skills/doc-author/config.local.yaml` names the skill that files your
documents:

```yaml
doc-platform: my-wiki-skill
```

This repository holds no platform skill. You supply one, and it must
implement [the platform contract](skills/doc-author/references/platform-contract.md).
`doc-author` stops until this key has a value, also for a document that
lives in a repository, such as a README.

## Update

1. Pull the changes in the clone:

   ```sh
   git -C ~/src/skills pull
   ```

2. Run the command that the last run of `link.sh` printed, for example:

   ```sh
   ~/src/skills/link.sh --harness claude-code
   ```

A pull changes the text of a linked skill immediately, because the links
point into the clone. The second step links added skills and removes the
links to deleted ones. When nothing changed, the script writes
`no changes`.

## What is here

| Path | What it does | Config keys |
|---|---|---|
| `skills/doc-author/` | Writes, files, and maintains documents for a reader: plans, design docs, reports, runbooks, and the documentation that ships with software. | `doc-platform` (required) |
| `skills/note-author/` | Captures, retrieves, and maintains durable notes as atomic Markdown files. | `vault-dir` (required) |
| `link.sh` | The link script, a copy from the meta-skills repository. It has its own version and its own copy of the license notice. | none |
| `AGENTS.md` | Instructions for agents that work on this repository: the version procedure. `CLAUDE.md` and `GEMINI.md` import it. `link.sh` does not link it. | none |
| `VERSION` | The version of the repository. | none |

Link both skills. Each one names the other as the place for work that it
does not do, and both carry the same table in `references/note-or-doc.md`.

## Portability

Each `SKILL.md` declares `metadata.harness: portable`. The portability
check of 2026-11-02 found no dependence on one harness. It found only
subject matter: `doc-author` lists `CLAUDE.md` and `AGENTS.md` as files
that it does not write, and `note-author` says that it does not apply to
the auto-memory of Claude Code.

The skills have run in Claude Code. No run in another harness is on
record.

## The provenance ledger

Each skill keeps the sources behind its guidance in a `sources.md` in its
own directory. `SKILL.md` does not link that file, so the file costs no
context when the skill loads.

## Requirements

- A harness that reads the Agent Skills standard.
- A POSIX shell (`sh`) and `git`, for `link.sh`.
- `git`, for `note-author`, to find the root of a project.
- A skill that implements the platform contract, for `doc-author`.

## Versioning

The file `VERSION` holds the version of the repository as
`major.minor.snapshot`. `master` is the development branch.

Every change that merges into `master` gets a new version. The effect of
the change on a person who already has the repository linked into a
harness sets the level:

| Level | The change | Examples |
|---|---|---|
| Major | stops something that the person had from working, after `git pull` and a new run of `link.sh` | a skill removed or renamed; a config key renamed or made required |
| Minor | adds something that the install can use, and breaks nothing | a new skill; a new optional config key |
| Snapshot | all other changes | guidance edits, fixes, references, documentation |

If more than one level fits, use the highest.

A branch with the name of each version marks the last state of that
version on `master`. To use an earlier version, check out its branch in
the clone, for example `git checkout 1.4`. The links point into the clone,
so the harness then reads that version.

`link.sh` has a version of its own, from its source repository.
`./link.sh --version` prints it. This repository never edits `link.sh`. A
change replaces the whole file with a newer copy from its source.

`AGENTS.md` holds the same policy as steps for agents, with the version
check to do immediately before a merge.
