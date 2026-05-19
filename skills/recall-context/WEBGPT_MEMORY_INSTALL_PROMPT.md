# WebGPT Memory Install Prompt — Recall Context

Paste this once if you want ChatGPT to remember the `Recall Context` command across future chats. The setup prompt (Prompt 1) already includes this, so most users won't need it separately.

```markdown
Please remember this as a durable AI You command:

Command: `Recall Context`

When I say `Recall Context`, `pull context`, `check my memory`, `check GitHub memory`, `look up my relationship`, `pull my relationship data`, `pull my work context`, or `before you answer, check my GitHub`, retrieve relevant context from my private AI You memory repo before answering.

Default private repo name:
`ai-you-memory`

Before retrieving, read this skill file from the public foundation:
`utb2017/ai-you/skills/recall-context/SKILL.md`

Operating rules:

- This is a retrieval task, not an archive task.
- Do not ask me to re-explain background that is already in the repo.
- Search by category, names, projects, and recent imports.
- Pull only the relevant context, not the whole repo.
- Open your reply with a short proof-of-retrieval line, then answer with continuity instead of resetting.
- Never read or write my personal notes from the public foundation repo `utb2017/ai-you`.

Output budget:

- Retrieval is preparation, the response is the deliverable.
- Keep the retrieval summary to 3 to 5 bullets, maximum 8 lines.
- Spend the rest of the reply on the actual response with depth.
- If I am venting or processing, the response is a human reply, not a bullet list. Reflect what is happening first, then offer practical next steps at the end.
- Prefer cutting retrieval bullets over cutting response depth. Never short-change the response by over-spending on retrieval.

If memory is available in this session, save this command.
```
