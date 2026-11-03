# Note style: controlled English derived from ASD-STE100

## Contents

- Why this standard, and why only part of it
- The rules that apply, with rewrites
- The rules that are deliberately dropped
- Deviations added for notes
- Self-check before saving

## Why this standard, and why only part of it

ASD-STE100 is a controlled natural language from the aerospace industry. The current issue holds 53 writing rules and a dictionary of roughly 900 approved words, each restricted to one meaning and one part of speech, plus roughly 1,200 deprecated words with suggested replacements.

The vault uses the writing rules. The vault does not use the approved-word dictionary. Three reasons:

1. **The standard excludes this use.** The ASD FAQ states that STE is "not intended for general-purpose writing". STE governs procedural and descriptive maintenance text. A note is a record, which is a different genre.
2. **The dictionary would police the wrong words.** STE already exempts Technical Names and Technical Verbs from the dictionary. In a technical note, the hostnames, flags, paths, and package names are the payload, and they are all exempt. Dictionary compliance would constrain only the connective tissue while the payload passes unchecked.
3. **The cost lands on every write.** Checking each word against a 900-word list needs the list in context on every capture. The writing rules cost nothing, because they are a habit rather than a lookup.

The writing rules survive the transfer because their purpose transfers. They exist to remove ambiguity for a reader who lacks the writer's context. That reader is a future agent.

This reference is the STE regime for notes. A user-wide style rule, where one exists, governs documentation and technical chat replies, not notes. Where the two differ, this file wins inside a note, and the differences are listed under "The rules that are deliberately dropped" and "Deviations added for notes" below.

## The rules that apply, with rewrites

### 1. One idea per sentence

Instructions take 20 words maximum. Descriptions take 25 words maximum.

- Avoid: "After confirming the driver is loaded, restart the service and then check the logs, because the failure sometimes only appears on the second start."
- Use: "Confirm that the driver is loaded. Restart the service. Read the logs. The failure sometimes appears only on the second start."

### 2. Active voice, with the actor named

Passive voice is allowed only when the actor is genuinely unknown.

- Avoid: "The certificate is renewed automatically."
- Use: "Caddy renews the certificate automatically."

The second version tells a future reader which component to debug.

### 3. Repeat the noun

Never open a sentence with a bare "it", "this", or "that". A pronoun that was obvious during the conversation is ambiguous six months later.

- Avoid: "The proxy sits in front of the API. This fails when the token expires."
- Use: "The proxy sits in front of the API. The proxy fails when the token expires."

### 4. One term per concept

Choose one term and keep it. Synonym variety defeats `grep`, which is the primary retrieval path.

- Avoid: mixing "controller", "stick", "dongle", and "adapter" for one device.
- Use: "controller", every time. Record the aliases once in the note body if the user says them out loud.

### 5. No phrasal verbs where a single verb exists

Phrasal verb meanings are not predictable from their parts.

| Avoid | Use |
|---|---|
| set up | configure, install |
| kick off, fire up | start |
| take down, tear down | stop, remove |
| look into | investigate |
| turn on / off | enable / disable |
| back up (verb) | make a backup of |

Fixed technical noun forms stay as they are: "a backup", "a setup file".

### 6. Noun clusters: three words maximum

- Avoid: "Z-Wave device inclusion failure state"
- Use: "the failure state during Z-Wave device inclusion"

### 7. One topic per paragraph, six sentences maximum

A paragraph that covers two topics gets retrieved for one and confuses the other.

### 8. Vertical lists for three or more items

- Avoid: "Check the port, the firewall rule, the DNS record, and the certificate expiry."
- Use: a bulleted list of four items.

### 9. Write full sentences

Keep articles and subjects. Telegraphic notes decay fastest, because the omitted words carried the relationships.

- Avoid: "Restart needed — driver reload first, else panic."
- Use: "Reload the driver before you restart the service. A restart without the reload causes a kernel panic."

### 10. No semicolons

Write two sentences.

### 11. Put the warning first

- Avoid: "Run the migration script, but note that it drops the table if the schema version is old."
- Use: "**Warning:** the migration script drops the table when the schema version is old. Check the schema version, then run the script."

This is a deliberate deviation from STE rules 7.2 and 7.3, which start a safety instruction with the command or condition and give the risk after it (the form STE itself prescribes). A note is a record that a reader finds by searching for the hazard, so the hazard leads.

### 12. Give one instruction per sentence

Numbered steps carry one action each. A step with two actions gets half-completed.

### 13. Use the same sentence shape for the same kind of statement

Parallel structure across notes makes the vault scannable and makes the index lines uniform.

## The rules that are deliberately dropped

| Dropped | Reason |
|---|---|
| The ~900-word approved dictionary | See above. Cost on every write, and it exempts the payload anyway. |
| One part of speech per word | Unenforceable without the dictionary in context. |
| The ban on perfect tenses | Notes record event order. See the deviations below. |
| The restriction on "-ing" forms | Many exact technical names contain them, such as "logging driver" and "polling interval". |
| The 6-sentence limit applied to code blocks and tables | Structural, not prose. |
| Command-then-risk order inside a warning (STE 7.2–7.3) | Notes lead with the hazard; see rule 11 above. |
| "approximately" over "about" for quantities | Dictionary rule; the vault does not use the dictionary. Either word is fine in a note. |

## Deviations added for notes

### Perfect tenses are allowed when event order matters

STE bans them because maintenance procedures are imperative and have no history. Notes are histories.

- Loses information: "The service restarted. The log started."
- Keeps information: "The service had already restarted before the log started."

Use the simple past everywhere else.

### Precise verbs of evidence are allowed

STE collapses "verify", "check", "confirm", and "ensure" into "make sure". The vault needs the distinctions, because the `confidence` field depends on them:

- **verified** — you ran the command, read the file, or saw the output yourself.
- **reported** — the user or a document stated it, and you did not confirm it.
- **assumed** — you inferred it. Name the inference in the body.

Never round an `assumed` fact up to `verified`.

### Technical names pass through verbatim

Never simplify or paraphrase a hostname, IP address, port, flag, path, package name, environment variable, or error string. Quote it exactly, in backticks. An approximated command is worse than no command, because it looks usable.

### Dates are absolute

A note outlives the conversation that produced it. Convert relative time to an absolute date at capture, while the anchor is still known.

- Avoid: "The controller moved to the NUC last week."
- Use: "The controller moved to the NUC on 2026-08-08."

## Self-check before saving

Read the note once against this list:

- [ ] Every sentence carries one idea, within the word limit.
- [ ] No sentence starts with a bare "it", "this", or "that".
- [ ] Each concept uses one term throughout.
- [ ] No phrasal verb where a single verb exists.
- [ ] Warnings come before the instructions they qualify.
- [ ] Every command, path, and error string is quoted exactly.
- [ ] Every date is absolute.
- [ ] `confidence` matches what you actually did.
- [ ] The first paragraph stands alone as a summary.
