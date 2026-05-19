# Prompts

These are the prompts you paste into ChatGPT.

## Core prompts

| Prompt | When to use it |
| --- | --- |
| [`01-setup-ai-you.md`](01-setup-ai-you.md) | Once, after connecting GitHub and creating your private `ai-you-memory` repo. Installs the two core commands and runs a smoke test. |
| [`02-archive-github.md`](02-archive-github.md) | At the end of an important conversation, to save the durable context. (Long form is here; the short command is just `Archive GitHub`.) |
| [`03-recall-context.md`](03-recall-context.md) | At the start of a chat about a recurring person, project, or topic. (Long form is here; the short command is just `Recall Context`.) |

## Bonus prompts

| Prompt | When to use it |
| --- | --- |
| [`04-install-text-my-person.md`](04-install-text-my-person.md) | Optional. Once, to install the `Text my <person>` skill and create your contacts placeholder. See [`docs/SMS_LINK_SKILL.md`](../docs/SMS_LINK_SKILL.md). |

## How prompts and skills relate

- A **skill** lives under `skills/`. It is what ChatGPT does when a command runs.
- A **prompt** lives under `prompts/`. It is what you paste into a chat to tell ChatGPT to install or run a skill.
- Once a skill is installed in ChatGPT memory, you usually don't need to paste the prompt again. You just say the command.

If a future ChatGPT session forgets a skill, paste the **long form** of the matching prompt and you'll be back in business.
