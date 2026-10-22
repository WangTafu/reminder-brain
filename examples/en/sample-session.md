# Example: one "tidy up my board" session (English)

> A made-up conversation that continues from the Inbox in `sample-inbox.md`. It shows what Claude does and asks during a tidy-up.

---

**You**: tidy up my board

**Claude**: Starting the tidy-up: archiving ticked items first, then working out progress, then asking you with cards where the rest should go.

*(Claude reads each table's "🤖 To archive" view and the Inbox "🤖 To sort" view, and reads the body of each unfinished Inbox item)*

**Claude**: The 2 ticked items are archived and progress is worked out. 3 items need you to pick a category:

> **Card 1 · Renew passport, expires end of June**
> - **A · Life · Admin & Money ★★★** (suggested): a document with a deadline; delay could hold up travel
> - **B · Life · Travel ★★☆**: if it's only for a specific trip
> - **C · Keep in Inbox**
>
> **Card 2 · Reply to landlord about a time to fix the water heater**
> - **A · Life · Admin & Money ★★☆** (suggested): a rental matter
> - **B · Life · Health ★★☆**: no hot water affects daily life
> - **C · Keep in Inbox**
>
> **Card 3 · Buy cat food**
> - **A · Life · Shopping ☆☆☆** (suggested): an ordinary purchase
> - **B · Life · Hobbies ★☆☆**: if you track your cat as a hobby
> - **C · Keep in Inbox**

**You**: *(picks)* 1 → A, 2 → C, 3 → A

**Claude**: Done. Here's the tidy-up:

**Archived 2**
- Book a dental cleaning → Life · Log, Archive "Life · Health"
- Switch the quarterly report charts to bar charts → Work · Log, Archive "Work · Projects"

**Progress worked out**
- Set up a home NAS for photos: 1 of 3 steps → 33

**Categorised 2**
- Renew passport, expires end of June → Life · Admin & Money · ★★★
- Buy cat food → Life · Shopping · ☆☆☆

**Left in the Inbox: 3**
- Set up a home NAS for photos: in progress (33)
- Finish chapter 3 of Atomic Habits: in progress (your 30)
- Reply to landlord: you chose to keep it

**Sorts**: the Inbox and all three category tables still sort by "Done" ascending + "Created" descending. No changes needed.

---

## What Notion looks like afterwards

- **Inbox**: only the 3 unfinished items
- **Life**: now has "Renew passport" and "Buy cat food"
- **Life · Log**, **Work · Log**: one new entry each
- **Archive**: 2 new entries, categorised "Life · Health" and "Work · Projects"
