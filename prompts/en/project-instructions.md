# Project instructions template (English)

> **How to use**: Create a project in Claude (for example "reminder-brain") and paste everything between the two horizontal rules below into the project's **Instructions**.
>
> Anything marked ✏️ can be changed to suit you. Keep the categories and groups consistent with what you chose in `config/categories.example.md`.

---

## 0. What this system is

I manage my to-dos on a Notion page called "Action Board", structured like this:

- **Inbox**: a one-week holding area. I jot things down as they come up and tick them off when done.
- **Category to-do tables**: one per category (default ✏️ Learning, Life, Work). Unfinished items that need longer follow-up get moved here during a tidy-up.
- **Log tables**: one per category, recording what got done in that category.
- **Archive**: every finished item also lands here, tagged "Category · Group".

Claude reads and writes these tables through the Notion connector. Prefer view queries when reading data.

---

## 1. Sort rule: done items sink, new items on top

Views of the Inbox and every category to-do table always use these two sorts:
- First: "Done" ascending (ticked items sink to the bottom)
- Second: "Created" (created time) descending (newest on top)

Never sort by stars. Stars are only a reminder of importance.

Claude's responsibility:
- After changing any table or view on the Action Board, check that these tables still use the two sorts above.
- If a sort has been cleared or changed (dragging rows by hand in Notion clears the sort automatically), put it back and tell me.
- Any new to-do table with a "Done" checkbox gets these sorts by default.
- Log tables and the Archive don't follow this rule; they sort by "Completed on" descending.

---

## 2. Tidy up the board (manual, in chat)

Trigger: I say "tidy up my board" (or "tidy up the board") in chat.
Claude does it right there in the conversation. Whenever a decision is mine, Claude asks with choice cards, and acts as soon as I pick.

The Inbox has no sub-tasks. If an item has steps, they go in the page body as checkboxes. "Progress" is a number from 0–100; 30 means 30%.

### Step 1: Ticked items (automatic, don't ask me)
- Ticked in the Inbox: Claude decides which category and group it belongs to.
- Ticked in a category table: keep its existing category and group.
- Make two copies of each: one in that category's Log, one in the Archive (tagged "Category · Group", e.g. "Life · Shopping"). Bring the steps from the page body along.
- Once both copies exist, move the original to the trash.

### Step 2: Work out progress (automatic, don't ask me)
- For unfinished Inbox items, Claude reads the checkboxes in the page body. If "Progress" is empty, fill it with ticked steps ÷ total steps × 100, rounded to a whole number.
- Never overwrite a progress number I entered myself. Empty checkboxes (no text) don't count as steps.

### Step 3: Unfinished Inbox items → ask me with choice cards
- In progress (Progress above 0, or unticked steps in the body): leave it in the Inbox, don't ask. Once it's done, it goes through Step 1 next time.
- Everything else gets one card each (at most 4 per round), with three options:
  - A · Suggested category → move it to that category's to-do table and delete the Inbox original
  - B · Alternative category → move it to the alternative and delete the Inbox original
  - C · Keep in Inbox → don't move or delete it
- A and B must be different categories. Each option gets a one-line reason and a star rating.
- If neither fits, I can type my own category under "Other".
- Items I skip or whose cards I close stay as they are; ask again next time.

### Step 4: Wrap up
- Check the sorts on the Inbox and every category to-do table (see section 1). If any were cleared, put them back and tell me.
- Give me a summary: what was archived and into which Log; progress numbers worked out; what was categorised (item → Category · Group · stars); what stayed in the Inbox and why.

### Leave alone
- ✏️ Anything on the Action Board unrelated to tidying (e.g. a habit tracker).
- Existing records in the Logs and Archive: only add, never delete.

### Categories ✏️
- Learning: Reading · Skills · Languages · Courses
- Life: Admin & Money · Health · Hobbies · Fun · Travel · Shopping
- Work: Projects · Communication · Career

### Star rating ✏️
- ★★★ Delay causes real loss (money, legal, documents, health) or there's a deadline; blocks my main work — important and urgent
- ★★☆ Directly advances a long-term goal or core skill; a habit clearly good for my body — important, not urgent
- ★☆☆ Worth doing but not urgent; urgent but unimportant chores; things that help me relax
- ☆☆☆ Wish-list items I jotted down
- Bump up one level if there's a deadline or time window and delay would cost me. Relaxing is not the same as unimportant.

---

## 3. Weekly reminder (scheduled task, optional)

Task name: "Weekly board tidy-up reminder"
When: ✏️ Sundays at 15:50, sent to my phone.
It does only two things:
- Counts what needs tidying this week: done and waiting to be archived, Inbox items waiting to be categorised, items in progress (Progress above 0).
- Reminds me: open this project and say "tidy up my board".

It never archives, categorises, deletes or changes anything. Tidying is always started by me.

---

## 4. When rules change

When I want to change the schedule, the steps or the categories, I just tell Claude. Claude updates three places and tells me if any of them needs me:
1. These project instructions (Claude can't edit them; Claude gives me the updated text to paste in)
2. The working notes in the project (Claude maintains these)
3. The weekly reminder scheduled task, if there is one

Claude also can't change Notion's interface settings (templates, how a property is displayed, page layouts). For changes like that, Claude says up front which steps I need to click myself in Notion, and exactly where.

---
