# Setup prompt (English)

> **How to use**: First connect the Notion connector in Claude, then create the project and paste the instructions as described in `docs/en/setup.md`. Then start a new chat in that project and send Claude everything between the two horizontal rules below.
>
> Claude will ask you a few questions first (which categories, where in Notion to put it), and only start building once you confirm.

---

Please set up the "reminder-brain" to-do system in my Notion. The project instructions are the source of truth for the rules. Follow the steps below, and give me a short update after each one.

## Step 0: Ask me first, build only after I confirm

Ask me with choice cards:
1. **Where**: create a new page called "Action Board" in my Notion, or put it under an existing page I name?
2. **Categories and groups**: the default is below. Ask whether I want to change it. I can add or remove categories, rename them, or change groups:
   - Learning: Reading · Skills · Languages · Courses
   - Life: Admin & Money · Health · Hobbies · Fun · Travel · Shopping
   - Work: Projects · Communication · Career
3. **Weekly reminder**: do I want one? If yes, which day and time (default Sundays 15:50)?

List the structure I confirmed back to me, and start building once I say "go".

## Step 1: Create the Inbox table

Inside the "Action Board" page, create a database called "Inbox". Make it a full-page database (not inline), so on the Action Board it shows as a single link and the table opens when you click it. Properties:

| Property | Type | Notes |
|---|---|---|
| Item | Title | |
| Done | Checkbox | |
| Progress | Number (plain number, not percent format) | Description: "Enter 0–100; 30 means 30%. If empty, Claude works it out from the body checkboxes during a tidy-up" |
| Importance | Select: ☆☆☆ / ★☆☆ / ★★☆ / ★★★ | Description: "Three stars is most important" |
| Planned for | Date | Optional |
| Created | Created time | |
| Last edited | Last edited time | |

Views:
- "To do" (table): show Done, Item, Progress, Importance, Planned for, Created; sort "Done" ascending + "Created" descending.
- "🤖 To archive" (table): filter Done = true.
- "🤖 To sort" (table): filter Done = false.

## Step 2: Two tables per category

For each category (e.g. "Learning"), again as full-page databases:

**To-do table**, named after the category (e.g. "Learning"), with properties:
- Item (title), Done (checkbox), Group (select; options are this category's groups), Importance (same four star levels), Progress (same as Inbox), Notes (text), Created (created time), Last edited (last edited time)

Views:
- "By group" (table): grouped by "Group", hide empty groups; sort "Done" ascending + "Created" descending.
- "🤖 To archive" (table): filter Done = true.

**Log table**, named "Category · Log" (e.g. "Learning · Log"), with properties:
- Item (title), Group (select, same as above), Completed on (date), Importance (same as above), Notes (text)

View: table, sorted by "Completed on" descending.

## Step 3: Create the Archive table

A full-page database. Properties: Item (title), Category (select; options are every "Category · Group" combination, e.g. "Life · Shopping"), Completed on (date), Importance (same as above), Notes (text).
View: table, sorted by "Completed on" descending.

## Step 4: Lay out the Action Board as colour blocks

Don't spread the tables across the Action Board. Give each area its own coloured block (callout) containing a bold title, one line of explanation, and that area's tables. Because the tables are full-page databases, each shows on the page as a single link you click to open. That way the Action Board shows the whole structure at a glance.

Layout, top to bottom:

| Block | Icon · colour | Position | Tables inside | Text |
|---|---|---|---|---|
| Inbox | ✅ blue | Full width | Inbox | A one-week holding area: one line per item, no sorting needed; newest on top, ticked items sink. For things with steps, open the item and write checkboxes in the body. On "tidy up my board", done items go to the Logs and Archive, items in progress stay here, and the rest are put to you on cards |
| Learning | 📚 purple | Full width | Learning, Learning · Log | This category's groups, plus a line on what goes here |
| Life | 🌿 yellow | Left column | Life, Life · Log | This category's groups |
| Work | 💼 orange | Right column (beside Life) | Work, Work · Log | This category's groups |
| Archive | 🏁 grey | Full width | Archive | The record of everything done: each entry tagged "Category · Group", newest first |

If my categories aren't the default three: one block and one colour per category; the first category takes a full row, and the rest go side by side in pairs.

## Step 5: Check

- Read every table's properties and views back and confirm they match the above.
- Confirm the Inbox and every category to-do table sort by "Done" ascending + "Created" descending.
- Read the Action Board back and confirm every table sits in its block and shows as a link, not an expanded table.
- Create a test item "Test: buy milk", confirm you can read and write it, then delete it.

## Step 6: Write working notes

Create a document in this project called "reminder-brain working notes", recording:
- Each table's name and internal address (database / data source / view IDs or URLs), so future chats can find them directly.
- The categories and groups I confirmed.
- The setup date.

## Step 7: Weekly reminder (if I want one)

Use Claude's scheduled tasks to create a weekly reminder from the template in `prompts/en/weekly-reminder.md`, replacing the placeholders with the real view addresses from Step 6. If scheduled tasks aren't available here, tell me and skip this step.

## Step 8: Tell me what I need to click myself

Some settings can't be changed through the Notion connector. At the end, list them for me with exactly where to click:
1. **Show Progress as a bar**: open the Inbox, click the "Progress" column header → Edit property → Show as "Bar", divide by 100. Do the same for each category to-do table.
2. **Default template**: open the Inbox, click the ▾ next to "New" at the top right → New template → in the body type `[]` and a space to leave one empty checkbox → back in ▾, click "⋯" next to the template → Set as default → All views.
3. If any view's grouping or sorting didn't take, tell me which view and how to set it.

---
