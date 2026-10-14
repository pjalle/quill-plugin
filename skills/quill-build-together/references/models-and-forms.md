# Models and forms: collect the right information

A model is what an organisation knows about a case: people, things, lists
of them, and the answers about each. A form is one screen set that
collects it. Several forms can sit on one model. Every record is filled
through a form and stored on the model.

## When this file applies

"Help me build a form for X", "add a field", "put these side by side",
"we also need to ask about Y", "make a version for Ireland", "a list of
children", "is this question hidden or locked".

## The questions that matter, in order

1. **Outcome first.** What do they want at the end of the first good case:
   a filled record, a document, a link they send? One representative case
   ("a new client with two children and a house") is worth more than a
   list of fields.
2. **Structure before fields.** Who are the people and things, which of
   them repeat (a list), and does one list hold different kinds of row (a
   variant)? Ask this early; field names and labels can wait. Do not propose
   a sublist or variant because it exists; propose it because their case
   repeats.
3. **One model, one form per country or branch.** Shared facts live once on
   the model; what differs by country goes on that country's form (labels,
   currency, phone country, national formats). Name forms so the family
   reads as one in a list ("Client | Ireland", "Client | United Kingdom").
4. **Settle the form's habits once.** Hidden or locked follow-ups, searchable
   or plain choice lists, a notes box per page. Apply `house-style.md`
   unless they say otherwise, and say which default you took.

## Workflow

1. Read what exists: `models.discovery.list`, then the model's versions and
   the current draft definition; `forms.model.list` for the forms on it and
   `forms.versions.get` for the draft they mean. A published model changes
   through a new model draft; the form draft is then relinked to it. Say so
   when it applies.
2. Build the smallest useful section first: the first page with the people
   and the one or two facts the case turns on. A new model takes two calls:
   `models.versions.create` with the id, the version and a model holding
   only its title and an empty field list, then `models.assemble` on that
   version with the categories and fields in one step (it needs the
   `model_id` and `version` it fills). Rehearse, then execute with the
   plan hash the rehearsal returned; a rehearsal saves nothing, so do not
   rehearse the same change twice. Then create the form draft and read both
   back. On cards each of these calls is its own card: let one be made
   before you prepare the next that needs it.
3. Add fields and sections one small step at a time with the bounded tools
   (`models.field.add`, `forms.field.add`, `forms.section.add` and their
   update twins) rather than replacing whole definitions; whole-definition
   writes are for a new form or a deliberate rewrite.
4. After each change, read the draft back and say where it shows: the
   Forms page shows the draft; a test record on the draft shows the fill
   page. Offer to create a test record when the structure has settled so
   they can see it filled in.
5. Expect a walk-through to cut things: a question whose answer the form
   already knows goes; "is the spouse an executor?" goes when the person
   just picks the executors. Offer those cuts yourself.

## Field types

Use the type names the tool schema lists: `text`, `multiline_text`,
`rich_text`, `number`, `currency`, `percentage`, `date`, `time`,
`datetime`, `email`, `phone`, `boolean`, `picklist`,
`multi_picklist`, `lookup`, `formula`, `address`, `location`,
`drawn_signature`, `image`, `booking`, `url`, `ranking`. A yes/no
question is a `boolean`; `displayMode` (`checkbox`, `radio`,
`slider`) applies to booleans only. A long answer is `multiline_text`.
A required answer is a `required` validator on the field; a yes/no that
must be yes is a `booleanValue` validator with its message.

## Shapes that come up

- **Rows of one list fall into kinds** (a child of both partners, of one,
  of the other): tag each row with its kind in one field rather than one
  yes/no per kind. "All children" stays one question for a template, and
  each placement can filter on the kind.
- **A question that opens follow-ups**: lock the follow-ups until it is
  answered (the page does not jump) or hide them (the page stays short).
  Ask once which is the form's habit; locked is the default.
- **Side by side**: put short related questions in one row; a long text or
  a list stays on its own line. Two rows that should line up need the same
  number of cells; fill a short row with an empty space element.
- **"It is the same for almost every row"**: make the repeated thing its
  own small list with an "applies to: all or one" choice, instead of
  repeating it under every row. Say the cost: the form cannot check that
  every row is covered.
- **A choice list** is a searchable picklist once it has more than a few
  options; people and organisations are always searchable. Where the
  answers are known, turn free text into a choice with an "Other" box
  locked until "Other" is picked.
- **A placement of a list that has kinds** always names the kind; rows
  added through an untyped placement carry no kind and show nowhere else.
- **A calculated field** is only computed where it is placed; a count that
  gates something must be placed (hidden) on the page that needs it.

## Working on a form they are also editing

- Read the live draft before every change; its concurrency token moves when
  they save in the builder. Never regenerate a form over their layout:
  change the draft in place, only what was asked.
- Before a write, ask whether their builder tab is saved. After a write,
  tell them to reload that tab; it holds the old copy and its next save
  would be refused.
- Reproduce a bug on your own test record, not on the record they have
  open.
- Once they publish, test records made on the old draft pairing stop
  opening; make a new one and say so.

## Building from their existing paperwork

- Read the documents they give you before asking what they hold. A
  dropdown's choices are often lost in a text export; ask for the original
  file when the choices matter.
- Build the first version from the paperwork, then expect the walk-through
  to cut it back. Mark anything you took from your own knowledge (a
  postcode format, a threshold) as unconfirmed and name who should check it.
- A dropdown's choices are permanent once saved; Quill refuses a save that
  removes one because records may hold it. Use the override only on a draft
  with test records alone, and say that old answers must be picked again.

## Verify

- The draft reads back with the change and nothing else moved.
- A test record on the draft shows the field, the lock or hide behaves,
  rows added in one placement appear where they should and nowhere else.
- Three states for anything conditional: not answered, yes, back to no.

## Library

`models/discovery`, `models/versions`, `models/definitions`, `models/fields`,
`models/sublists`, `models/variants`, `models/option_sets`,
`models/categories`; `forms/discovery`, `forms/versions`,
`forms/definitions`, `forms/fields`, `forms/sections`, `forms/rows`,
`forms/stacks`, `forms/conditions`, `forms/sublists`, `forms/child_sublists`,
`forms/sublist_fields`, `forms/meta`, `forms/rehearsal`.
