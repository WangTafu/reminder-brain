# Optional: import from Apple Reminders (English)

If your to-dos currently live in Reminders on your iPhone or Mac, you can move them into the Notion Inbox in one go and then tidy them up as usual.

After the move, we suggest **jotting new things straight into the Notion Inbox** rather than using both. Two lists drift apart quickly.

This is how the author moved over: one command on a Mac exports the whole Reminders database, and you hand it to Claude. **Every list, the order, sections, subtasks, notes and due dates all come along**, so nothing is missed and nothing gets reshuffled.

You need: a Mac signed in to the same Apple ID, and a Claude that can read files and run code to analyse them (for example a Claude app chat where you can upload files). If your iPhone syncs Reminders with iCloud, the Mac has the same data.

## Step 1: give Terminal permission

macOS protects Reminders data, so Terminal can't read it by default.

1. Open **System Settings → Privacy & Security → Full Disk Access**
2. Click **+** at the bottom left, choose **Terminal** under Applications → Utilities, and switch it on
3. **Quit Terminal fully with `Cmd + Q` and open it again.** The permission doesn't apply until you do; a window that says "Restored session" doesn't count

You can switch this permission off again after exporting.

## Step 2: run the export command

Paste this whole block into Terminal and press Return:

```bash
mkdir -p ~/Desktop/reminders_export && cd ~/Library/Group\ Containers/group.com.apple.reminders/Container_v1/Stores && for f in Data-*.sqlite; do sqlite3 "$f" ".backup '$HOME/Desktop/reminders_export/$f'"; done && cd ~/Desktop && zip -rq reminders_export.zip reminders_export && echo Done
```

When it prints `Done`, you'll find **`reminders_export.zip`** on your Desktop. That's the file to give Claude: one zip holding a few `Data-*.sqlite` files; your reminders are in the largest one.

The command only **copies** the data (using `sqlite3 .backup`, so it's fine if Reminders is open). It doesn't change your reminders.

**Troubleshooting:**

| Terminal shows | Why | What to do |
|---|---|---|
| `zsh: no matches found: Data-*.sqlite` | Terminal has no permission, so it can't see the files | Go back to step 1; make sure you added the permission and reopened Terminal with `Cmd + Q` |
| `Operation not permitted` when you type `ls` | Same | Same |
| The prompt changed from `~` to `Stores` | The command moved into the Reminders data folder; that's normal | Ignore it; type `cd ~` or reopen Terminal to go back |

## Step 3: give the zip to Claude

Upload `reminders_export.zip` to the project chat, then send:

> This is a backup of the Reminders database from my Mac (a Core Data SQLite store). Please use code to read every **unfinished** reminder:
> - Items are in `ZREMCDREMINDER` (`ZCOMPLETED=0`, `ZMARKEDFORDELETION=0`), lists in `ZREMCDBASELIST`, subtasks via `ZPARENTREMINDER`, sections in `ZREMCDBASESECTION`
> - List order is in `ZREMCDOBJECT.ZLISTIDSMERGEABLEORDERING_V2`; order within a list depends on `ZSORTINGSTYLE`: for manual order use `ZREMINDERIDSMERGEABLEORDERING_V2_JSON`, for creation date sort by `ZCREATIONDATE`
>
> First tell me how many items each list has. Then create a page "Reminders (original)" under the Action Board and write everything in exactly as it appears in the app, in the same list order and item order: one heading per list, a smaller heading per section, one checkbox per item, subtasks indented. Don't change a word.

## Step 4: check, then import into the Inbox

Compare the "Reminders (original)" page with Reminders on your phone or Mac: are the counts and order right? Once they are, say:

> Add each item from "Reminders (original)" to the Inbox. Copy titles as they are, put any notes in the page body, and put due dates in "Planned for".

Keep the original page as a reference you can check against any time.

**Privacy note:** this database holds **all** your reminders, including finished ones. Only send it to your own Claude, and delete the `reminders_export` folder and zip from your Desktop when you're done.

## After importing

Everything you imported is in the Inbox. Say "tidy up my board" and Claude will ask you, item by item with cards, which category each belongs to. If there are many, tidy up over a few rounds; each round asks about at most 4 items.
