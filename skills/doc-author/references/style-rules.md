# Developer-documentation style rules

The conventions that the Google, Microsoft, GitLab, Red Hat, and Kubernetes
documentation style guides agree on, plus the few points where they split.
Where the project you are writing in already has a convention, the project's
convention wins; these are the defaults for a project that has none.

## Contents

- Voice and wording
- Headings
- Procedures and steps
- Code samples
- Command-line syntax and placeholders
- Code in running text
- API reference descriptions
- Links
- Notices (note, caution, warning)
- Lists and Markdown hygiene
- Contested points (choose and stay consistent)

## Voice and wording

- Address the reader as "you"; do not write "we" for the reader or the
  product.
- Active voice; the doer is the subject. Passive only when the actor is
  unknown or irrelevant.
- Present tense for how the software behaves. No "will" for product
  behavior; no "would".
- Conversational and direct, not frivolous. Lead with what matters; cut
  "you can", "there is", "in order to", "please".
- Write for a global audience: no idioms, no "simply", "easily", "just",
  "quickly", "obviously"; prefer "for example" to "e.g."; avoid -ing forms
  where a reader could misparse them.
- Timeless: no "currently", "now", "new", "soon", "recently"; anchor to a
  version or date. Do not document unreleased or future features.
- No directional language ("above", "below", "on the right"); refer to
  sections by name.
- Bias-free: "they" for a generic person; neutral terms ("allow list",
  "block list", "primary/replica").
- Use one term per concept; the product's own names, spelled as the
  product spells them.

## Headings

- Sentence case for every heading and title.
- One level-1 heading per page; do not skip levels; no empty headings (a
  heading followed directly by another means a missing paragraph or a
  redundant heading); no links or code-only text as a heading.
- Task headings start with an imperative verb ("Install the agent");
  concept and reference headings are noun phrases ("Retry policy", "Exit
  codes"). Avoid -ing headings.
- Headings predict their content: no "Overview", "Introduction", "Misc",
  "Notes", "Important" as a heading. "Known issues" is acceptable for a
  reference section of limitations.
- Keep headings short; front-load the keyword; mark a section that not
  every reader needs with the prefix "Optional:".

## Procedures and steps

- Introduce the procedure with a sentence that ends in a colon when the
  steps follow immediately ("To rotate the key:"); the sentence adds
  information, not a repeat of the heading.
- Prerequisites come first, as a plural bulleted "Prerequisites" section,
  never in a note and never discovered at step four.
- Numbered steps; one action per step; each step starts with an imperative
  verb; parallel structure across steps.
- Say where before what ("In `settings.yaml`, set `timeout`"), the goal
  before the action when the step has a goal ("To retry failed uploads,
  add `--retries 3`"), and the action before its result.
- Number only the reader's actions; what the system does in response goes
  in prose under the step.
- A single-step procedure is one bullet, never a one-item numbered list.
- Document the primary way to do a task; a second way gets its own section
  or page. Do not repeat a procedure; link to it.
- Mark an optional step with "Optional:" at its start. Sub-steps are
  lettered.
- End with a verification: what the reader sees when it worked.
- Keep a procedure to one screen where you can; split longer ones.

## Code samples

- Precede every sample with a sentence that says what it does or shows;
  end with a colon when the sample follows immediately. Avoid "run the
  following command" as the whole introduction; say what the command does.
- Fenced code blocks with a language tag on every fence (`bash`, `python`,
  `toml`, `text` for output); blank lines around the fence.
- Complete, copy-paste runnable, and tested. Click-to-copy commands need
  no edits after copying; put placeholders only where the reader must
  supply a value.
- Show expected output separately from the command, introduced with a
  fixed phrase: "The output is similar to the following:" (or "The output
  is:" when it is exact). Show output only when it adds information.
- Indicate omitted code with a comment in the sample's own language
  (`# ...` in Python, `// ...` in Go); never bare three dots or the
  ellipsis character in code. In shown output, a line of three dots may
  stand for omitted lines.
- Wrap at 80 characters; follow the language's own indentation rules; no
  trailing whitespace.
- Comments inside a sample explain why or point out what to notice, not
  what each line does. Secure by example: validate input, no hard-coded
  secrets, no `chmod 777`.
- A sample that mentions a version matches the text around it; no comments
  about alternative versions inside the sample.

## Command-line syntax and placeholders

- Synopsis notation: `[arg]` optional, each optional item in its own
  brackets; `{a|b}` a required choice separated by `|`; `arg...` repeatable.
- Placeholders: use the project's style; default to `<angle-brackets>`
  with a descriptive name (`<log-file>`), and follow the command with a
  list that says what each placeholder stands for. Never leave a
  placeholder unexplained.
- Shell prompt: omit the `$` on single-line commands unless the project
  shows it; if a block mixes commands and output, show the prompt on every
  command line. Never show the current directory in a prompt.
- Long commands: break with the shell's continuation character at the end
  of each line except the last, and indent continuation lines by four
  spaces.
- Options and flags in code font, capitalized as typed; name both forms the
  first time (`-o`, `--output`).

## Code in running text

- Code font for anything the reader types or the code defines: commands,
  flags, file names and paths, directories, environment variables, keys,
  values, functions, methods (no empty parentheses after a method name),
  classes, types, fields, HTTP methods and status codes, package names,
  IP addresses and ports, text input.
- Bold for UI labels only ("select **Save**"); not for emphasis, not for
  keywords, not for file names.
- Not code font: product, service, and organization names; domain names;
  URLs the reader follows in a browser.
- Do not inflect a code element: "the `Session` objects", not
  "`Session`s"; add a noun and inflect the noun. No quotation marks
  around code.
- Italics only for the first mention of a term that is defined there, and
  sparingly.

## API reference descriptions

- First sentence states the purpose without repeating the element's name:
  "Opens a connection to the cache." not "open_cache opens…". Only the
  first sentence shows in indexes, so it must stand alone.
- Methods start with a third-person verb: "Returns…", "Adds…", "Creates…";
  getters "Gets the…"; boolean checks "Checks whether…" or "Returns true
  if…".
- Parameters: "The…" or "A…", with the type, whether required, the allowed
  values, and the default; booleans as "True if …; false otherwise." Do not
  repeat the parameter name or type as its whole description.
- Return value: what it is, its type, and the condition a boolean reports.
- Errors and exceptions: each one that the interface promises, with when
  it is raised.
- Deprecated elements name the replacement and, when known, the version:
  "Deprecated. Use `connect` instead."
- A fixed section order for every entry: description, syntax or signature,
  parameters, return value, errors, remarks, example, see also. Consistency
  is what makes a reference scannable.

## Links

- Descriptive link text that stands on its own and usually matches the
  target's title; never "click here", "this page", "here", or a bare URL
  as the text.
- Introduce cross-references consistently: "For more information, see
  Configuration." Use "see" for a link; do not quote link text.
- Short link text with the important words first; the same text does not
  link to two targets on one page; do not link the same target twice in a
  section.
- Inside a repository, relative links to files and anchors; they work in
  clones and forks and can be checked.
- No forced new tabs, no external-link icons, no links in headings.

## Notices (note, caution, warning)

- Three levels, in rising force: a note is useful but not critical; a
  caution says proceed carefully; a warning says do not do this, or this
  cannot be undone.
- Use them rarely, one at a time, never two in a row. Write the
  information as plain text first and promote it only if it is relevant
  but outside the reader's current path.
- Never put in a note what the reader needs to succeed: prerequisites,
  earlier steps, a required step, a cross-reference the task depends on.
  Those go in the flow, before the step that needs them.
- Use the project's admonition syntax (`> [!NOTE]`, `!!! note`,
  `{{< note >}}`, or bold run-in "Note:") and only that one.

## Lists and Markdown hygiene

- Numbered lists only for sequence; bullets for everything else;
  description lists or tables for name-and-value pairs.
- Parallel items, same grammatical form, same punctuation: a period after
  every complete sentence, none after fragments, consistent within the
  list; capital first letter; a colon after the introducing phrase.
- Say whether the items in a bulleted list are all required or
  alternatives when that is not obvious.
- Tables for facts that share attributes (flags, keys, error codes); one
  row per element.
- Blank lines around fences, lists, and headings; no trailing spaces;
  language tag on every fence; no raw HTML where Markdown does the job.
- Match the repository's linters when present (`.markdownlint*`,
  `.vale.ini`) and leave them passing.

## Contested points (choose and stay consistent)

The guides split on these; pick the project's existing convention, or the
first option listed, and apply it everywhere in the document set:

| Point | Options |
|---|---|
| Task heading verb | bare imperative "Create an issue" (Google, GitLab) / "To create an issue" (Microsoft) / gerund "Creating an issue" (Red Hat) |
| Placeholder form | `<angle-brackets>` (Kubernetes, Microsoft, GitLab) / `UPPER_SNAKE` (Google) |
| `$` prompt | omit (Kubernetes) / show consistently (Google) |
| User-typed input | code font (Google) / bold (Microsoft) |
| Empty parentheses after method names | omit (Google) / show (Microsoft examples) |
| Code in headings | avoid (Google) / allowed in backticks (GitLab) |
| Period on one-sentence bullets | yes (GitLab) / no (Microsoft Learn) |
| Future tense in tutorials | occasional "you will" (GitLab) / present only (Google, Kubernetes) |
