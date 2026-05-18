# Archive GitHub Skill

Command name: `Archive GitHub`

Aliases:

- `archive github`
- `archive this to github`
- `archive this chat`
- `save this to github`
- `save this chat to github`
- `write this down`
- `write this down to github`
- `save this memory`
- `archive this conversation`

Default private repo name:

`ai-you-memory`

## Purpose

When the user invokes this command, archive the current ChatGPT conversation as organized Markdown memory/context in the user's private AI You GitHub repo.

This is not brainstorming. This is not a proposal. This is not a generic summary. It is an archive execution task.

## Before Writing

1. Identify the user's private memory repo.
   - Default: `ai-you-memory`
   - If memory/custom instructions mention another repo, use that.
   - Never write personal notes to the public foundation repo `utb2017/ai-you`.
   - If the repo does not exist, use `https://github.com/utb2017/ai-you/generate` as the setup fallback and ask the user to create a private copy.
2. Read the private repo state:
   - `README.md`
   - `index.md`
   - `logs/import-log.md`
   - relevant `categories/*/_index.md`
   - any existing related notes
3. Search for related names, projects, dates, and topic keywords before creating duplicates.
4. Read the full current conversation.

## Category Choices

Use the strongest primary category:

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
- `inbox`

Use `inbox` only as a last resort.

If a chat has multiple major topics, create multiple notes. If a topic is minor, keep it in the strongest note and add tags/cross-links.

## Human-Life Triggers To Preserve

Pay attention to repeated or emotionally important references like:

- my wife / husband / partner
- my girlfriend / boyfriend / spouse
- my kid / child / daughter / son
- my mom / dad / parent / sibling
- my boss / coworker / client / customer
- my friend / neighbor
- my doctor / therapist / shrink
- my project / business / app
- vacation / trip / flight / hotel
- dentist / appointment / medication / sleep

## File Rules

Filename format:

`YYYY-MM-DD-short-topic-name.md`

Use the original chat date or best-known event date when available. If unknown, use today's date and mark uncertainty in the note.

Every note must use the frontmatter and sections from:

`templates/chat-summary-template.md`

## Privacy Rules

The user's memory repo should be private, but still redact dangerous information.

Do not include:

- passwords
- API keys
- auth tokens
- bank details
- SSNs
- private keys
- exact credentials
- exact phone numbers
- anything dangerous if leaked

Preserve useful context, not risky secrets.

## Index And Log Rules

After creating notes:

1. Update the relevant category `_index.md`.
2. Add a one-line description.
3. Update root `index.md` for major or recurring notes.
4. Update `logs/import-log.md`.
5. Verify the created/updated files exist.

## GitHub Write Behavior

Writing to GitHub is the primary path. Do not stop at a plan.

If GitHub asks the user to confirm file creation/update, trigger the confirmation modal and wait for the user to confirm.

Do not claim success unless the file exists after writing.

If write actions are not immediately visible:

1. Search/list/discover the GitHub connector/app action surface.
2. Look for actions named like:
   - create file
   - update file
   - repository contents
   - save file
   - commit file
   - create private GitHub file
   - create or update file contents
3. Use only actions that are actually exposed in the session.
4. Do not invent unlisted low-level routes.
5. If a route fails, try another exposed write route or branch/PR route if available.

If GitHub write is unavailable but file creation/download is available, create a downloadable archive packet containing the full note bodies and index/log updates.

If neither GitHub write nor file download is available, paste the complete archive packet inline.

The archive packet must include:

- every new Markdown file path
- every full Markdown file body
- exact category `_index.md` updates
- exact root `index.md` updates when needed
- exact `logs/import-log.md` rows
- suggested commit message

Correct write failure wording:

`This session did not expose a working GitHub write action. The archive packet is complete so the memory can still be saved.`

Do not say:

- `GitHub cannot write`
- `The repo cannot be updated`
- `The archive is impossible`

## Final Response

Keep it short:

- files created/updated
- categories used
- dates used
- commit/hash/verified paths if available
- any uncertainty

Do not end by asking the user what to do next.
