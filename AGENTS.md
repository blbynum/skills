# skills: instructions for agents

<!-- last-verified: 2026-11-02 -->

These instructions are for agents that work on this repository. They do
not ship to users: keep this file at the repository root, never in
`skills/` or `rules/`, and never link it into a harness. `CLAUDE.md` and
`GEMINI.md` import this file for the harnesses and versions that do not
read `AGENTS.md` directly.

## Versioning

`VERSION` at the repository root holds the version as
`major.minor.snapshot`. `master` is the development branch. Keep this
section and the "Versioning" section of `README.md` in agreement.

1. Give every change that merges into `master` one new version. Set it in
   `VERSION` on the change's branch. A helper branch that merges into a
   change's branch gets no version of its own.
2. Pick the level from the change's effect on a person who already has
   the repository linked into a harness. If more than one level fits, use
   the highest.
   - Major: the install breaks, or needs more than `git pull` and a new
     run of the link script. Examples: a skill or rule removed or
     renamed; a config key removed, renamed, or made required; a link
     script command that worked before now fails.
   - Minor: the install keeps working and gains something. Examples: a
     new skill or rule; a new optional config key; a new link script
     option; a skill that does a new kind of task.
   - Snapshot: every other change: guidance edits, fixes, references,
     evals, documentation.
3. Immediately before the merge, check the version again; another change
   can take the number first. Fetch, read `VERSION` on `master`, and set
   the branch's `VERSION` to master's version plus one step at the
   change's level:
   - Snapshot: `X.Y.S` becomes `X.Y.(S+1)`. If the branch's snapshot is
     less than or equal to master's snapshot, it must change to master's
     snapshot plus one.
   - Minor: `X.Y.S` becomes `X.(Y+1).0`.
   - Major: `X.Y.S` becomes `(X+1).0.0`.
   Commit that change before the merge.
4. Before the merge, leave a branch named after master's current version
   at master's tip:
   - For a snapshot change, make sure the branch `X.Y.S` (for example
     `1.4.2`) exists there. Create it if it does not exist.
   - For a minor or major change, create the branch `X.Y` for the old
     minor version (for example `1.4`). For a major change, also create
     the branch `X` (for example `1`). Then delete the snapshot branches
     of the old minor version (`1.4.0`, `1.4.1`, and so on). Each one is
     an ancestor of `X.Y`, so no commit is lost.
5. Never delete or move a major or minor branch. When `master` is
   pushed, push the new version branches and the deletions with it.
6. `link.sh` is a copy of the script from the meta-skills repository. It
   has a version of its own, `LINK_SH_VERSION` near the top of the
   script, which belongs to that source, and it gets no branches here.
   - Do not edit `link.sh` in this repository. To update it, replace the
     whole file with the newer version from the source URL in its header,
     and keep the header with the license notice.
   - A change that replaces `link.sh` takes a level for `VERSION` at
     least as high as the script's own change: major when a command that
     worked before now fails; minor for a new option or harness; snapshot
     for fixes and help text.
