# Everything else Quill does

The jobs in the other files are the ones most people start with. Quill
also imports existing content, cleans up models and forms, moves records
between versions, reviews records, connects to Salesforce, Google Drive
and webhooks, manages people, roles and keys, keeps saved test personas,
and shows billing. All of it is reachable through the same tools; the
library holds each procedure.

## One procedure for all of them

1. **Outcome and reach.** Ask what they want at the end and which things it
   touches (a model, every record on it, an integration, a person). Say the
   reach back in one line before doing anything.
2. **Authority and procedure.** `quill_orient` for what the connection may
   do in that area; `quill_catalogue` to find the capability by area;
   `quill_library` for its procedure, preconditions and refusals. Read the
   procedure before the first call.
3. **Smallest authorised change, then verify.** Rehearse what can be
   rehearsed, make the change (on cards, once they tap or say yes), read
   it back, and say where it shows.

## Where things live

| They want to | Area and library |
| --- | --- |
| Bring a form or document they already have into Quill | `import/jobs`, `import/review` |
| Find and fix unused fields, broken references, stale drafts | `cleanup/findings`, `cleanup/plans`, `cleanup/receipts` |
| Move records to a newer model version | `migration/impact`, `migration/batches` |
| Comment on and review records | `reviews/general` |
| Recover something deleted | `trash/items` |
| Salesforce, Google Drive, embedded hosts, webhooks, storage | `integrations/salesforce`, `integrations/google-drive`, `integrations/embedded`, `integrations/webhooks`, `integrations/storage-destinations`, `integrations/setup-guides` |
| Saved test personas for trying a form | `personas/library` |
| What the plan includes and costs | `billing/status` |
| Approvals waiting on a person | `mandates/approvals`, `mandates/oversight` |
| Keys, credentials and developer settings | `developer/profile`, `developer/credentials`, `developer/mint`, `developer/secrets` |
| Sending for signature, delivering documents out | Not part of this plugin's jobs today. Say so and point to the admin UI. |

## Boundaries

- Bulk operations over many records, credential administration and
  integration setup change things for other people. Show the reach, ask
  for the one yes the step needs, and prefer a rehearsal or a small batch
  first.
- Settings that affect every member (roles, keys, billing) are for an
  owner or admin; if the person cannot, say who can.
- Never ask for, show or store a secret. Keys and credentials are minted
  and shown in the admin UI to the person who may hold them.
