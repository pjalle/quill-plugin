# Validation and rehearsal: make good answers work

A rule lives on a model or form version and judges records: it can stop a
record from completing, flag it for a check, or only advise. Rules are
written in Quill's rule language, proved on examples in the workbench, and
turned on as a draft, a trial or live. Named formats and value lists in the
organisation library let one definition check the same kind of value
everywhere.

## When this file applies

"Make every field enforce proper input", "an Eircode has to look like D02
X285", "the shares must add up to 100", "two people cannot be the same
person", "why was this record refused", "test this record before I send
it".

## The questions that matter

1. **One wrong case and one awkward valid case.** Ask for a value they know
   is wrong and one that is unusual but real. A pattern nobody tested
   refuses a real customer.
2. **What should happen**: stop the record (a block), send it for a check
   (a warning they must look at), or just advise. Fixed formats (postcode,
   national id, company number, email, phone, a percentage outside 0 to
   100, a negative amount) block; conventions ("starts with a capital")
   warn, because real names break them.
3. **Which kind of value**, not which field. Think in kinds: person name,
   street, town, postcode, national id, company number, phone, email,
   share, amount. One named format per kind in the organisation library,
   applied to every field of that kind, so a street is checked the same way
   wherever it appears.
4. **The message** shows the shape ("An Eircode looks like D02 X285"), not
   the rule's name.

## Workflow

1. Read what already applies: the rules on the version (`logic/rules`), the
   organisation library of formats and value lists (`logic/library`), and
   the rule suggestions Quill derives from the structure (two lookups that
   must differ, shares that add up, dates in order).
2. Draft in the workbench (`logic/workbench`): write the rule, validate it
   against the model, render it back to check it says what they meant, run
   it on the good and bad examples until each agrees, and analyse it so no
   proven finding is left unexplained. Start from a recipe for a common
   shape rather than writing text.
3. Put it on the version as a draft with its examples (`logic.rule.add`),
   rehearse the change, then turn it on at the tier they chose. A change to
   a live rule on a published version needs a reason; a change that lapses
   earlier decisions needs that accepted explicitly. Turning a rule on may
   need an owner or admin; if the person cannot, save it as a draft and say
   who can turn it on.
4. Show it working: on a test record, enter the bad values and read back
   what blocks and what only warns, in a few short sentences.
5. Before a record completes or a document is generated, rehearse the fill
   (`logic/fill`): validate the answers, read the findings, fix only from
   facts you can source, and say what still waits on the person.

## Shapes that come up

- Several yes/no questions feeding one rule: word them so the same answer
  is the concern on all of them, or "No, No" reads as fine when it is not.
- When rewording flips a question's meaning, rename the model field with
  it, so stored data still means what its name says. Cheap on a draft, a
  migration once published.
- A follow-up that depends on how many rows a list has: a hidden calculated
  count on the row, and the rule reads it.
- Exceptions: a record can carry a recorded decision for a rule that does
  not fit this one case (`logic/decisions`). Offer it when the rule is
  right in general and wrong here.

## Verify

- Every rule has at least one example that passes and one that fails, and
  analysis reports no surviving mutation.
- A test record shows the message where expected and nowhere else.
- The person has seen the awkward valid value accepted.

## Library

`logic/workbench`, `logic/rules`, `logic/rules_batch`, `logic/library`,
`logic/discover`, `logic/fill`, `logic/decisions`, `logic/evidence`,
`logic/understand`, `logic/quality`, `forms/rehearsal`.
