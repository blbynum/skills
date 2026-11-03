# Sources — notes

Provenance ledger for the note-author skill: every subject-matter claim it
makes, with the source, the date it was last verified, and the models or
vintage a finding was measured on. SKILL.md does not link this file, so it
never loads with the skill. The authoring skill reads it at its research
step and refreshes the "Last verified" dates of the sources it re-checks.
Split out of the shared ledger on 2026-10-31; entries keep their original
wording and dates.

### note-author skill — community agent-memory practice, 2026
- URLs: https://vectorize.io/articles/best-ai-agent-memory-systems ,
  https://github.com/zilliztech/memsearch
- Last verified: 2026-08-15 (fetched search summary)
- Supports (corroboration only): atomic markdown notes with an index file
  and bidirectional links as current common practice for durable agent
  memory — corroborates the note-author skill's design, establishes nothing
  beyond it.

## doc-author, outline, notes — notes-versus-docs pass (2026-11-02)

Subject-matter sources for the pass that rewrote doc-author as the one
documents skill (platform docs plus the software-docs reference), created
the outline platform skill, added the shared note-or-doc table to notes, and
gave eight producing skills a `notes-skill` or `docs-skill` key. Read by the
lead unless marked "strand": a strand is a fresh-context subagent of the
same session that returned claim records with verbatim quotes and URLs, and
the lead did not open that page.

Moved from the shared ledger on 2026-11-03; entries keep their original wording and dates.

### Luhmann, "Communicating with Slip Boxes" (1981, Kuehn translation)
- URL: https://luhmann.surge.sh/communicating-with-slip-boxes
- Last verified: 2026-11-02 (fetched; the three quotes below confirmed exact)
- Supports: a note is upstream material and a publication is composed, not
  copied — "Theoretical publications do therefore not result from simply
  copying what can already be found in the slip box"; the slip box is "a
  kind of secondary memory ... an alter ego"; a note "receives its quality
  only from the network of links and back-links". Grounds note-or-doc.md
  rule 3 (a note becomes a doc by composition, not by moving).

### NARA, General Records Schedule 5.2 FAQs (transitory and intermediary records)
- URL: https://www.archives.gov/records-mgmt/grs/faqs-for-grs-5-2
- Last verified: 2026-11-02 (fetched; page updated June 2023, reviewed
  2024-06-14)
- Supports: use, not polish, makes a record — "If it is used for
  decision-making or taking action, it is a record"; "Transitory records are
  required for only a short time (generally less than 180 days)";
  "Intermediary records exist to create subsequent records." Grounds the
  note-or-doc table's "What is it for?" row and the "when in doubt" line.

### Forte Labs, "The CODE method" (basboverview)
- URL: https://fortelabs.com/blog/basboverview/
- Last verified: 2026-11-02 (fetched; published 2023-05-01, updated
  2023-11-23)
- Supports: Express as the output stage — "the true purpose of learning is
  to turn our knowledge into effective action"; the page names no single
  audience. Grounds "one piece of work can yield both" (note-or-doc.md rule
  2) together with Forte's intermediate-packets post (strand).

### Notion Engineering, "Building Shared Memory for AI Agents in Notion"
- URL: https://www.notion.com/blog/building-shared-memory-for-ai-agents-in-notion
- Last verified: 2026-11-02 (fetched; Hesham Salman, published 2026-08-18;
  all five quotes confirmed exact)
- Supports (one vendor's own vault; tier 3 measured on their system): the
  contamination of a shared store by agent scratch — "15%-20% were likely
  duplicates or near-duplicates", "3-5% were session notes", "The first bad
  version of a memory system is a junk drawer with an API", "By default,
  facts expire", "Memory is something that must be periodically
  maintained". Grounds note-or-doc.md rule 1 (scratch is neither) and the
  outline skill's archive-as-end-state rule.

### Strand-read sources (claim records only; pages not opened by the lead)
- Ahrens, How to Take Smart Notes — quotes via Goodreads excerpts only
  (takesmartnotes.com now redirects to a course page); "Write exactly one
  note for each idea and write as if you were writing for someone else";
  project notes "reside outside the Zettelkasten". Tier 3 as read.
- Matuschak, Evergreen notes and About these notes —
  https://notes.andymatuschak.org/Evergreen_notes ; "Write notes for
  yourself by default, disregarding audience"; "These notes are mostly
  written for myself". Disagrees with Ahrens on audience; the note-author skill
  already follows Ahrens.
- Appleton, A Brief History & Ethos of the Digital Garden —
  https://maggieappleton.com/garden-history ; seedling / budding /
  evergreen; "there is no 'final version' on a garden".
- The National Archives (UK), Essential Records Management (PDF, 2009) —
  https://cdn.nationalarchives.gov.uk/documents/essential-records-management.pdf ;
  ISO 15489 definition of a record; capture into the filing structure is
  the dividing act; a personal mailbox "treated as an individually owned
  asset".
- Claude Code memory doc — https://code.claude.com/docs/en/memory ; auto
  memory is machine-local; CLAUDE.md is for shared project standards;
  "move it to a skill" for multi-step procedures.
- Anthropic memory tool — https://platform.claude.com/docs/en/agents-and-tools/tool-use/memory-tool ;
  one tool routed by a `command` field; the injected prompt tells Claude to
  "record status / progress / thoughts" and to delete stale files.
- CoALA (arXiv 2309.02427, v3 2024-03-15); "Memory in the Age of AI
  Agents" (arXiv 2512.13564, 2025-12-15); MemGPT (arXiv 2310.08560) —
  working / episodic / semantic / procedural tiers; MemGPT exposes one
  function per tier. No category for material meant for other people.
