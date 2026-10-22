# What Claude can change, and what you click yourself (English)

Claude works with your Notion through Notion's official connector. It can change **data and structure**, but not **interface settings**.

This isn't about permissions. Notion simply doesn't expose these features to outside connections, so granting Claude full access wouldn't help. Think of it this way: in the Notion app you have the full menu; Claude has a remote control with only some buttons. All the everyday data operations are there, but interface settings like templates and some layout options haven't been added to the remote yet.

> This reflects how things were when this was written (October 2026). Notion may open up more later.

## Claude can do directly

- Create, edit and delete items
- Change page body content (e.g. add checkboxes)
- Add and remove properties, change property types and descriptions
- Change a view's sorts, filters and visible columns
- Apply an **existing** template when creating an item

## You click these in Notion

| What you want | Where to click |
|---|---|
| Show a number as a bar or ring | Column header → Edit property → Show as |
| Create a template, set the default | ▾ next to "New" → New template; "⋯" next to the template → Set as default |
| Remove a block from the page layout | Open any item → "⋯" at the top right → Customize layout |
| Turn sub-items on or off | "⋯" at the top right of the view → Sub-items |
| Make a page public or duplicable | "Share" at the top right of the page |

## Gotchas we hit

- **Default templates only apply to new items.** When you open an older empty page, Notion asks you to pick a template instead of applying it.
- **Percent format is easy to get wrong.** With a number property in percent format, typing 30 shows 3000%. That's why "Progress" here is a plain number shown as a bar and divided by 100: type 30 and it means 30%.
- **Renamed properties can get a suffix.** If the new name matches a property you just deleted, Notion may add " 1" or " 2". Have Claude read the table structure back after renaming.
- **Formulas can't read the page body.** Notion formulas can't see checkboxes in the body, so "progress from checkboxes" is worked out by Claude during a tidy-up, not live.
- **Why no sub-tasks.** Notion has built-in sub-tasks (sub-items), but they're heavy for 1–3 step chores: every step becomes its own row and crowds the Inbox. Checkboxes in the body are lighter.

## A note for Claude

Section 4 of the project instructions already says: when proposing a change, Claude says up front which steps you need to click yourself in Notion, and exactly where, rather than discovering mid-way that it can't do them.
