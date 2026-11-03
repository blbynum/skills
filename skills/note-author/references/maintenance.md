# Vault maintenance

## Contents

- INDEX.md format
- TAGS.md format
- Merging duplicates
- Correcting a stale note
- Pruning
- Link hygiene
- Full audit checklist

## INDEX.md format

`INDEX.md` is the entry point for retrieval. A reader reads the index, picks two to five notes, then reads those notes in full. The index must therefore hold enough signal to choose well, and stay short enough to read whole.

One line per note, sorted alphabetically by title:

```markdown
# Note index

- [Home Assistant upgrade order](home-assistant-upgrades.md) — Upgrade Z-Wave JS UI before HA Core, because HA Core rejects an older schema. `homelab` `home-assistant`
- [Z-Wave JS UI runs on an external server](zwave-js-ui-external.md) — HA connects to a standalone instance on the host `zwave-host`, not a local add-on. `homelab` `home-assistant`
```

Rules for index lines:

1. The summary is one sentence, taken from the note's first paragraph and shortened.
2. The summary states the fact. It does not describe the note. Write "Upgrade Z-Wave JS UI before HA Core", not "Notes about upgrade order".
3. Tags come last, in backticks.
4. Alphabetical order by title keeps diffs small and puts near-duplicates next to each other, where you will notice them.

Rebuild the index only when it has drifted. Normal captures edit one line.

## TAGS.md format

```markdown
# Tags

- `homelab` — Self-hosted infrastructure on the home network.
- `home-assistant` — Home Assistant and its integrations.
```

Be reluctant to coin a tag. A tag earns its place when three or more notes need it. Before you add one, read `TAGS.md` and try to reuse an existing tag. Tag proliferation makes tags useless faster than a missing tag hurts.

Two to four tags per note. A note that needs six tags is probably two notes.

## Merging duplicates

When two notes cover the same subject:

```
- [ ] 1. Read both notes in full
- [ ] 2. Choose the survivor: better slug, more inbound links, higher confidence
- [ ] 3. Move the facts that only the other note holds into the survivor
- [ ] 4. Resolve contradictions — do not keep both claims
- [ ] 5. Set the survivor's updated date to today
- [ ] 6. Repoint every [[wikilink]] that named the deleted note
- [ ] 7. Delete the other file and its index line
```

Step 4 is the one that matters. Two contradictory statements in one note is worse than either note alone. When you cannot resolve the contradiction, keep the claim you can support, lower `confidence` to `reported`, and state the open question explicitly in the body.

Confirm with the user before you delete a file.

## Correcting a stale note

Edit in place. Do not append a correction below the wrong text, because a future reader may grep the wrong line and stop there.

1. Replace the incorrect text with the correct text.
2. Set `updated` to today.
3. Set `confidence` to match how you learned the new fact.
4. When the old value carries diagnostic value, record it in one line under a `## History` heading, with its date.

## Pruning

Delete a note when it meets any of these tests, after you confirm with the user:

- The fact is now false and has no historical value.
- The fact duplicates a source of truth that the reader will always consult instead, such as a config file in a repository.
- The note was never true. It recorded an assumption that proved wrong.

Do not delete a note only because it is old. Age is not decay.

## Link hygiene

- Links use `[[slug]]`, matching the filename without the `.md` extension.
- Every link is bidirectional. When note A links to note B, note B links back to note A.
- A link to a note that does not exist is allowed. It marks a note worth writing.
- Check for broken links during an audit. Run the check from the notes root, the project's `notes/` or the configured vault directory (`vault-dir`):

```bash
cd "<notes-root>" && grep -oh '\[\[[^]]*\]\]' *.md | tr -d '[]' | sort -u | while read -r s; do [ -f "$s.md" ] || echo "missing: $s"; done
```

## Full audit checklist

Run this when the user asks for a cleanup.

```
- [ ] 1. List every .md file, and compare against INDEX.md — find both directions of drift
- [ ] 2. Find near-duplicate titles in the index, and merge them
- [ ] 3. Check every tag in use against TAGS.md, and remove tags used only once
- [ ] 4. Find broken [[wikilinks]] with the command above
- [ ] 5. Find one-directional links, and complete them
- [ ] 6. Read notes with confidence: assumed — verify what you can, and promote or delete
- [ ] 7. Read the oldest notes, and flag facts that look stale to the user
- [ ] 8. Report what changed, and ask before you delete anything
```

Step 8 stands. Deletion needs the user's confirmation every time.
