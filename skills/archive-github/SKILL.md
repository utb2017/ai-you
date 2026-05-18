# Archive GitHub Skill

Command name: `Archive GitHub`

Aliases:

- `archive github`
- `archive this to github`
- `archive this chat`
- `archive this conversation`
- `save this to github`
- `save this chat to github`
- `save this memory`
- `write this down`
- `write this down to github`

Default private repo name:

`ai-you-memory`

## Purpose

When the user invokes this command, archive the current ChatGPT conversation as organized Markdown context inside the user's private AI You GitHub repo.

This is **not** brainstorming. This is **not** a proposal. This is **not** a generic summary. It is an archive **execution** task.

The user's expectation: their durable context is in their repo when this command finishes.

## Before writing anything

1. Identify the user's private memory repo.
   - Default: `ai-you-memory`.
   - If the user's memory or custom instructions name a different repo, use that.
   - **Never** write personal notes to the public foundation repo `utb2017/ai-you`.
   - If the private repo does not exist, tell the user to open `https://github.com/utb2017/ai-you/generate`, create a private repo named `ai-you-memory`, and rerun.
2. Read the private repo state:
   - `README.md`
   - `index.md`
   - `logs/import-log.md`
   - relevant `categories/<category>/_index.md`
   - any existing notes that look related (same names, same project, same date range)
3. Search before creating duplicates. If the chat is a continuation of an earlier note, prefer updating or cross-linking that note.
4. Read the **full** current conversation, not just the last message.

## Choosing a category

Use the strongest single primary category from this list:

- `relationship`
- `work`
- `people`
- `family`
- `health`
- `travel`
- `projects`
- `business`
- `ideas`
- `memories`
- `inbox` (last resort only)

Disambiguation:

- A spouse / partner / dating context goes in `relationship`, not `people`.
- A boss / coworker / client / customer goes in `work`, not `people`.
- A parent / sibling / child goes in `family`.
- A friend / neighbor / acquaintance goes in `people`.
- A doctor / therapist / medication / sleep / mental-health pattern goes in `health`.
- A trip / flight / hotel / location goes in `travel`.
- A personal app / build / creative project goes in `projects`.
- A revenue-bearing or company-shaped idea goes in `business`.
- A theory, prompt, or speculative idea goes in `ideas`.
- A personal memory or life event goes in `memories`.

If a chat has multiple major topics, create multiple notes. If a topic is minor, keep it in the strongest note and add tags or cross-links instead of fragmenting.

## Human-life triggers worth preserving

Pay attention to repeated, named, or emotionally weighted references like:

- `my wife`, `my husband`, `my partner`, `my girlfriend`, `my boyfriend`, `my spouse`
- `my kid`, `my child`, `my daughter`, `my son`
- `my mom`, `my dad`, `my parent`, `my sibling`
- `my boss`, `my coworker`, `my client`, `my customer`, `my employee`
- `my friend`, `my neighbor`
- `my doctor`, `my therapist`, `my shrink`
- `my project`, `my business`, `my app`, `my company`
- `my trip`, `my vacation`, `my flight`, `my hotel`
- `dentist`, `appointment`, `medication`, `sleep`
- recurring proper nouns (names, project names, places) that show up more than twice in the chat

## File rules

Filename format inside `categories/<category>/`:

`YYYY-MM-DD-short-topic-name.md`

- Use the date the conversation actually happened. If unknown, use today's date and mark uncertainty in the note's `confidence` frontmatter field.
- Keep the topic short, hyphenated, lowercase, no spaces, no special characters.

Every note should use the structure from `templates/chat-summary-template.md`:

- frontmatter (title, source, dates, category, tags, people, projects, confidence, privacy_level)
- `# Summary`
- `# Important Details`
- `# People / Entities`
- `# Decisions`
- `# Emotional Context`
- `# Projects / Tasks`
- `# Follow-Ups`
- `# Cross-Links`
- `# Raw Notes To Preserve`

For person-focused notes, also reference `templates/person-note-template.md`. For project-focused notes, also reference `templates/project-note-template.md`. For relationship-focused notes, also reference `templates/relationship-note-template.md`.

## Privacy rules

The user's repo should be private, but **redact dangerous information anyway**. Do not include:

- passwords
- API keys
- auth tokens
- bank account numbers, card numbers, CVVs
- SSNs / national IDs
- private keys
- exact credentials of any kind
- exact phone numbers (a city/country area code is fine if relevant)
- home address details specific enough to locate the user
- anything dangerous if leaked

Preserve **meaning**, not secrets. If the chat reveals a password or key, write `[redacted]` and continue.

## Index and log rules

After creating the note(s):

1. Update the relevant `categories/<category>/_index.md` with a one-line entry that includes the date and a short description.
2. If the topic is recurring or major, also update root `index.md` under `Recent Imports`.
3. Update `logs/import-log.md` with a row describing the import.
4. Read each updated file back from GitHub to verify it persisted.

## GitHub write behavior

Writing to GitHub is the primary path. Do not stop at a plan.

If GitHub asks the user to confirm a file create / update, **trigger the confirmation modal** and wait for the user to press Confirm. Do not turn that into a chat question.

Do not claim success unless the file exists in the repo after writing.

If write actions are not immediately visible in this session:

1. Search / list / discover the GitHub connector or app actions.
2. Look for actions named like:
   - create file
   - update file
   - repository contents
   - save file
   - commit file
   - create private GitHub file
   - create or update file contents
3. Use only actions that are actually exposed in this session.
4. Do not invent low-level routes (for example, do not guess `/GitHub/link_xxx/create_file` style routes that are not in your action list).
5. If a route fails, try another exposed write route, or a branch / pull request route if available.

## Reducing confirmation fatigue

To minimize how many confirmation pop-ups the user sees:

- Default order: write the main note file first, then the category `_index.md`, then `logs/import-log.md`.
- Skip the root `index.md` update for minor archives. Only touch the root index for recurring or major topics.
- If the user explicitly says `Archive GitHub — single packet mode`, write **one** combined Markdown file at `logs/relay-packets/YYYY-MM-DD-HHMM-archive-packet.md` containing the full note body and the index / log updates the user can apply later. That collapses the archive into one write.

## When GitHub write is unavailable: relay packet

If, after honest discovery, the session truly cannot reach a GitHub write action, do **not** lose the user's archive. Produce a complete `LOCAL ARCHIVE RELAY PACKET` so the user can paste it into their repo manually or in another session.

The packet must include, in this order:

1. A short header naming the destination repo (`ai-you-memory`) and the reason for falling back (no exposed write action in this session).
2. Every new Markdown file path and the **full file body** of each file.
3. The exact `categories/<category>/_index.md` update (line to add).
4. The exact root `index.md` update if applicable.
5. The exact `logs/import-log.md` row to add.
6. A suggested commit message.

Use the file body (with the relay packet inside) as a downloadable Markdown attachment when possible. If no download is available, paste the relay packet inline.

Correct fallback wording:

> This session did not expose a GitHub write action. Below is the relay packet so the memory is not lost.

Incorrect wording (do not say any of these):

- `GitHub cannot write.`
- `The repo cannot be updated.`
- `The archive is impossible.`

## Final response shape

After archiving (or producing the relay packet), the final reply should be short:

- files created or updated (with paths)
- categories used
- dates used
- whether GitHub writes were verified
- any uncertainty (for example, "date is approximate")

Do not end by asking the user what to do next. The archive is the closer.
