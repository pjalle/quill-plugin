# Fill links: let the intended person supply the answers

A fill link is a web address that lets someone outside the organisation
fill a record in, without an account. A record fill link opens one
existing record; a form fill link creates a new record each time it is
used. Minting a link sends nothing: the person still has to send it.

## When this file applies

"Send this to the client to fill in", "a link for new enquiries", "the
client lost the link", "cancel the link I sent".

## The questions that matter

1. **New record or existing one.** "Let the client complete what we
   started" is a record link; "anyone who wants to enquire" is a form
   link.
2. **Who should be able to open it, and for how long.** A link is a bearer
   address: anyone holding it can open it. Offer verification (the
   recipient proves an email or identity before filling) and an expiry
   date; recommend both for anything personal.
3. **Which form and version** a form link uses, and whether a draft version
   is intended (for testing) or the published one.

## Workflow

1. Confirm the record or form, read it, and check its readiness with the
   fill rehearsal when the link is for completing a record.
2. State what will happen in one line: "This makes a link to the Smith
   record that works until 31 October and asks for an email code first.
   It sends nothing." Minting is a commit: directly, wait for the yes
   before you mint; on cards, the mint call shows the card, so stop there
   and let them tap or say yes.
3. Mint (`fill_links.record.mint` or `fill_links.form.mint`) and, once it
   is made, give them the link once, with its expiry and verification in
   the same line.
4. Say how to revoke it (`fill_links.record.revoke`) and that a revoked
   link stops working at once; offer to mint a fresh one. On cards,
   revoking takes their tap.

## Shapes that come up

- A link for a client, then an answer the client gave by email: enter it
  on the record from the email as the source; the client's link keeps
  working on the same record.
- Several links on one record: list them before minting another; revoke
  the ones no longer wanted.
- Embedding a form on their own website is a separate setting
  (`fill-links/embed`); point there when they ask for "a form on our site".

## Verify

- The link opens the intended form or record (open it yourself only when
  verification allows; otherwise read the link back from the list).
- The list shows the link with the expiry and verification you set.

## Library

`fill-links/general`, `fill-links/embed`, `records/lookup`, `logic/fill`,
`forms/discovery`.
