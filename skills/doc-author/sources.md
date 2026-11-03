# Sources — doc-author

Provenance ledger for the doc-author skill: every subject-matter claim it
makes, with the source, the date it was last verified, and the models or
vintage a finding was measured on. SKILL.md does not link this file, so it
never loads with the skill. The authoring skill reads it at its research
step and refreshes the "Last verified" dates of the sources it re-checks.
Split out of the shared ledger on 2026-10-31; entries keep their original
wording and dates.

## doc-author skill subject-matter sources

Provenance for the doc-author skill (created 2026-10-28). Research pass of
2026-10-28: five parallel subagent strands (frameworks; style guides;
repository artifacts; empirical evidence; current practice and AI readers),
claim records with verbatim quotes distilled here; the record files and the
downloaded paper PDFs lived in the session scratchpad and are ephemeral.
"Fetched" = page retrieved and read that day (WebFetch extraction or raw
curl); "summary-only" = claim rests on a search summary or a secondary
because the primary was paywalled, 403, or 404. Lead spot-checks on
2026-10-28: diataxis.fr/tutorials (temptations list and headings),
developers.google.com/style/code-samples (omitted-code and ellipsis rules),
and the extracted text of Uddin & Robillard 2015, Sohan et al. 2017, and
Aghajani et al. 2019 for the three quoted figures — all matched the records.
Evidence-calibration rule this section enforces: the skill states no
percentages, multipliers, or p-values; every qualitative claim and every
contract line traces here, with the population and year where a study is
behind it.

### Frameworks: Diátaxis, the Good Docs Project, Write the Docs, SWE at Google
- Diátaxis (Daniele Procida), https://diataxis.fr — start-here, tutorials,
  how-to-guides, reference, explanation, compass, map, tutorials-how-to,
  reference-explanation, how-to-use-diataxis, quality, colophon, news; all
  fetched 2026-10-28; pages undated; news page's newest entries 4 and 6 Aug
  2026 (Polish translation, atom feed); repo commits through 2026-08-06 are
  typos, translations, infrastructure — no change to the four-kind model
  found. "Complex hierarchies" page 404s live; read from a Wayback snapshot
  of 2024-12-27 (landing pages "should read like an overview"; "Seven items
  seems to be a comfortable general limit"; "not a scheme ... four boxes").
  Grounds: the compass table (informs action/cognition × acquisition/
  application), per-kind purpose/question/form, "Crossing or blurring the
  boundaries ... is at the heart of a vast number of problems in
  documentation", the tutorial contract (teacher's responsibility; "A
  tutorial must be safe"; single path, no choices; the four anti-pedagogical
  temptations "abstraction, generalisation; explanation; choices;
  information"; "A tutorial is not the place for explanation"; visible
  results early and often), the how-to contract ("already-competent user";
  "practical usability is more helpful than completeness"; "no digression,
  explanation, teaching"; written "from the perspective of the user, not of
  the machinery"; title "How to integrate application performance
  monitoring."), the reference contract ("Neutral description is the key
  imperative"; "austere. One hardly reads reference material; one consults
  it"; structure "should mirror the structure of the product"; must not
  "explain, instruct, discuss, opine"; "Provide examples"), the explanation
  contract ("discursive treatment ... that permits reflection"; "can and must
  consider alternatives"; implicit "about" title test; "tends to absorb other
  things"), and the bounds ("It certainly does not mean that you should
  create empty structures"; "a guide, not a plan"; "every step in the right
  direction is worth publishing immediately"). Diátaxis addresses "deep
  quality", not "functional quality" (accuracy, completeness) — the reason
  the skill pairs it with the source-of-truth and verification steps.
  Licence not stated on the colophon (CC-BY-SA 4.0 per a search summary,
  unverified). Grade: practitioner, single author, adopted by "several
  hundred projects" (colophon); no outcome measurement exists.
- The Good Docs Project, https://www.thegooddocsproject.dev/template and
  the readme, tutorial, how-to, reference, concept, changelog, release-notes
  template pages — fetched 2026-10-28; undated, ©2026; latest release 1.4
  "Golden Gate" 2025-06-13 (blog post fetched); section names verbatim,
  per-section guidance partly extractor paraphrase. Grounds: README section
  set (description, who it is for, dependencies, install/configure/run/
  troubleshoot, contributing, additional docs, help, terms) and "reorder and
  remove sections ... that do not apply"; tutorial sections (Overview,
  Background, Before you begin, Steps, Summary, Next Steps) with the
  15–60-minute and ≤7-primary-steps limits (paraphrase); how-to "Do not use
  a how-to to teach concepts", "Address one logical goal (task) per how-to
  page"; reference "Avoid high-level usage instructions", "limit procedural
  or instructional content"; changelog vs release notes (audience, purpose,
  scope, language; SemVer + YYYY-MM-DD; link every entry; bug fixes say
  what and why, not how). Grade: community templates.
- Write the Docs guide — docs-as-code, beginners-guide-to-docs,
  docs-principles, tools/testing — fetched 2026-10-28; undated. Grounds:
  docs-as-code definition ("writing documentation with the same tools as
  code": issue trackers, Git, plain-text markup, code reviews, automated
  tests; "You can block merging of new features if they don't include
  documentation"); first-docs checklist (what problem it solves, a small
  code example, link to code and tracker, how to get support, how to
  contribute, install in "a couple of lines", one standard license); FAQs
  rot (paraphrase); principles — "Consider incorrect documentation to be
  worse than missing documentation" (Current), ARID "Accept (some)
  Repetition In Documentation", Complete "cover concepts in full, or not at
  all", Nearby, Unique; testing ladder ("The most useful tests are run on
  each commit"; build exits 0 / strict modes; link checking "a really great
  place to start"; Vale with Proselint/Write-good). Grade: community
  guide, no outcome data.
- Software Engineering at Google, ch. 10 "Documentation" (Tom Manshreck,
  O'Reilly 2020), https://abseil.io/resources/swe-book/html/ch10.html — raw
  HTML read 2026-10-28; CC BY-NC-ND 4.0. Grounds: docs "treated as code"
  (source control, owners, "Undergo reviews for changes (and change with
  the code it documents)", issues tracked, periodically evaluated);
  audience framing and "keep your documents short" (the brevity quote is
  Pascal's; no Shakespeare line exists in the chapter); seekers vs
  stumblers; five types and "it is important to know the different types,
  and to not mix types. A document should have, in general, a singular
  purpose"; reference comments mandatory for files, public classes, and
  public functions, "beginning with an indicative verb"; design docs cover
  goals, implementation strategy, decisions with trade-offs, alternatives;
  tutorials "assume nothing", prerequisites stated first, "number each
  action that a user needs to undertake. Don't number actions that the
  system may take", combine atomic user operations; conceptual docs may
  sacrifice "some accuracy ... for clarity"; landing pages are "a traffic
  cop"; three reviews (technical for accuracy, audience for clarity,
  writing for consistency); WHO/WHAT/WHEN/WHERE/WHY "in the first two
  paragraphs"; "Documents without owners become stale"; freshness dates
  with reminders "when the document hasn't been touched in, for example,
  three months"; stale docs removed or marked obsolete; "one mistake
  engineers often make is adding design decisions or implementation
  details to an API document". Grade: single-company practice, widely
  cited; no measurement.

### Style guides: Google, Microsoft, GitLab, Red Hat, Kubernetes
- Google developer documentation style guide,
  https://developers.google.com/style/ — highlights (2026-10-09),
  code-samples (2025-10-10), procedures (2026-10-27), headings (2026-06-08),
  link-text (2026-10-09), notices (2026-10-09), code-syntax (2026-10-09),
  code-in-text (2026-10-09), api-reference-comments (2026-07-01), tense
  (2024-10-15), voice (2024-10-15), timeless-documentation (2024-10-15),
  future (2026-05-19), whats-new (2026-10-16); all fetched 2026-10-28 as
  quote extractions (full page not seen for most). Grounds the consensus
  rules below plus: "Put conditions before instructions"; "Tell the reader
  where to complete an action ... before you state the action"; "state the
  goal before the action"; "Use a colon if it immediately precedes the
  procedure"; "In general, use one step for each action"; "give only the
  best way"; "Avoid repeating procedures"; "Don't use notes to tell the
  reader about prerequisites"; "Don't make a full procedural step into a
  note"; "Minimize notice usage"; "Indicate omitted code by using a comment
  in the syntax of the language ... Don't use three dots or the ellipsis
  character"; "Wrap lines at 80 characters"; "The output is similar to the
  following:"; CLI notation ("square brackets ... optional", "curly braces
  ... choose one—and only one", pipe, "three dots and no spaces"); "Provide
  a click-to-copy command example that the reader doesn't need to edit";
  "Follow the command line with a descriptive list of the placeholders";
  code-font inventory (incl. IP addresses, port numbers, package names,
  text input — added Apr 2026); "Don't inflect the name of a code
  element"; "In the first sentence of a class description, briefly state
  the intended purpose ... Don't repeat the class name"; getters "Gets the
  ..." / "Checks whether ..."; "True if ...; false otherwise."; "When
  something is deprecated, tell the user what to use as a replacement";
  "Write link text that makes sense without the surrounding text"; "don't
  use a URL as link text"; "Don't force links to open in a new tab"; "Use
  _see_"; "Don't use directional language"; "Don't pre-announce anything";
  timeless words "now, new, and currently"; "Avoid documenting future
  features or products"; What's new 2025–2026: subjective words "simply,
  quickly, properly, and carefully" (Oct 2026), limit gerunds (Oct 2026),
  "do the following" lead-in and "Optional:" headings (Apr 2026), removed
  empty parentheses after method names (May 2025). Internal inconsistency
  recorded: code-samples says indent Markdown code four spaces; code-syntax
  says use a fence. Grade: vendor style guide, dated pages.
- Microsoft Writing Style Guide, https://learn.microsoft.com/en-us/style-guide/
  — top-10-tips (ms.date 2026-07-02), writing-step-by-step-instructions
  (2026-03-18), formatting-text-in-instructions (2026-03-10),
  formatting-developer-text-elements (2026-04-23), code-examples
  (2019-08-07), reference-documentation (2019-08-07), headings (2018-07-24),
  bias-free-communication (2024-04-18), whats-new (2026-07-02); full text
  read 2026-10-28. Grounds: "Default to sentence-style capitalization";
  "Lead with what's most important. Front-load keywords"; "Make sure that
  customers know where the action should take place before you describe
  the action"; "Use a separate step for each instruction"; single step as
  "a bullet instead of a number"; "Try to fit all the steps on the same
  screen" (no "seven steps" rule on the current page); "Show expected
  output, either in a separate section after the code example or by using
  code comments"; "Always compile and test your code"; "Write secure code";
  reference article order (title/description, declaration, parameters,
  return value, remarks, example, requirements, see also) and "explain what
  the element does or represents without repeating the element name";
  "they" in generic references; "block list"/"allow list" (Jan 2026);
  quotation marks for AI prompts in text (Apr 2026). Microsoft's own
  notes-and-tips page 404s; alert definitions (Note/Tip/Important/
  Caution/Warning) come from the Microsoft Learn Markdown contributor guide
  (ms.date 2025-04-29), a platform guide. Grade: vendor style guide.
- GitLab documentation topic types and style guide,
  https://docs.gitlab.com/development/documentation/topic_types/ (+ concept,
  task, reference, troubleshooting, tutorial) and /styleguide/ — fetched
  2026-10-28, undated. Grounds: CTRT (concept, task, reference,
  troubleshooting; "the page usually starts with a concept and then
  includes a task or reference topic"); concept "Don't tell them how to do
  this thing. Tell them what it is", titles are nouns, avoid "Overview",
  "Introduction", "How it works"; task title "`active verb` + `noun`",
  "To create an issue:", "`Prerequisites` must always be plural",
  "document the primary way only"; reference "in an easily-scannable
  format, like a table or list", "Known issues" acceptable; troubleshooting
  last on a page, "workaround" vs "resolution"; tutorial "Tutorial: + active
  verb", "Use future tense from time to time"; style: "Use bold for UI
  element labels only", fenced code with "a syntax name at the top",
  "Use notes sparingly", list punctuation rules, "Do not skip a level".
  Grade: vendor (open-source project) style guide.
- Red Hat modular documentation reference guide,
  https://redhat-documentation.github.io/modular-docs/ (2026-03-13) —
  quote extraction 2026-10-28. Grounds: concept/procedure/reference modules
  and assemblies; procedure subheadings fixed (Prerequisites, Procedure,
  Verification, Troubleshooting, Next steps, Additional resources — "Do not
  change or embellish these subheadings"); "Each step describes one action
  written in the imperative form"; "For single-step procedures, use an
  unnumbered bullet"; prerequisites "a bulleted list ... plural heading";
  procedure titles are gerund phrases (the contested point); "A module
  should not contain another module". Grade: vendor style guide.
- Kubernetes documentation style guide (raw
  content/en/docs/contribute/style/style-guide.md, main) — read 2026-10-28,
  undated. Grounds: "Address the reader as 'you'"; "Use present tense";
  "Use active voice"; "Avoid words such as 'just', 'simply', 'easy'";
  "Avoid words like 'currently' and 'new'"; "Avoid making promises"; "Use
  angle brackets for placeholders. Tell the reader what a placeholder
  represents"; "Don't include the command prompt"; "Separate commands from
  output" ("The output is similar to this:"); sentence-case body headings
  with title-case front-matter titles; examples with version info
  "consistent with the accompanying text", "do not include comments about
  alternative versions". Grade: community (CNCF) style guide.
- Consensus (three or more guides): second person; active voice; sentence
  case; numbered lists for sequence only; code font for code, bold for UI
  only; intro sentence + colon before procedures and samples; one action
  per step, imperative, location before action; no skipped heading levels,
  one H1, no empty headings; descriptive link text; notices sparingly and
  never for required information; note < caution < warning; fenced blocks
  with language tags and a fixed command/output separator; concept = noun
  title without steps, task = verb title with steps, reference = table;
  explain every placeholder; document only the primary way; prerequisites
  plural, bulleted, before steps; present tense. Contested (recorded in the
  skill's style-rules table): task-heading verb form (bare imperative vs
  "To ..." vs gerund), placeholder form (`<angle>` vs `UPPER_SNAKE`), `$`
  prompt, user-typed input font, empty parentheses after methods, code in
  headings, period on one-sentence bullets, future tense in tutorials.
  Not fetched: Apple Style Guide (title-case claim is secondary and dated),
  Splunk and DigitalOcean rule pages (summary-only), Google's current
  contractions rule.

### Repository artifacts: README, changelog, community files, ADR, doc comments, API reference
- GitHub Docs "About READMEs"
  (docs.github.com/.../customizing-your-repository/about-readmes), "Setting
  guidelines for repository contributors", "Adding a security policy",
  "Adding a code of conduct", "About community profiles" — WebFetch
  extracts 2026-10-28, undated. Grounds: the five README contents ("What
  the project does / Why the project is useful / How users can get started
  / Where users can get help / Who maintains and contributes"); README
  precedence `.github`, root, `docs`; auto-generated TOC; "Relative links
  are easier for users who clone your repository"; CONTRIBUTING in root,
  `docs`, or `.github`, linked on issue/PR creation, with "Steps for
  creating good issues or pull requests", links, "Community and behavioral
  expectations"; SECURITY.md = supported versions and how to report;
  community-profile checklist (per-row table text not returned by the
  extractor). Grade: vendor doc.
- Standard Readme spec (raw github.com/RichardLitt/standard-readme
  spec.md, undated) — fetched. Grounds: "Sections must appear in order
  given below. Optional sections may be omitted"; short description "Must
  be less than 120 characters"; Install and Usage as code blocks; title
  "must match repository, folder and package manager names"; License "Must
  be last section"; TOC optional under 100 lines. Make a README
  (makeareadme.com, undated) — fetched: section order (Name, Description,
  Badges, Visuals, Installation, Usage, Support, Roadmap, Contributing,
  Authors, License, Project status); "Use examples liberally, and show the
  expected output if you can"; abandoned project "put a note at the top".
  The Art of README (hackergrrl) is 404 everywhere tried; "cognitive
  funneling" (broad to specific) is summary-only. Grade: community
  conventions.
- Keep a Changelog, https://keepachangelog.com/en/1.1.0/ — fetched
  2026-10-28; URL, header, and root link still say 1.1.0 (the site's own
  embedded changelog lists 1.1.1 2023-03-05 and 1.1.2 2024-09-27 as text
  patches; whether they are spec versions is unresolved). Grounds:
  "curated, chronologically ordered list of notable changes for each
  version"; seven principles ("for humans, not machines"; an entry for
  every version; same types grouped; linkable; latest first; release date
  displayed; say whether SemVer); the six types `Added`, `Changed`,
  `Deprecated`, `Removed`, `Fixed`, `Security`; "Using commit log diffs as
  changelogs is a bad idea"; "If you do nothing else, list deprecations,
  removals, and any breaking changes"; ISO 8601 dates; "A changelog which
  only mentions some of the changes can be as dangerous as not having a
  changelog"; `Unreleased` at the top; `[YANKED]`; file `CHANGELOG.md`; the
  canonical header text. Conventional Commits 1.0.0
  (conventionalcommits.org/en/v1.0.0/, fetched): `<type>[scope]:
  <description>`, fix→PATCH, feat→MINOR, `BREAKING CHANGE`/`!`→MAJOR,
  "Automatically generating CHANGELOGs" as a goal. SemVer 2.0.0 (fetched):
  "MUST declare a public API"; deprecation bumps MINOR and "update your
  documentation". Grade: community de-facto standards.
- ADRs: Nygard, "Documenting Architecture Decisions" (cognitect.com,
  2011-11-15, fetched) — "architecturally significant" = "affect the
  structure, non-functional characteristics, dependencies, interfaces, or
  construction techniques"; `doc/arch/adr-NNN.md`, "numbered sequentially
  and monotonically. Numbers will not be reused"; Title "short noun
  phrases"; Context "value-neutral"; Status proposed/accepted/deprecated/
  superseded "with a reference to its replacement"; Decision "full
  sentences, with active voice"; "All consequences should be listed here,
  not just the 'positive' ones"; "one or two pages long"; "we will keep the
  old one around, but mark it as superseded"; "Nobody ever reads large
  documents". MADR 4.0.0 (2024-09-17; raw CHANGELOG.md, README.md, and
  template/adr-template.md fetched): front matter status/date/
  decision-makers/consulted/informed; Context and Problem Statement;
  Decision Drivers; Considered Options; Decision Outcome "Chosen option:
  ..., because ..."; Consequences Good/Bad; Confirmation; Pros and Cons;
  More Information; `docs/decisions/nnnn-title.md`. adr.github.io
  definitions (fetched, ©2026). AWS Prescriptive Guidance ADR process
  (fetched, undated, vendor): "At a minimum ... context ... decision ...
  consequences"; "When the team accepts an ADR, it becomes immutable"; new
  ADR supersedes. Azure Well-Architected ADR page (ms.date 2026-04-10,
  vendor): "append-only log. Don't go back and edit accepted records";
  "Only include choices that affect the system's structure, key quality
  attributes, or are difficult to reverse"; "Record the confidence level";
  "Keep records pithy, assertive, on-topic, and factual"; "Avoid making
  decision records design guides". GitHub blog "Why Write ADRs"
  (2020-08-13, vendor): reasons only. Grade: practitioner origin plus
  vendor guidance; consistent across all four.
- Doc comments: PEP 257 (peps.python.org, last modified 2024-04-17,
  fetched): docstrings for modules, exported functions and classes, public
  methods; one-liner "prescribes the function or method's effect as a
  command", "should NOT be a 'signature'"; multi-line = summary line, blank
  line, elaboration; function docstrings cover "arguments, return
  value(s), side effects, exceptions raised, and restrictions". Google
  Python Style Guide §3.8 (undated, fetched): summary line ≤80 chars with
  terminal punctuation; mandatory for "public API", "nontrivial size",
  "non-obvious logic"; descriptive or imperative style "consistent within a
  file"; Args/Returns (omit when only None)/Raises/Attributes; "never
  describe the code". Go doc comments (go.dev/doc/comment, undated,
  fetched): "Every exported (capitalized) name should have a doc comment";
  complete sentences "naming the declared symbol"; "Package " first
  sentence; "should not explain internal details such as the algorithm";
  `Deprecated:` paragraphs; Go example tests (go.dev/blog/examples,
  2015-05-07, fetched): "compiled (and optionally executed) as part of a
  package's test suite", "guarantees that the information will not go out
  of date". Rust: rustdoc "How to write documentation" (undated, fetched):
  "the public API of all code should have documentation"; summary / blank
  line / details / "at least one code example that users can copy/paste";
  "Everything before the first empty line will be reused" in search; `#
  Panics` "every time edge cases in your code can be reached"; rustdoc
  documentation tests (fetched): examples "executed ... as tests"; RFC 1574
  (raw, 2016-03-31, fetched): "third person singular present indicative
  form"; headings Examples, Panics, Errors, Safety, Aborts, Undefined
  Behavior; "Everything should have examples"; plural "Examples". Javadoc:
  JDK 21 Documentation Comment Specification (docs.oracle.com, fetched;
  the classic "How to Write Doc Comments" article is 403): first sentence
  is the summary; main description then block tags; `@deprecated` "should
  tell the user when the API was deprecated and what to use as a
  replacement". TSDoc (tsdoc.org, ©2026, fetched): summary vs `@remarks`;
  core tag set. JSDoc getting-started (fetched): `/**` immediately before
  the code. Google C++ style comments section (fetched): declaration
  comments describe use (null pointers, performance), definition comments
  the tricky parts, prefer "why", `TODO` format. Grade: standards and
  vendor conventions; no outcome data.
- HTTP API reference: learn.openapis.org specification/docs.html and
  best-practices.html (©2026, fetched): "Almost every object ... accepts a
  `description` field" (CommonMark); "`summary` is used for list view, and
  should be kept short"; explicit `example`/`examples` for tooling;
  "single source of truth"; OADs are "first-class source files"; "Seldom
  Need to Write OpenAPI Descriptions by Hand". Vendor, labelled: ReadMe
  blog (undated) per-endpoint list ("What it does, in plain language /
  Required and optional parameters, with types and acceptable values / A
  full example request and response / What errors it can return");
  Postman API-documentation page (©2026) components (authentication,
  endpoints/operations, request/response examples, terms of use); Stripe
  Markdoc post (2022-09-13) and Twilio docs post (2024-07-08) describe
  their platforms (tested samples, OpenAPI-generated reference, CI
  validation), not page contracts. Grade: standard-body guidance plus
  vendor practice; the per-endpoint list is corroborated by the Sohan 2017
  recommendations below.

### Empirical evidence: what developers need and where documentation fails
- Uddin & Robillard, "How API Documentation Fails", IEEE Software 32(4),
  2015, DOI 10.1109/MS.2014.80 — author PDF fetched and text-extracted
  2026-10-28. N: exploratory survey 69 of 698 IBM Canada; validation survey
  254 of 1,064 IBM Canada/UK (23.8%; 203 developers, 51 architects; mean
  13.17 years); 323 total. Verbatim: "The three severest problems were
  ambiguity, incompleteness, and incorrectness of content"; "the
  respondents prioritized addressing five content-related problems over
  any presentation problem"; six problems rated "Blocker" at least once:
  "incompleteness, ambiguity, obsoleteness, incorrectness, inconsistency,
  and unexplained examples" — the four presentation problems (bloat,
  fragmentation, excess structural information, tangled information)
  never; "The respondents infrequently observed incorrect content, but
  they judged instances as 'Severe' or 'Blocker'"; no significant
  novice/expert difference. Grounds the skill's opening claim and
  "unexplained examples" rule. Grade: peer-reviewed survey, one company.
- Robillard & DeLine, "A field study of API learning obstacles", Empirical
  Software Engineering 16:703–732, 2011 — author PDF fetched. N: >440
  Microsoft developers (80/1,000 Phase I survey; interviews; 334/1,936
  Phase III). Verbatim: "inadequate API documentation as the most severe
  obstacle facing developers learning a new API"; "Small examples that
  nevertheless demonstrate API usage patterns involving more than one
  method call will be more useful than single-call examples"; "code
  snippets exercising only one API method were of little value"; examples
  read "as recommendations ('this is how you should use the API')" so
  "Examples should be developed to demonstrate 'best practices'" and
  signal being up to date; developers "skipping over explanatory text".
  Robillard, "What Makes APIs Hard to Learn?", IEEE Software 2009 — PDF
  fetched; N=80 Microsoft: 78% learned by reading documentation, 55% by
  code examples; docs must "include good examples, be complete, support
  many complex usage scenarios, be conveniently organized, and include
  relevant design elements"; "more than one-quarter ... absence of API
  usage examples tailored to their needs". Grade: peer-reviewed, one
  company, 2009–2011.
- Meng, Steinhardt & Schubert, "How Developers Use API Documentation: An
  Observation Study", Communication Design Quarterly 7(2), 2019, DOI
  10.1145/3274995.3274999 — publisher-hosted PDF fetched. N=11
  professional developers (authors: "too small to warrant statistical
  analyses"), screencast + eye tracking, one REST API. Verbatim: "used API
  documentation about 49% of the time"; API reference most used; code
  example pages "head to head with the API reference and were active about
  21% of the total time"; "both opportunistic and systematic developers use
  code examples as starting point"; concepts page ignored by five of
  eleven; guidelines: structure "according to categories that reflect the
  functionality or content domain of the API rather than ... the type of
  information", integrate conceptual information into tasks, present
  critical concepts "redundantly, e.g. ... integrated into the source code
  by using code comments", examples "complete and ready to be used via
  copy and paste" (placeholders referencing other examples "hindered"
  reuse), missing search blocked re-finding. Meng et al. 2018 (JTWC 48(3))
  abstract-only: initial global understanding, then concepts-oriented or
  code-oriented strategies; "completeness and clarity are relevant to API
  documentation". Grade: peer-reviewed observation, tiny N; directions
  only.
- Sohan, Maurer, Anslow & Robillard, "A Study of the Effectiveness of
  Usage Examples in REST API Documentation", VL/HCC 2017 — author PDF
  fetched. N=26 professional engineers (16 without examples, 10 with
  three examples added), 539 API calls, WordPress REST API. Verbatim: "We
  observed a p-value of 0.0003 for the success rates using Fisher test,
  and p-values of 0.017 and 0.051 for the trial API calls and time spent";
  "without usage examples developers spend more time and execute more
  trial attempts yet have lower success rates"; 14 of 15 without examples
  failed the Content-Type header vs 2 of 10 with; four recommendations
  (data types per field, valid formats, required HTTP headers, how to
  obtain prerequisites). Grounds the HTTP API reference contract. Grade:
  peer-reviewed controlled study, small N.
- Aghajani et al., "Software Documentation Issues Unveiled", ICSE 2019,
  DOI 10.1109/ICSE.2019.00122 — author-hosted PDF fetched. N: 878
  artifacts mined (824 labelled) from issues, PRs, Stack Overflow, mailing
  lists; 162 issue types. Verbatim: content issues in 485 artifacts vs
  "how it is written" 255; "Completeness accounts for 55% of the issues
  related to the documentation content"; "Up-to-dateness problems account
  for 39% ... In 21% of these cases, the inconsistency appeared to be
  between a system's behavior and its description"; code examples are the
  type "most frequently impacted by correctness issues ... 50%", then
  installation guidelines 20%; findability half of usability issues; lack
  of clarity 55% of readability issues. Aghajani et al., "Software
  Documentation: The Practitioners' Perspective", ICSE 2020, DOI
  10.1145/3377811.3380405 — read from ch. 6 of Aghajani's USI dissertation
  (folia.unifr.ch), which reproduces the paper; the ICSE PDF was 403. N:
  146 practitioners (125 ABB, 21 forums); issue-relevance percentages from
  Survey-I, 78 respondents. Verbatim: clarity "most important ... (88% of
  them)"; missing docs for a new feature 69%, missing install/deploy/
  release docs 68%, findability 65%, faulty tutorial 65%, outdated
  references 64%, erroneous code examples 59%, code–doc inconsistency 59%,
  "content is not useful in practice" 59%; format/presentation only 33%;
  missing code comments only 28%; superfluous content 55% and duplicate
  content 46% the main maintainability concerns; lack of time 65%.
  Grounds "content over presentation", single-sourcing, and the
  verification step. Grade: peer-reviewed mining + survey.
- Head, Sadowski, Murphy-Hill & Knight, "When Not to Comment", ICSE 2018
  (Google) — PDF fetched. N: 1,147 survey responses (60 seeking API usage),
  625 second survey, 26 interviews; Google C++. Verbatim: "a minority
  (between around 5–25%) of visits to implementation files were to learn
  about API usage"; 61.7% of 60 would have preferred the answer in the
  header; "274 of 601 surveyed developers reported ... 'Missing/poor
  documentation for an API'"; "updating documentation may provide only
  limited value for developers, while requiring effort maintainers don't
  want to invest" — the counterweight the skill's Bounds section reflects
  (document the public contract; do not pad). Grade: peer-reviewed, one
  company.
- Staleness: Forward & Lethbridge, DocEng 2002 (submitted PDF fetched;
  N=48): "Documentation is always outdated" — 43% somewhat, 25% strongly
  agree; 82% want tools that track code changes for documentation. GitHub
  Open Source Survey 2017 (opensourcesurvey.org/2017/, fetched; N=5,500
  random + ~500 non-random): "Incomplete or outdated documentation is a
  pervasive problem, observed by 93% of respondents" (the common
  paraphrase "incomplete or confusing" is not the report's wording); "60%
  of contributors say they rarely or never contribute to documentation";
  licence "very important" for 64% (use) and 67% (contribute). Tan,
  Wagner & Treude, EMSE 2023 (abstract-only): "most projects contain at
  least one outdated code element reference"; Wen et al. ICPC 2019
  (abstract-only): 1.3 billion AST-level changes, 1,500 systems. Garousi
  et al., IST 2015 (post-print abstract fetched; N=25, one company):
  up-to-dateness, accuracy, preciseness highest impact on usefulness;
  source code preferred during maintenance. Grade: mixed; direction
  consistent across two decades.
- Use of documentation as a learning resource: Stack Overflow Developer
  Survey 2025 (survey.stackoverflow.co/2025/developers/, fetched; 33,454
  answering of 49,019): "Technical documentation ...: 67.8%" — the top
  resource. 2026 survey (30,903 responses; top page and blog fetched; the
  learning sub-page 404): technical documentation top learning source at
  58.9% of the 52% who learned a skill — summary-only via IT Brief
  2026-10-06. Grade: vendor survey, self-selected.
- DORA: Accelerate State of DevOps 2021 (dora.dev PDF, pp. 21–23,
  fetched): "about 25% of respondents have good quality documentation";
  "2.4 times more likely to see better software delivery and operational
  (SDO) performance"; quality measured as helps readers accomplish goals /
  accurate, up-to-date, comprehensive / findable, organized, clear;
  practices: document critical use cases, update guidelines, owners, docs
  in the development process, recognition, "Automated testing for code
  samples". State of DevOps 2023 (pp. 27–30, fetched) REVISES the delivery
  claim: "We continue to be surprised to find no effect of quality
  documentation on software delivery performance. This is the second year
  we see this behavior", while reporting documentation amplifies the
  effect of technical capabilities and raises team/organisational
  performance, with a burnout caveat. Per-year N not in the extracted
  chapters. The skill therefore makes no delivery-performance claim.
  Grade: vendor survey; odds-style comparisons; causality not established.
- Agent-era preprints (labelled preprint, abstract-only):
  Chatlatanagulchai et al., "Agent READMEs", arXiv 2511.12884 (2025;
  N=2,303 context files, 1,925 repos): context files cover tests 75.9%,
  implementation 70.8%, architecture 68.1%, security 14.8%, performance
  14.5%. Gloaguen et al., "Evaluating AGENTS.md", arXiv 2602.11988 (2026):
  "providing context files does not generally improve task success
  rates", ">20%" inference cost, "repository overviews ... are not
  helpful". Guelman et al., "On the Quality of AI-Generated Source Code
  Comments", arXiv 2408.14007 v3 (2025; 142 classes, 273 methods, two
  expert raters): 58.8% equivalent, 27.7% superior; text-overlap metrics do
  not track human judgment. Grounds the skill's routing of CLAUDE.md/
  AGENTS.md elsewhere and its insistence on human-style review of
  generated docs; none of these numbers appear in the skill.
- Secondary-only (not fetched; via the papers above): Plösch et al. QSIC
  2014 (N=88: accuracy, clarity, consistency, readability, structuredness,
  understandability), Chen & Huang JSS 2009 (N=137), Nasehi et al. ICSM
  2012 ("explanations accompanying an example are as important as the
  examples themselves"), Lethbridge/Singer/Forward IEEE Software 2003
  (claimed ~40% time in docs vs 3% observed), Nykaza et al. SIGDOC 2002,
  Watson et al. SIGDOC 2013, Khan et al. SANER 2021 (five documentation
  smells; 95.2% of 21 developers say they hurt productivity).

### Current practice: docs-as-code, testing, freshness, llms.txt, agent files, AI-generated docs
- Testing and linting tools, self-descriptions fetched 2026-10-28: Vale
  (vale.sh, updated 2026-10-26) "A markup-aware linter for prose", ships
  Microsoft, Google, Red Hat style packages, 12 markup formats, GitHub
  Action and pre-commit (its "111 of 156 checked repos run Vale in CI" is a
  vendor adoption claim, sample unknown); markdownlint
  (github.com/DavidAnson/markdownlint) "static analysis tool for Node.js
  with a library of rules", `.markdownlint.json`; lychee
  (github.com/lycheeverse/lychee) "Fast, async, stream-based link checker
  written in Rust", `lycheeverse/lychee-action`; Python doctest
  (docs.python.org, 3.15.2, 2026-10-28) "To check that a module's
  docstrings are up-to-date by verifying that all interactive examples
  still work as documented". markdown-link-check not fetched. Grade:
  maintainer self-description, high for what each tool is.
- Freshness: Google timeless-documentation (2024-10-15) and future
  (2026-05-19) pages, SWE-at-Google freshness dates and owners (above),
  Diátaxis small-step iteration (above); Go wiki Deprecated.md
  (summary-only): `Deprecated:` paragraph, deprecation does not imply
  removal. No Google style page on "deprecated" or "document versions"
  exists (404; two searches).
- llms.txt: proposal (llmstxt.org, published 2024-09-03, modified
  2026-08-10, fetched): root `/llms.txt` Markdown, "An H1 with the name of
  the project or site. This is the only required section", optional
  blockquote, H2 link lists, `.md` page variants; the proposer's own
  adoption claims ("thousands of sites") are self-interested. Adoption
  verified directly 2026-10-28: platform.claude.com/docs/llms.txt (~800
  `.md` links; docs.anthropic.com/llms.txt 301s there) and
  code.claude.com/docs/llms.txt; docs.stripe.com/llms.txt (519 links, 517
  `.md`, plus "Instructions for Large Language Model Agents"; "Never
  hardcode an old version number from training data");
  developers.cloudflare.com/llms.txt (per-product index); Mintlify
  (mintlify.com/docs/ai/llmstxt) auto-generates `llms.txt` and
  `llms-full.txt` (the `-full` variant is a platform convention, not in the
  proposal) and its effectiveness claims carry no data. Use evidence, all
  crawler-fetch studies and none measuring coding agents: Ahrefs
  2026-06-15 (137K domains, SEO vendor) "28% ... publish an llms.txt file",
  "97% of those files received zero traffic in May 2026", "96% of the
  requests ... came from bots", AI retrieval bots ~1.1% (denominator
  ambiguous in the article), verdict "the cons outweigh the pros right
  now"; John Mueller via Search Engine Journal 2025-04-17 (secondary)
  "comparable to the keywords meta tag", "none of the AI services have
  said they're using LLMs.TXT"; an 83-site 2026 log study (summary-only,
  secondary; OpenAI 7 vs 3,990 robots.txt fetches, ClaudeBot 9 vs 3,120,
  Perplexity 0 vs 775, Meta the exception) and two single-site censuses
  (summary-only). Hence the skill: add only on request or when the
  generator already emits it; claim no benefit.
- Agent instruction files (one claim each): agents.md (fetched, undated)
  "A simple, open format for guiding coding agents", "complements
  [README] by containing the extra, sometimes detailed context coding
  agents need", Linux Foundation stewardship, self-reported 60k+ repos;
  code.claude.com/docs/en/memory (fetched 2026-10-28): "Keep it to facts
  Claude should hold in every session: build commands, conventions,
  project layout, 'always do X' rules", "target under 200 lines per
  CLAUDE.md file", `/doctor prompt-audit` flags stale or contradictory
  instructions, AGENTS.md read as project instructions when no CLAUDE.md
  (v2.1.277+). Anthropic engineering: "writing-tools-for-agents"
  (2025-09-11) "think of how you would describe your tool to a new hire",
  "eschew low-level technical identifiers"; "effective-context-engineering"
  (2025-09-29) "find the smallest set of high-signal tokens", sections
  with Markdown headers, "Folder hierarchies, naming conventions, and
  timestamps all provide important signals". No OpenAI guidance on docs for
  model readers located (not searched separately).
- AI-generated documentation policy: Hora & Robbes, arXiv 2605.16706
  (ICSME 2026, abstract fetched): of 1,000 popular repos, "118 AI
  policies", "78% ... allow AI-assisted contributions", "51% ... require
  the disclosure", "74% ... require a human in the loop"; LLVM AI Tool
  Policy (llvm.org, 2026-10-28, fetched): "Contributors must read and
  review all LLM-generated code or text before they ask other project
  members to review it", `Assisted-by:` trailer, approved use "using an LLM
  to generate documentation, which a contributor manually reviews for
  correctness"; FiPy, Nazara, Open Transit policies (summary-only) follow
  the same pattern; Grafana writers' toolkit AI quick reference
  (summary-only): verify product claims against source files, mark
  unverifiable ones `[UNVERIFIED]`. Google's gen-AI content page is Search
  Central SEO guidance, not a docs rule. No GitHub Docs page on
  AI-generated documentation found.

### Baseline and eval evidence for this skill (2026-10-28)
- Harness for every run: Claude Code 2.1.287 on the CLI, model resolved to
  claude-opus-5-5[1m] (the account's `opus[1m]` default), builtin plugins
  cc-plugin-agents-md, cc-plugin-plugin-authoring, cc-plugin-telemetry; no
  user hooks; the user's rules (anti-sycophancy, scope-discipline,
  artifacts, ste100) and every personal skill loaded in both arms. Fixture:
  `doc-author/evals/fixtures/logsift`, a five-module Python CLI with no
  docs, a config loader with a four-location search order, a 24-hour
  default window, and a `WARN` alias — written for this pass.
- Step 0 (three `claude -p --permission-mode acceptEdits` probes, Bash
  denied by the harness): READMEs and pages accurate against the code in
  every probe; failures were a getting-started page whose commands used a
  file the reader does not have while its shown output came from the
  repository's `sample.log`, reference material (format spec, option
  table) inside the tutorial, config documented inside the CLI reference,
  no version marker, and no verification loop (harness-conditioned: each
  probe said it could not run commands).
- Trigger eval (`trigger_eval.py`, 16 queries × 2 runs, $0.33): 16/16
  pass; recall 1.00 on 8 should-trigger queries (README, API docs,
  tutorial, docstrings, changelog, ADR, docs-tree review, config how-to);
  false-positive rate 0.00 on 8 near-misses, which routed to info-design
  (incident write-up), notes, project-author, mermaid, or no skill (commit
  message, script over docs, verbal explanation, team summary). No
  co-invocation of info-design on the should-trigger queries.
- A/B eval (`ab_eval.py --mode skill`, 3 tasks × 3 runs × 2 arms, Bash
  pre-allowed for python3/cat/ls/grep/etc., PATH giving Python 3.14 as
  `python3`, fixture copied to `./logsift`):
  - README: with $0.72±0.12, 33 turns, 98 s; without $0.45±0.04, 20 turns,
    58 s. Both arms accurate (search order, exit codes, aliases, UTC rule
    spot-checked), both warn about the 24-hour default, both use
    `sample.log`, neither adds badges or empty sections. With-arm ran every
    example (8–14 tool invocations of the CLI) and shows real output after
    each; without ran 2–3; one without run put a quick-start command on a
    file the reader does not have and left three fences untagged. Rubric:
    with 3/3, without 2/3. The rubric discriminator (runs at least one
    command) passes in both arms once Bash is allowed — the step-0 failure
    was the harness, not the model.
  - Getting started + CLI reference: with $0.73±0.09, 31 turns; without
    $0.48±0.01, 20 turns. Tutorial reproducibility: with 3/3 (each page has
    the reader create the input file verbatim or uses `sample.log`;
    numbered user actions; "notice that" sentences), without 0/3 (commands
    on an `app.log` the reader does not have, output from `sample.log`).
    Reference material inside the tutorial: with 0/3, without 3/3 (a log
    format section in every page). Config documented in one place: both
    arms 3/3. Reference completeness: with 3/3, without 2/3 (one run
    omitted exit codes). CLI invocations: with 10–16, without 2–4.
    Untagged code fences: with 0 across 9 pages, without 11 across two
    runs. Rubric: with 3/3, without 0/3 — the decisive result.
  - Configuration page: with $0.63±0.13, 19 turns; without $0.40±0.04,
    12 turns. Facts correct in all six runs (search order, first-found
    wins, `[logsift]` table, empty env var ignored, missing explicit file
    exits 2, unknown keys ignored); "which wins" in the top 30 lines 6/6;
    TOML example 6/6. Version marker: with 3/3 ("This page describes
    logsift 0.3.0"), without 0/3 (one "Known issue (0.3.0)" aside only).
    Length: with 132–191 lines, without 137–168 — neither arm wrote a
    short how-to; both wrote a configuration reference. Rubric: with 4/5,
    without 3/5.
  - Cost: the with-arm costs 50–60% more and takes about 60% longer on
    every task, from the verification loop (more CLI runs) and reading the
    two reference files. Untagged fences: with 0/9 runs, without 6/9.
- Skill text at A/B time: the version launched at 13:41; the "Reviewing an
  existing docs tree" section, the changelog release-time sentence, and
  the recurring-question mapping were added afterwards and are
  desk-checked only. Watch items (one pass, one model): the with-arm did
  not shorten the configuration page; one with-arm README put the 24-hour
  gotcha in a GitHub alert where the skill prefers plain text.

### Gaps a future pass should close
- Full text of Meng 2018, Nykaza 2002, Watson 2013, Wen 2019, Tan 2023
  (abstract-only); DORA 2021/2023 per-year respondent counts; the Stack
  Overflow 2026 learning-resources sub-page (404 this pass).
- No peer-reviewed study of llms.txt, and no measurement of coding agents
  reading `.md` page variants in-session; no 2023–2026 controlled
  experiment on developers using outdated documentation.
- The Art of README (404 everywhere) and Oracle's Javadoc style article
  (403); Apple Style Guide not fetched; Redocly best practices not fetched;
  the GitHub community-profile checklist table text not returned.
- Whether Keep a Changelog 1.1.2 is a spec version; Google's current
  contractions rule; Microsoft's own notes-and-tips page (404).
- A Diátaxis-vs-CTRT comparison from a primary source (none found).

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

### Anthropic, "Writing effective tools for agents"
- URL: https://www.anthropic.com/engineering/writing-tools-for-agents
- Last verified: 2026-11-02 (fetched; published 2025-09-11)
- Supports: "Make sure each tool you build has a clear, distinct purpose";
  "When tools overlap in function or have a vague purpose, agents can get
  confused about which ones to use"; "More tools don't always lead to better
  outcomes." Negative: the sentence "If a human engineer can't definitively
  say which tool should be used" is NOT on this page (a strand attributed
  it to the context-engineering post; not re-read by the lead, so not
  relied on). Grounds keeping notes and docs as two skills whose
  descriptions name the boundary, rather than a front door that overlaps
  every writer skill.

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

### Skill authoring best practices — additions read this pass
- URL: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices
- Last verified: 2026-11-02 (re-fetched in full, raw markdown, for this
  pass; see the core entry above for the standard sections). Read for this
  pass, verbatim: the "Conditional workflow pattern" — "1. Determine the
  modification type: Creating new content? → Follow 'Creation workflow'
  below. Editing existing content? → Follow 'Editing workflow' below"; its
  tip — "If workflows become large or complicated with many steps, consider
  pushing them into separate files and tell Claude to read the appropriate
  file based on the current task"; "Claude uses it to choose the right Skill
  from potentially 100+ available Skills"; and the naming section's
  "Overly generic: `documents`, `data`, `files`". The page states no rule on
  when to split one skill into two. Grounds the doc-author shape: one
  SKILL.md that routes by kind, with the software-docs body as a reference
  file, and the decision to keep the name doc-author rather than `docs`.

### Strand-read sources (claim records only; pages not opened by the lead)
- Diátaxis, start here — https://diataxis.fr/start-here/ ; four types by
  user need; nothing on working notes or drafts (negative finding).
- The National Archives (UK), Essential Records Management (PDF, 2009) —
  https://cdn.nationalarchives.gov.uk/documents/essential-records-management.pdf ;
  ISO 15489 definition of a record; capture into the filing structure is
  the dividing act; a personal mailbox "treated as an individually owned
  asset".
- GitLab handbook usage and handbook-first pages — search summaries only;
  the page body could not be fetched in four attempts (navigation only).
  "if the content is meant to be long lived it should be moved to the
  handbook as an SSOT". Not relied on beyond corroboration.
- Basecamp, How we communicate — https://basecamp.com/guides/how-we-communicate ;
  "Writing solidifies, chat dissolves"; "Where you put something, and what
  you call it, matters."
- Ubl, Design Docs at Google (2020-07-06) —
  https://www.industrialempathy.com/posts/design-docs-at-google/ ;
  author-owned, informal, reviewed sparingly, history after ship.
- SkillsBench (arXiv 2602.12670) — already in this ledger; "Focused Skills
  with at most three modules outperform larger or exhaustive bundles".
- RAG-MCP (arXiv 2505.03275) and "How Many Tools Should an LLM Agent See?"
  (arXiv 2605.24660, measured on Claude Sonnet 4.6): tool-count effects on
  selection accuracy (13.62% → 43.13%; 87.1% → 93.1%), from registries of
  dozens to thousands of tools, so directional only for 1 versus 2 skills.
- Community guides on splitting skill descriptions (hackernoon ai-coding
  tip 035; dak-dev skill pitfalls) — tier 3, unverified: split when
  triggers diverge; state the boundary in each description.
