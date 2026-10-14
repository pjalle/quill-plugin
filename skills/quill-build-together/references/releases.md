# Releases: make the intended version usable

Nothing reaches the people filling in until it is published. Publishing is
a family release: a model, the forms and templates pinned to it, and every
changed member of that family in one plan. Quill computes the plan, gives
it a token, and executes exactly that plan with that token.

## When this file applies

"Publish it", "make it live", "go live with the Irish form but not the UK
one", "what has changed since the last release", "discard this draft".

## The questions that matter

1. **Which finished work goes live, and what must stay a draft.** The
   family plan lists every changed member; some may be someone else's
   unfinished work. Show the members and ask which to hold.
2. **What the release means for existing records.** A published model
   change can be breaking for records on the old version; the plan says
   so and needs that acknowledged. Say what it means in their terms
   ("records already filled keep the old version until they are moved").
3. **Which form is the model's default** after the release, when more than
   one form sits on it.

## Workflow

1. Read the changes since the last release (`releases.family.changes`) and
   any findings that would refuse publication: carried rules that no longer
   fit, examples that drifted, cleanup findings on the version. Fix or name
   them before planning.
2. Plan: `releases.publish.plan` for the model returns the members in
   dependency order and a plan token. Show the list in their words: "This
   publishes the Client model, the Ireland form and the engagement letter;
   the UK form draft would go too unless we hold it." Add version numbers
   only when an older version is live and the difference matters to them.
3. Name in one line what goes live and what is held, then go on by mode:
   - **On cards:** call the execution with that token, the holds, the
     breaking acknowledgement if the plan asked for it, and notes. The
     go-live card lists the members going live and what is held; say in one
     line that their tap publishes it, and stop. Only the tap publishes: an
     earlier "publish it" does not count, and never call
     `quill_change_confirm` for it.
   - **Direct:** rehearse the execution with that token and the holds, ask
     for the one yes this step needs, then execute with the same token, the
     holds, the acknowledgement and notes. Their earlier "publish it" is
     that yes; do not ask twice.
4. A stale token means something changed since the plan: plan again and
   show the difference.
5. Verify, once it is made: read the published versions back and the
   release in the history. Say in one or two sentences what went live and
   what was held, and that test records on the old draft pairing will stop
   opening. No table of members, ids or versions.

## Discarding a draft

Discarding is destructive and permanent. Name the exact version first.
On cards, only their tap discards it; directly, rehearse it and ask for a
yes even when they asked for it in passing.

## Verify

- The published form opens for a new record, on the published model
  version.
- The history lists the release with the members that were planned.
- Held members are still drafts.

## Library

`releases/family`, `releases/drafts`, `forms/versions` (passport and
health reads), `models/versions`, `templates/versions`, `logic/rules`
(publication refusals), `migration/impact` when records must move.
