# Platform contract

What the docs skill expects from the platform skill named in
`doc-platform`. A platform skill (for Outline, Confluence, Notion, a docs
repository, or any other store) does each operation in its own way and
says how in its own body. The docs skill speaks only in the vocabulary
below, so a change of platform changes one config value.

## Contents

- Vocabulary
- Operations
- What the docs skill sends
- What the platform skill returns
- When an operation is not possible

## Vocabulary

- **Home**: where a document lives. A container (a collection, a space, a
  folder) and a parent (a parent document, or the container root). Every
  document has exactly one home.
- **Status**: `draft` (readable by the author only), `published` (readable
  at its home), `archived` (kept and searchable, marked as not current).
- **Private area**: a home only the author can read.
- **Link**: a stable URL the platform resolves to the document.
- **Breadcrumb**: the container and parents from the root to the document,
  written `Container › Parent › Title`.

## Operations

| Operation | Meaning |
|---|---|
| Find | Locate documents by title, by text, or by place. Return the link, the breadcrumb and the last update of each. |
| Read | Return a document's text, its home and its status. |
| Create | Make a document from a title, a body, a home and a status. |
| Update | Change one passage, or replace the body. |
| Move | Give a document a new home. |
| Archive | Set the status to archived. Restore reverses it. |
| Link | Return the link for a document. |
| Private | File a document in the private area. |

## What the docs skill sends

- The title.
- The body, in Markdown, without a level-1 heading; the title carries it.
- The home, as a container and a parent, or as a description of where the
  document belongs when the docs skill does not know the platform's tree.
  The platform skill then proposes a home and says it before it files.
- The status: `published` unless the user asked for a draft.
- The owner, as a name, when the platform records one.
- Links to the related documents the body should point at.

## What the platform skill returns

- The link and the breadcrumb.
- The status.
- What the read-back changed: any passage the platform stored differently
  from what was sent.

## When an operation is not possible

The platform skill says so and offers the nearest alternative, with its
cost. It does not do something else in silence. The docs skill reports the
gap to the user.
