# Using ChatGPT

> ⚠️ The ChatGPT version hasn't been tested yet. This is written from what ChatGPT and Notion document publicly. If you try it, please share how it went in Issues.

You use the **same prompts** as with Claude, unchanged. You just need to know about the differences below.

## 1. First, check that ChatGPT can *write* to Notion

This is the key step. Tidying up means creating items, updating progress and deleting originals. **If ChatGPT can only read, it can only do half the job** (count things and make suggestions, but not archive or file anything).

- What you want to connect is **Notion MCP** (Notion's official connection), which can create pages, update properties, delete pages and change views. Notion's help page lists ChatGPT as a supported app.
- In ChatGPT this is usually under **Settings → Apps**. If you can't find a Notion connection that can write, you may need to turn on **developer mode** (Settings → Apps → Advanced settings) and add Notion MCP yourself.
- Which plans can do this changes over time; check OpenAI's and Notion's latest docs.

**How to check**: once connected, ask ChatGPT to "create a page called 'Test' in my Notion, then delete it". If it can, you're good to go; if not, it can only read.

## 2. Where the rules go

Paste everything between the two horizontal rules in `prompts/en/project-instructions.md` into a **ChatGPT project's instructions**, and say "tidy up my board" in that project from then on.

A custom GPT also works, but using Notion from a GPT is set up differently and is more work, so start with a project.

## 3. No choice cards

ChatGPT doesn't have Claude's tap-to-choose cards. The prompts already cover this: without cards, it numbers each item and lists A / B / C as text, and you reply like "1A 2C 3B".

## 4. Working notes

During setup, Claude keeps "working notes" in the project with the address of every table. ChatGPT can't write documents into a project, so it creates a page with the same name under the Notion Action Board instead (the prompts already say so).

## 5. Weekly reminder (optional)

ChatGPT has **scheduled tasks (Tasks)** that can notify your phone or send an email. Send it everything between the horizontal rules in `prompts/en/weekly-reminder.md` and ask it to create a task for Sundays.

- The free plan can create tasks too, but only with a rough time of day (e.g. afternoon).
- It's not confirmed whether a scheduled task can read Notion. That's fine: the prompt says that if reading fails, just send the reminder without the counts.

## 6. Everything else is the same

What Notion lets an assistant change, and what you have to click yourself, is the same as with Claude (see [`notion-limits.md`](notion-limits.md)). You still set the progress bar and the default template in Notion yourself.
