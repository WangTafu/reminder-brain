# Optional: import from Apple Reminders (English)

If your to-dos currently live in Reminders on your iPhone or Mac, you can move them into the Notion Inbox in one go and then tidy them up as usual.

After the move, we suggest **jotting new things straight into the Notion Inbox** rather than using both. Two lists drift apart quickly.

## Option A: let Claude read Reminders directly (easiest)

On some devices the Claude app can read your Reminders, for example on an iPhone where you've granted Claude access to Reminders. If yours can, say in the project chat:

> Read the unfinished items in my Reminders list "<list name>" and add each one to the Notion Inbox. Copy titles as they are, put any notes in the page body, and put due dates in "Planned for". List them for me when you're done.

If Claude says it can't read Reminders, use option B or C.

## Option B: copy and paste (works anywhere)

1. In Reminders on a Mac, open a list, press `Cmd + A` to select all, then `Cmd + C` to copy.
   On an iPhone, copy items one by one, or use option C.
2. Paste into the project chat and add:

   > These are to-dos copied from Reminders, one per line. Please add each to the Notion Inbox and list them for me when you're done.

## Option C: export with Shortcuts

In the Shortcuts app, build a shortcut:

1. "Find Reminders" where "Is Completed" is off, from the list you want
2. "Get Name" from the input (or "Get Details of Reminders → Title")
3. "Combine Text" with "New Lines"
4. "Copy to Clipboard"

Run it, paste into the Claude chat, then follow step 2 of option B.

## After importing

Everything you imported is in the Inbox. Say "tidy up my board" and Claude will ask you, item by item with cards, which category each belongs to. If there are many, tidy up over a few rounds; each round asks about at most 4 items.
