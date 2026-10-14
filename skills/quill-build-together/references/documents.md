# Documents: generate, inspect and correct the result

Generating makes a document from a record and a template. Each generation
is a stored revision with a version label; editing a document makes a new
revision; final and locked documents keep their frozen PDF. Generation is
a gate: the template's rules judge each document first.

## When this file applies

"Make the engagement letter for this client", "regenerate it", "why did
it not generate", "is this the latest PDF", "fix the typo in the letter".

## The questions that matter

1. **Which record and which template**, and whether they want every
   document the template makes or one row's.
2. **Findings first.** Read the generate gate before generating; a stop
   means the answers or the rule need attention, not a retry.
3. **Edit the answers or edit the document.** A wrong answer should be
   fixed on the record so every later document is right; an edit on the
   document fixes this revision only. Recommend the record unless the
   document is final.

## Workflow

1. Validate with the generate gate for the design (or rehearse the
   generation) and read the report: which documents are admitted, which
   are stopped and by what.
2. Fix stopped answers from sourced facts, or record an exception
   (`logic/decisions`) when the rule is right in general and wrong here, or
   generate only the admitted rows.
3. Generate (`records.documents.generate`) and, once it is made, read the
   result: the document rows with their version labels and their rules
   receipt. On a test record, `design_version` names a template draft to
   render, so a draft can be tried before it is published.
4. Read the document: the content revision, and the PDF only when a list
   row says the stored PDF is present. An older PDF link is not the
   current bytes; a new edit has no PDF until it is rendered.
5. Say what was made, its version label, and where to see it (the record's
   Documents tab).

## Shapes that come up

- A document that should not change again: advance its status to final
  or locked; say that it then keeps its frozen PDF and edits make a new
  revision rather than touching it.
- A superseded document: record the one that replaces it rather than
  deleting.
- Delivery to a configured destination (a Drive folder, a storage
  destination) is set up by the organisation; say where the configured
  destination is and confirm the delivered revision is the intended one.
  Sending documents out for signature is not part of this plugin's jobs
  today; say so if asked and point to the admin UI.

## Verify

- The generated document opens and reads correctly, including conditional
  passages and tables.
- Its version label and rules receipt match the generation you ran.
- Nothing was generated for a stopped row.

## Library

`records/generation`, `documents/core`, `documents/pdf`,
`documents/delivery`, `documents/retention`, `logic/fill`,
`logic/document-problems`, `logic/decisions`.
