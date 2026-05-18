# Categories

Each folder here is one part of your life. The archive skill picks the strongest one when it saves a chat.

| Folder | What goes here | Example trigger phrases |
| --- | --- | --- |
| `relationship/` | Spouse, partner, dating context, ongoing relationship patterns. | "my wife", "my partner", "my girlfriend", "my husband" |
| `work/` | Job, career, bosses, coworkers, clients, customers, workplace. | "my boss", "my client", "my job", "my coworker" |
| `people/` | Friends, neighbors, important people who don't fit relationship/family/work. | "my friend", "my neighbor" |
| `family/` | Parents, kids, siblings, extended family, household dynamics. | "my mom", "my dad", "my kid", "my sibling" |
| `health/` | Health, doctors, therapy, sleep, anxiety, medications, body patterns. | "my doctor", "my therapist", "anxiety", "sleep" |
| `travel/` | Trips, vacations, flights, hotels, place-based memories. | "my trip", "my vacation", "my flight" |
| `projects/` | Personal projects, apps, builds, creative work. | "my project", "my app", "my build" |
| `business/` | Companies, customers, products, monetization, launch plans. | "my business", "my company", "my product" |
| `ideas/` | Theories, prompts, mental models, future possibilities. | "my idea", "I've been thinking about" |
| `memories/` | Important life events, personal history, stories worth preserving. | "I'll never forget", "back when" |
| `inbox/` | Last-resort holding area when a note doesn't fit anywhere yet. | (used only when nothing else fits) |

## Each folder has an `_index.md`

The index file is a one-line list of the notes in that folder, with dates and short descriptions. The archive skill updates the index every time it saves into the folder.

You can read the index in seconds. ChatGPT reads it first when you say `Recall Context`, before opening individual notes.

## Adding a new category

If your life has a recurring pattern that doesn't fit, you can add a new category in your private memory repo:

1. Create a new folder, e.g. `categories/finance/`.
2. Add a `_index.md` to it (copy the shape of any existing one).
3. The next time you archive, mention the new category if needed:
   ```text
   Archive GitHub — save this to my finance category.
   ```

Don't go wild with new categories. Fewer, broader categories make recall easier.
