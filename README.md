# AI You

Give ChatGPT a memory it can actually come back to.

AI You is a simple GitHub-based memory system for ChatGPT. It gives you a private repo where important conversations can be saved as organized Markdown notes, then recalled later when you need context.

This public repo is the starter foundation. It contains only instructions, prompts, skills, categories, and templates. Your personal memory should live in your own private copy.

## What You Get

- A private GitHub archive for your important ChatGPT context.
- A simple save command: `Archive GitHub`.
- A simple recall command: `Recall Context`.
- Folders for relationship, work, people, family, health, travel, projects, business, ideas, memories, and inbox.
- Structured Markdown summaries instead of messy transcript dumps.

## Before You Start

1. Create or log in to a GitHub account: [github.com/join](https://github.com/join)
2. Open ChatGPT and connect GitHub using the GitHub connector.
   - OpenAI GitHub connector help: [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
   - Connector overview: [Connectors in ChatGPT](https://help.openai.com/en/articles/11487775/)
3. Give ChatGPT access to the private repo it creates for you.

Model note: in testing, regular `5.5 extended thinking` exposed the needed GitHub and memory tools more reliably than Pro for this workflow. If the GitHub tools do not appear, switch model/surface before assuming the setup is broken.

## The Three Prompts

### Prompt 1: Setup AI You

Use this once.

Open ChatGPT, make sure the GitHub connector is available, then paste:

```markdown
Set up AI You for me.

Use the GitHub connector/app.

Read the public foundation repo:
`utb2017/ai-you`

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
- If you cannot create the repo directly, tell me to click "Use this template" or fork/copy the public repo into a private repo, then continue setup after I confirm.
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

### Prompt 2: Archive This Chat

Use this at the end of an important conversation.

```markdown
Archive GitHub
```

ChatGPT should read `skills/archive-github/SKILL.md` from your private repo and save the durable context into the right folder.

### Prompt 3: Recall Context

Use this before asking about a recurring person, project, problem, relationship, work topic, health pattern, or trip.

```markdown
Recall Context

Pull the relevant context from my GitHub memory before you answer.
```

You can also be specific:

```markdown
Recall Context

Pull my relationship context before you answer.
```

or:

```markdown
Recall Context

Pull my work/project context before you answer.
```

## How It Works

`Archive GitHub` saves context.

`Recall Context` retrieves context.

The archive skill decides where a note belongs. For example:

- "my wife", "my partner", "relationship" -> `categories/relationship/`
- "my boss", "work", "client" -> `categories/work/`
- "my doctor", "anxiety", "sleep" -> `categories/health/`
- "vacation", "trip", "flight" -> `categories/travel/`
- "new app", "business idea", "project" -> `categories/projects/` or `categories/business/`

The recall skill searches your indexes and notes before answering, so ChatGPT can respond with continuity instead of starting over.

## Privacy Rules

Your personal repo should be private.

Do not store:

- passwords
- API keys
- auth tokens
- bank details
- SSNs
- private keys
- exact credentials
- exact phone numbers
- anything dangerous if leaked

AI You is designed to preserve meaning, not secrets.

## About GitHub Confirmations

ChatGPT may ask you to confirm GitHub file writes. That is normal safety behavior. The goal is to keep the workflow simple, but some confirmations may be unavoidable when writing private files.

## Public vs Private

This repo:

`utb2017/ai-you`

is public and contains only the foundation.

Your private repo:

`ai-you-memory`

is where your personal notes should go.

Never put personal memory notes in the public foundation repo.

## Repo Structure

```text
ai-you/
  README.md
  index.md
  categories/
  skills/
  templates/
  prompts/
  logs/
```

## License

MIT

