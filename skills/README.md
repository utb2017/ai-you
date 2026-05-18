# AI You Skills

Skills are short, command-style instructions ChatGPT reads from this repo. They tell ChatGPT exactly how to behave when you say a particular phrase.

AI You ships with two skills.

## Core skills

| Skill | Command | What it does |
| --- | --- | --- |
| [`archive-github`](archive-github/SKILL.md) | `Archive GitHub` | Save the current chat into your private memory repo as structured Markdown. |
| [`recall-context`](recall-context/SKILL.md) | `Recall Context` | Pull relevant context from your private memory repo before ChatGPT answers. |

Each skill folder has:

- `SKILL.md` — the full instructions ChatGPT should follow.
- `README.md` — a short pointer to `SKILL.md` and the install prompt.
- `WEBGPT_MEMORY_INSTALL_PROMPT.md` — a short paste you can give ChatGPT to remember the command.

## Why two commands

- **`Archive GitHub`** is the closer. You use it at the end of an important conversation. Think of it like saving the file before you close the tab.
- **`Recall Context`** is the opener. You use it when starting a new conversation about a recurring person or topic. It tells ChatGPT to read your repo and answer with continuity.

These two phrases are the entire user surface. Once setup is done, you won't need to think about prompts again — you just say the command.
