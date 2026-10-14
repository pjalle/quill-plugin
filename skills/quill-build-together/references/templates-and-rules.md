# Templates, their rules and tables: produce the right document

A template (Quill calls a template family a design) turns a record into a
document: fixed wording, places where answers go, passages that appear
only when a condition holds, and tables that repeat for each row of a
list. A template's own rules decide which documents may be generated.

## When this file applies

"Make an engagement letter from this", "the clause about children only
when there are children", "a table of the assets", "rename the field this
template reads", "why does this document not generate".

## The questions that matter

1. **Who reads it and what does a finished one look like.** Ask for one
   example output, or the Word document they use today. Separate fixed
   wording, information from the record, and repeated content.
2. **One representative passage first.** Build one paragraph with one
   answer in it and one condition, read it back, and let them react before
   building the whole document.
3. **What must stop a document.** A missing signatory, an unanswered date,
   shares that do not add up: these become the template's rules, not notes
   in the wording.

## Workflow

1. Read what exists: templates on the model (`templates/discovery`), the
   draft version (`templates/versions`, `templates/definitions`), and which
   fields it reads.
2. Edit content with the bounded tools (`templates/content`): replace text
   in a block, insert or move a node, set a mark, rename a field reference,
   set the output name. Tables have their own tools (`templates/tables`).
   Replace a whole subtree only for a deliberate rewrite.
3. Write the template's rules the same way as any rule (see
   `validation-and-rehearsal.md`), on the template version: prove them in
   the workbench, add them as drafts with examples, turn them on. A rule
   marked for every document judges every document; a rule about one row
   never stops another row's document.
4. Preview with contrasting synthetic cases: a record that should get the
   clause and one that should not; a list with none, one and three rows.
   Then generate on a test record, naming the template draft, and read
   the document (see `documents.md`).
5. Read the saved draft back before expanding it, and say where it shows:
   the Templates page, and the generated document on the test record.

## How answers go into the text

Template content is a tree of typed nodes, not text with braces: a
`{{name}}` in a paragraph prints literally. An answer is a `mergeField`
node, `{ "type": "mergeField", "attrs": { "fieldPath": "owner_name" } }`,
inline among the `text` nodes of a paragraph. A passage that appears only
when a condition holds is a `conditionBlock` with `attrs.field`,
`attrs.operator` and `attrs.value` around the nodes it guards; content
repeated for each row of a list is a `loopBlock`. Read one existing
template's draft before writing your first paragraph and copy its shapes.

## Shapes that come up

- A document per row of a list (one letter per beneficiary): the design
  makes one document per subject row; the rules that reach that row judge
  that document.
- Wording that differs by country: one template per country's form, or
  one template with conditions on the country, whichever keeps the family
  readable. Recommend one and say the cost.
- A field the template reads that the form later renames: rename the
  reference in the template in the same step, or the next generation
  fails its check.

## Verify

- The preview shows the clause with the condition met and omits it
  without.
- A generated document on a test record reads correctly in the generated
  PDF, not only in the editor.
- The template's rules report the stop they were built for and nothing
  else.

## Library

`templates/discovery`, `templates/versions`, `templates/definitions`,
`templates/content`, `templates/tables`, `templates/settings`,
`templates/batch_rehearse`, `templates/batch_apply`, `logic/rules`,
`logic/workbench`, `logic/document-problems`, `records/generation`.
`templates/checks` reads historical converted findings; it is not how a
new rule is written.
