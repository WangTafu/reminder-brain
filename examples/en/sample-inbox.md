# Example: a week's Inbox (English)

> Everything below is made up. It shows what typically goes in the Inbox and how to write steps in the page body.

## The Inbox

| Done | Item | Progress | Importance |
|---|---|---|---|
| ☐ | Renew passport, expires end of June | | ★★★ |
| ☐ | Set up a home NAS for photos | | ★☆☆ |
| ☐ | Finish chapter 3 of Atomic Habits | 30 | ★★☆ |
| ☐ | Reply to landlord about a time to fix the water heater | | ★★☆ |
| ☐ | Buy cat food | | ☆☆☆ |
| ☑ | Book a dental cleaning | | ★★☆ |
| ☑ | Switch the quarterly report charts to bar charts | | ★★☆ |

## What an item with steps looks like

**"Set up a home NAS for photos"**, opened, has this body:

- [x] Pick drives and order them
- [ ] Install the OS and set up a shared folder
- [ ] Turn on automatic photo backup from my phone

"Progress" is empty. During a tidy-up Claude counts 1 of 3 steps ticked, fills Progress with 33, treats it as "in progress" and leaves it in the Inbox.

**"Finish chapter 3 of Atomic Habits"** has an empty body (just the template's one empty checkbox), but you typed 30 into "Progress" yourself. Claude doesn't overwrite your number; this one is also "in progress" and stays in the Inbox.

## Items without steps

Things like "Buy cat food" and "Book a dental cleaning" have nothing in the body. Tick "Done" when they're done. The template's empty checkbox can just sit there; Claude doesn't count it as a step.
