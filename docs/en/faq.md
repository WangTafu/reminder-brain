# FAQ (English)

### Is this an app? What do I install?

Nothing. It's a set of rules written for Claude plus a few tables in Notion. Claude follows the rules to read and write your Notion and tidy up your to-dos. The repo is all text files, no code.

### Does it cost anything?

The Notion free plan is enough. On the Claude side you need an account with Projects and the Notion connector. The weekly reminder needs scheduled tasks, which not every Claude environment has; without them, skip it. Saying "tidy up my board" works the same.

### Will Claude delete my stuff?

- For ticked items, Claude first copies them into a Log and the Archive, and only after both copies exist does it move the original to the trash. Notion keeps trashed pages for 30 days.
- For unfinished items, Claude asks you about each one with a card. If you don't pick, it doesn't touch it.
- Logs and the Archive are add-only.
- The weekly reminder is read-only and changes nothing.

### Why tidy up "manually" instead of fully automatically?

Categorising needs your judgement: one person files "buy running shoes" under Health, another under Shopping. A fully automatic system gets this wrong in ways that are hard to notice. So Claude suggests and you confirm with a tap. Tidying a week's to-dos usually takes a few minutes.

If you'd rather trust Claude's judgement, you can make it fully automatic; see `customize.md`.

### How should I fill in progress?

| Situation | What you do |
|---|---|
| A small thing with no steps | Tick "Done" when it's done, nothing else |
| 1–3 steps | Write checkboxes in the body and tick them as you go; leave Progress empty and Claude works it out during a tidy-up |
| You want to estimate yourself | Type a number in "Progress", e.g. 30. Claude won't overwrite it |
| All done | Tick "Done" |

### I want the Chinese version

Send Claude the files in `prompts/zh/` instead of the English ones. Table names, property names and Claude's replies will be in Chinese.

### Can I repurpose it?

Yes. It's MIT licensed: change it, share it, use it commercially. A reading list, a project board, a household chore chart are all just different categories and rules.
