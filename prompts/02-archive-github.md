# Prompt 2 — Archive GitHub

Use this at the **end** of an important conversation, when you want the durable context preserved.

## Short form

If setup worked and ChatGPT remembers the command, this is enough:

```text
Archive GitHub
```

## Long form (if ChatGPT seems to have forgotten the skill)

Paste this if the short form does not produce a saved file in your private repo:

````markdown
Archive GitHub

Save the important durable context from this chat into my private AI You memory repo (`ai-you-memory`).

Use the archive-github skill from the public foundation:
`utb2017/ai-you/skills/archive-github/SKILL.md`

Rules:

- This is an archive execution task, not brainstorming or proposal-only output.
- Do not write personal notes to the public `utb2017/ai-you` repo. Personal notes go only in my private `ai-you-memory` repo.
- Choose the strongest category folder (relationship, work, people, family, health, travel, projects, business, ideas, memories, or inbox as last resort).
- Use a filename like `YYYY-MM-DD-short-topic-name.md`.
- Use the `templates/chat-summary-template.md` shape: frontmatter, summary, important details, people, decisions, emotional context, projects/tasks, follow-ups, cross-links, raw notes to preserve.
- Update the relevant `categories/<category>/_index.md` with a one-line entry.
- Update root `index.md` if this is a major or recurring topic.
- Update `logs/import-log.md` with a row for this archive.
- Redact dangerous secrets (passwords, API keys, exact credentials, SSNs, exact phone numbers, anything dangerous if leaked).
- Verify the new file exists by reading it back from GitHub.

If GitHub write actions are not visible in this session:

- Search / list / discover the GitHub connector or app actions before giving up.
- Look for actions named like: create file, update file, repository contents, save file, commit file, create private GitHub file, or create-or-update-file-contents.
- Do not invent low-level routes that are not exposed.

If this session still cannot write to GitHub, do NOT lose the archive. Produce a complete `LOCAL ARCHIVE RELAY PACKET` so I can copy it into my repo by hand or in another session. The packet must include:

- every full Markdown file body, with the exact path it should be saved to,
- the exact `_index.md` updates,
- the exact `logs/import-log.md` row,
- a suggested commit message.

Tell me clearly: "This session did not expose a GitHub write action. Below is the relay packet so the memory is not lost." Do NOT say GitHub is broken or the repo cannot be updated.

End by listing, in 5 lines or less:

- the files you saved (or staged in the relay packet),
- the categories used,
- the dates used,
- whether you verified the writes.
````

## Reducing confirmation fatigue

ChatGPT's GitHub connector may pop a confirmation modal for each file. To minimize clicks while still keeping the archive useful, the archive skill is told to:

1. Write the main note file first (one confirmation).
2. Then update the category `_index.md` (second confirmation).
3. Then update `logs/import-log.md` (third confirmation).
4. Skip the root `index.md` update for minor archives, only update it for recurring or major topics.

If you ever feel the modal is firing too often, you can ask:

```text
Archive GitHub — single packet mode

Write everything as one combined Markdown file in my private repo at
`logs/relay-packets/YYYY-MM-DD-HHMM-archive-packet.md`,
including the full note body and the index/log updates I should apply.
I will reconcile the indexes and logs later.
```

That collapses the archive into one write, with one confirmation, at the cost of needing a small follow-up step later.
