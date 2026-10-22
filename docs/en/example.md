# Example: one tidy-up

> A made-up example. Read it and you'll know what "tidy up my board" does.

## Before

The Inbox has 4 items:

| Item | Done | Steps in body | Progress |
|---|---|---|---|
| Book a dental cleaning | ✅ | | |
| Set up a home NAS | | 3 steps, 1 ticked | empty |
| Renew passport, expires end of June | | | |
| Buy cat food | | | |

## You say "tidy up my board", Claude does four things

**1. Archive (automatic)**
"Book a dental cleaning" is ticked → copied into the Life Log and the Archive (category "Life · Health"), and the original is removed from the Inbox.

**2. Progress (automatic)**
"Set up a home NAS" has 1 of 3 steps ticked → progress set to 33, and it stays in the Inbox.

**3. Ask you where things go**
The other two haven't started. Claude shows one card for each, for example:

> **Renew passport, expires end of June**
> - A · Life · Admin & Money ★★★ (recommended): has a deadline
> - B · Life · Travel ★★☆: if it's for a specific trip
> - C · Keep in Inbox

You pick: passport → A, cat food → C.

**4. Wrap up**
Claude checks the sorting hasn't changed, then gives you a summary: what was archived, what progress was set, what was filed, and what stayed in the Inbox.

## After

- **Inbox**: "Set up a home NAS" (33) and "Buy cat food"
- **Life**: now has "Renew passport" ★★★
- **Life Log** and **Archive**: each gained "Book a dental cleaning"
