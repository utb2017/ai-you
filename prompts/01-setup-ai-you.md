# Prompt 1: Setup AI You

Paste this into ChatGPT after connecting GitHub.

```markdown
Set up AI You for me.

Use the GitHub connector/app.

Read the public foundation repo:
`utb2017/ai-you`

Public template URL:
`https://github.com/utb2017/ai-you/generate`

Then create a private GitHub repo in my account named:
`ai-you-memory`

Copy the foundation structure into that private repo:

- README.md
- index.md
- categories/
- skills/
- templates/
- logs/

Important:

- My private personal data must go only into my private repo, not into the public `utb2017/ai-you` repo.
- If `ai-you-memory` already exists, use it instead of creating a duplicate.
- If you cannot create the repo directly, tell me to open `https://github.com/utb2017/ai-you/generate`, create a private repo named `ai-you-memory`, then continue setup after I confirm.
- After the repo exists, read:
  - `skills/archive-github/SKILL.md`
  - `skills/recall-context/SKILL.md`
  - `prompts/02-archive-github.md`
  - `prompts/03-recall-context.md`

Please remember these commands if memory is available:

- `Archive GitHub` means save the important durable context from the current chat into my private `ai-you-memory` repo.
- `Recall Context` means read my private `ai-you-memory` repo and pull relevant context before answering.

Do not ask me to choose folders or filenames by default. Make the best reasonable decision, redact dangerous secrets, update indexes/logs, and verify GitHub writes when possible.
```
