# Setup (English)

The whole thing takes about 15 minutes. Claude does most of the building. You connect an account, paste two pieces of text, and click a few things in Notion.

## What you need

- A Notion account (the free plan is enough)
- A Claude account with Projects
- (Optional) For the weekly reminder, scheduled tasks in your Claude environment

## Step 1: Connect Notion in Claude

In Claude's settings, find **Connectors**, add Notion and authorise it. Give Claude access to the page where you want the system to live (or your whole workspace).

## Step 2: Create a Claude project

1. Create a new project in Claude, named whatever you like, e.g. "reminder-brain".
2. Open `prompts/en/project-instructions.md` and copy everything between the two horizontal rules into the project's **Instructions**.
3. If you want different categories or star rules, edit the parts marked ✏️ now, or later.

## Step 3: Have Claude build the tables

Start a new chat in the project and send Claude everything between the two horizontal rules in `prompts/en/setup-notion.md`.

Claude asks where to put it, which categories to use and whether you want a weekly reminder. Once you confirm, it will:
- Create the Inbox, a to-do table and a Log table per category, and the Archive
- Set up the views and sorts
- Lay out the Action Board as colour blocks: one coloured box each for the Inbox, every category and the Archive, each with a line of explanation and its tables shown as links you click to open
- Write "working notes" into the project with every table's address
- (If you want it) set up the weekly reminder

## Step 4: Click a few things in Notion

Notion doesn't expose these settings to outside connections, so Claude can't change them and you need to click them yourself (see `notion-limits.md` for why):

1. **Show Progress as a bar**
   Open the Inbox, click the "Progress" column header → Edit property → "Show as" → "Bar" → divide by 100. Do the same in each category's to-do table.
2. **Default template: open a page and there's a checkbox**
   Open the Inbox, click the ▾ next to "New" at the top right → "+ New template" → in the body type `[]` and a space to leave one empty checkbox → close the template → back in ▾, click "⋯" next to the template → "Set as default" → "All views".

   Note: the default template only applies to items created **after** you set it. When you open an older empty item, Notion asks you to pick a template.

## Step 5: Try it

1. Jot three things into the Inbox, e.g. "Renew passport", "Buy cat food", "Finish chapter 3 of Atomic Habits".
2. Tick one of them.
3. Give another one two checkbox steps in its body, and tick one step.
4. Go back to the project chat and say "tidy up my board".

You should see: the ticked item archived into a Log and the Archive; the item with steps given progress 50 and left in the Inbox; and a card from Claude asking which category the last one belongs to.

See `examples/en/sample-session.md` for an example conversation.

## Optional: import from Apple Reminders

See `apple-reminders.md`.
