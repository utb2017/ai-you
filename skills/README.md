# AI You Skills

Skills are short, command-style instructions ChatGPT reads from this repo. They tell ChatGPT exactly how to behave when you say a particular phrase.

## Core skills

| Skill | Command | What it does |
| --- | --- | --- |
| [`archive-github`](archive-github/SKILL.md) | `Archive GitHub` | Save the current chat into your private memory repo as structured Markdown. |
| [`recall-context`](recall-context/SKILL.md) | `Recall Context` | Pull relevant context from your private memory repo before ChatGPT answers. |

These two are the heart of AI You. Once setup is done, you only need these.

## Bonus skills

| Skill | Command | What it does |
| --- | --- | --- |
| [`text-my-person`](text-my-person/SKILL.md) | `Text my <person>` | Draft a message and build a tappable `sms:` link that opens your phone's Messages app with the recipient and body pre-filled. **You** still press Send. |

Bonus skills are optional. Install them only if you want them. Each one ships with its own setup prompt under [`prompts/`](../prompts/).

## Skill anatomy

Each skill folder has:

- `SKILL.md` — the full instructions ChatGPT should follow when the command runs.
- `README.md` — a short pointer to `SKILL.md` and the install prompt.
- `WEBGPT_MEMORY_INSTALL_PROMPT.md` — a short paste you can give ChatGPT to remember the command.

## Why this design

- **Two-command core (`Archive GitHub` + `Recall Context`)** is the entire promise. Save the chat, recall it later. That's the whole product.
- **Bonus skills are opt-in** so the main flow stays simple and the surface area for non-technical users stays small.
- **All skill files live in the public foundation**, so any chat in any session can read the latest version of the rules. Your private repo holds your data, not the rules.
