# Make it your own (English)

All the rules are written in plain text, with no code, so changing the system means changing text. Here are the common changes.

After changing any rule, keep these three places in sync (Claude will remind you):
1. **Project instructions**: Claude can't edit these. It gives you the updated text and you paste it in.
2. **Working notes** (a document in the project): Claude updates these itself.
3. **Weekly reminder** (scheduled task): Claude updates it itself. It doesn't read the project instructions, so it needs its own update.

## Rename, add or remove categories

Just tell Claude, for example:

> Rename "Learning" to "Growth", and add a category "Family" with groups "Kids · Parents · Chores".

Claude will:
- Rename tables in Notion, or create a new to-do table and Log table
- Update the "Category" options in the Archive
- Give you the updated "Categories" section to paste into the project instructions
- Update the view addresses in the working notes and the weekly reminder

When removing a category, Claude first asks where its unfinished items should go.

## Change groups

> Add a group "Pets" under "Life", and merge "Fun" and "Hobbies" into "Interests".

Claude edits the select options. When merging, it moves items from the old groups to the new one before deleting the old options.

## Change the star rating

The star rating is just a set of judgement rules for Claude. Edit the "Star rating" section of the project instructions. You can also drop stars entirely: delete that section and ask Claude to remove the "Importance" property.

## Change or turn off the reminder

> Move the weekly reminder to Friday at 8 pm.
> I don't want the weekly reminder any more.

## Change the tidy-up flow

A few common changes:
- **Stop asking about every item**: "Change step 3: Claude files each item under its suggested category and shows me the list afterwards; I'll say if any are wrong."
- **Ask about more items at once**: choice cards hold at most 4 items; that's an interface limit. With more items Claude asks in several rounds.
- **No Archive**: "Drop the Archive, just use the Logs." Then delete that table.

## Change the table structure

Claude can add properties, rename properties and add views. It can't change how a property is displayed (bar, ring), templates or page layouts; you click those in Notion. See `notion-limits.md`.

## Switch language

To use Chinese instead, send Claude the files in `prompts/zh/` instead of the English ones. Table names, property names and Claude's replies will be in Chinese.
