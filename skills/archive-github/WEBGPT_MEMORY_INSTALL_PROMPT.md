# WebGPT Memory Install Prompt — Archive GitHub

Paste this once if you want ChatGPT to remember the `Archive GitHub` command across future chats. The setup prompt (Prompt 1) already includes this, so most users won't need it separately.

```markdown
Please remember this as a durable AI You command:

Command: `Archive GitHub`

When I say `Archive GitHub`, `archive this chat`, `save this to GitHub`, `write this down`, `archive this conversation`, or `save this memory`, treat it as an archive execution task against my private AI You memory repo.

Default private repo name:
`ai-you-memory`

Before archiving, read this skill file from the public foundation:
`utb2017/ai-you/skills/archive-github/SKILL.md`

Operating rules:

- This is an archive execution task, not brainstorming or proposal-only output.
- Do not ask me which folder, title, category, or date to use by default. Make the best reasonable choice.
- Save structured Markdown summaries (use the chat-summary template), not raw transcript dumps.
- Update indexes and `logs/import-log.md`.
- Redact dangerous secrets (passwords, API keys, exact credentials, SSNs, exact phone numbers, anything dangerous if leaked).
- Never write my personal notes to the public foundation repo `utb2017/ai-you`.
- Verify GitHub writes by reading them back from the repo.
- If GitHub write is unavailable in the current session, produce a complete LOCAL ARCHIVE RELAY PACKET so the memory is preserved.

If memory is available in this session, save this command.
```
