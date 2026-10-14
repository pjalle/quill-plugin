# House style: how a form should feel

Apply these when you build or reshape a form, without asking first, and
say in one line which you applied. They are Quill's opinion, not rules of
the platform: the person can overrule any of them in a word, and you keep
their choice for the rest of the conversation.

- **A yes/no answer is a switch, not a checkbox.** Give the two sides words
  ("Yes" / "No"), so an unanswered switch reads differently from "No".
- **A choice with more than a few options is a searchable picklist.** Three
  or four options may stay a plain picklist or radio cards; anything a
  person would scan for (countries, relationships, roles) is searchable.
- **A picker of people or organisations is always searchable.** Lists of
  people grow, and the person filling in knows the name they want.
- **Turn free text into a choice where the answers are known.** A reviewer
  who reads many records wants the same words every time; keep a free-text
  "Other" beside the choice, locked until "Other" is picked.
- **Put short related questions side by side** so the page scrolls less: a
  question with its follow-up, a name with an age, three switches in a row.
  A long text box or a list stays on its own line.
- **Lock, do not hide, a follow-up.** A follow-up that is visible and
  locked until its question is answered shows what an answer opens up and
  keeps side-by-side questions in place. Hide only what would be noise
  when locked: a whole page, a whole list most people never need, a
  question with no meaning for this client.
- **When something in a row does hide, confine its neighbours to their own
  column** (the item's column width setting), so the row does not reflow.
- **Line rows up.** Two rows that belong together get the same number of
  cells; fill a short row with an empty space element.
- **One model for every country or branch, one form per country.** Shared
  facts live once in the model; what differs by country goes on that
  country's form: labels ("Postcode" is "Eircode" in Ireland), the currency
  symbol, the phone country, and the formats for national values. A field
  only one country needs still goes on the shared model; only that
  country's form shows it.
- **Say the same thing the same way on every form of a family:** the same
  page order, the same page titles where the content is the same, the same
  notes box at the foot of every page.
- **Every field enforces proper input** once the structure has settled: one
  named format per kind of value in the organisation library, blocking
  only what is certainly wrong (see `validation-and-rehearsal.md`).
- **Names tell the family apart.** When you copy a form to start another,
  change both its names: the saved name and the title inside its
  definition. They are stored apart and shown in different places.
