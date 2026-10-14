# Records and filling: enter, read and complete answers

A record holds one case's answers on a published model, filled through a
form. It is a draft until it completes; completing runs the rules. Answers
can be entered by a person in the admin UI, by someone with a fill link,
or by you through the tools.

## When this file applies

"Put this client in", "what did we answer for X", "finish this record",
"why will it not complete", "fill it from this email", "find the record for
Smith".

## The questions that matter

1. **Which record.** Find it before asking: by name or reference through
   `records/lookup` or `records/discovery`. If several match, show them
   and ask which.
2. **Where each answer comes from.** Only enter what you can source: their
   message, a document they gave, an existing record. Say the source for
   anything you inferred, and leave unknown answers empty rather than
   guessing.
3. **Draft or complete.** Saving a draft stores answers; completing judges
   them. Ask which they want when it is not obvious; "enter this" is a
   draft.

## Workflow

1. Read the record: its answers, each row's id, the time it was last
   changed. Read which rules apply and what each answer may hold
   (`logic/discover`).
2. Compose the change as answer changes, with your own ids for new rows.
3. Rehearse when they want the verdict first, or when completing: validate
   with the same changes and keep the evaluation hash.
4. Write with the record's last-changed time and the evaluation hash. A
   refused completion still saved the answers: say so, repair what the
   findings name from facts you can source, and complete again. If the
   rules or the day moved, rehearse again.
5. Stop and report when a finding needs a fact only the person or their
   client knows; offer a record fill link for that (see `fill-links.md`).
6. Say what the record holds now, whether it is complete, and where to see
   it (the Records page, the record's history).

## Shapes that come up

- A fact only the client knows: do not invent it; mint a fill link or ask
  the person.
- Two tabs writing one record refuse each other's saves; if they have the
  record open, say so before you write.
- A record on an older model version may need moving before a new form or
  template applies to it (`migration/impact`).
- Copying a record to start another: `records/copy`; say what is copied
  and what starts empty.

## Verify

- The record reads back with the answers and the right completion state.
- Findings on the record are the ones expected, with their sources.
- The person has been told what still waits on them.

## Library

`records/lookup`, `records/discovery`, `records/core`, `records/create`,
`records/copy`, `records/metadata`, `records/views`, `records/exports`,
`logic/fill`, `logic/discover`, `logic/decisions`, `reviews/general`.
