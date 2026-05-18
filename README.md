# AI You

**ChatGPT forgets. GitHub remembers. AI You shows ChatGPT where to look.**

AI You is a free, public template that turns a private GitHub repo into long-term memory for your ChatGPT conversations. You save the parts of a chat that matter, then pull that context back into any future chat with one short command.

This repo is the public foundation. It contains only instructions, prompts, skills, categories, and templates. Your personal notes belong in your own private copy. Nothing in here is anyone's personal data.

> Public foundation: [`utb2017/ai-you`](https://github.com/utb2017/ai-you)
>
> Create your private copy: [Use this template](https://github.com/utb2017/ai-you/generate)

---

## Why this exists

If you use ChatGPT a lot, you already know the problem.

- You explain your relationship for the tenth time.
- You re-describe your job, your project, your symptoms, your trip.
- A great conversation ends and the context is gone.
- A new chat means starting over.

ChatGPT's built-in memory is small and quiet. AI You gives ChatGPT a real notebook it can read and write to: a private GitHub repo, organized in plain Markdown, that you control.

You don't have to learn GitHub. You don't have to write code. You install two commands and use them like punctuation:

- Say **`Archive GitHub`** at the end of an important chat to save it.
- Say **`Recall Context`** at the start of the next chat to bring it back.

That's the whole product.

---

## Who this is for

- ChatGPT users on the web or phone who keep losing context.
- People in long relationships, jobs, projects, or treatment plans who hate repeating themselves.
- Anyone who wishes ChatGPT remembered them across chats without joining a new app.
- Builders who want a portable, exportable, file-based memory they can read in a text editor.

You do not need to be a developer. If you can copy and paste, you can use AI You.

---

## What you get

- A private GitHub repo (yours, not ours) to store your important context.
- Two commands: **`Archive GitHub`** and **`Recall Context`**.
- A folder system: relationship, work, people, family, health, travel, projects, business, ideas, memories, inbox.
- Three short setup prompts you copy and paste.
- A "smoke test" step that proves the setup actually works before you trust it.
- Markdown files you can read, edit, back up, or delete at any time. No vendor lock-in.

---

## Cost

**Free.** AI You is a public template, not a paid service. The only paid thing in the loop is your normal ChatGPT subscription, and even that is optional if you have ChatGPT free with the GitHub connector available to you.

We do not see, store, or process anything you save. Your memory lives in your GitHub account, on your computer if you clone it, and nowhere else.

---

## Quickstart in 5 steps

This is the whole flow. Most people finish in under 10 minutes.

### 1. Make sure you have a GitHub account

If you don't have one, sign up at [github.com/join](https://github.com/join). It is free.

### 2. Connect GitHub to ChatGPT

In ChatGPT, open the connectors / apps panel and connect GitHub. OpenAI's help docs:

- [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
- [Connectors in ChatGPT](https://help.openai.com/en/articles/11487775)

You will be asked which repos ChatGPT can read and write. You can grant access to all of your repos or only the one we are about to create.

### 3. Create your private memory repo from this template

Click [Use this template](https://github.com/utb2017/ai-you/generate). Name your new repo:

```
ai-you-memory
```

Set it to **Private**. That repo is now yours. It already has the folder structure, the skills, the prompts, and the templates. You will write your own notes into it.

### 4. Run the setup prompt in ChatGPT

Open a fresh ChatGPT chat. Paste **Prompt 1** (in [`prompts/01-setup-ai-you.md`](prompts/01-setup-ai-you.md), and reproduced below). ChatGPT will:

- read this public repo,
- confirm your private `ai-you-memory` repo exists and is reachable,
- read the two skill files so it knows how `Archive GitHub` and `Recall Context` work,
- run a tiny **smoke test**: it creates one small file in `logs/smoke-tests/` and reads it back, just to prove writing actually works,
- ask you to remember the two commands.

Setup is not done until the smoke-test file is created and read back from your private repo.

### 5. Use the two commands

- At the end of a meaningful chat, say:

  ```text
  Archive GitHub
  ```

- At the start of a new chat about the same person, project, or topic, say:

  ```text
  Recall Context
  ```

That's it. You're using AI You.

---

## The three prompts

You copy each of these from the [`prompts/`](prompts/) folder, or from below.

### Prompt 1 — Setup AI You (run once)

Paste this into ChatGPT after connecting GitHub:

````markdown
Set up AI You for me.

Use the GitHub connector / app.

Read the public foundation repo:
`utb2017/ai-you`

I have already created my private memory repo from the public template at:
`https://github.com/utb2017/ai-you/generate`

Default private repo name:
`ai-you-memory`

If `ai-you-memory` does not exist yet, tell me to open the template link, create a private copy named `ai-you-memory`, and rerun this prompt after I confirm.

Once my private repo exists:

1. Read the two skill files from the public foundation repo:
   - `skills/archive-github/SKILL.md`
   - `skills/recall-context/SKILL.md`
2. Read the two prompt files from the public foundation repo:
   - `prompts/02-archive-github.md`
   - `prompts/03-recall-context.md`
3. Run a GitHub write smoke test in my private repo:
   - Create one file in `logs/smoke-tests/`.
   - Filename format: `YYYY-MM-DD-HHMM-github-write-smoke-test.md`.
   - File body: `AI You GitHub write contact established.`
   - Read the file back from GitHub after writing it.
   - If GitHub asks me to confirm the write, trigger the confirmation modal and wait for me to press Confirm.
   - Do NOT archive any personal content during setup. Only create the smoke-test file.

If memory is available in this ChatGPT session, please remember these two durable commands:

- `Archive GitHub` means save the durable context from the current chat into my private `ai-you-memory` repo using the archive-github skill.
- `Recall Context` means read my private `ai-you-memory` repo and pull the relevant context before answering, using the recall-context skill.

Rules:

- My personal notes go only in my private `ai-you-memory` repo, never in the public `utb2017/ai-you` repo.
- Do not ask me to choose folders, filenames, or categories by default. Make the best reasonable choice.
- Redact dangerous secrets (passwords, API keys, exact credentials, SSNs, etc.).
- Update indexes and logs when archiving.
- Verify GitHub writes by reading back what was written.

If GitHub write actions are not visible in this session:

- First, search/list/discover the GitHub connector or app actions before giving up.
- Look for actions named like: create file, update file, repository contents, save file, commit file, create private GitHub file, or create-or-update-file-contents.
- Do not invent low-level routes that are not exposed.
- If this model surface still cannot write, tell me clearly: "This session does not expose a GitHub write action. Switch to a different ChatGPT model and rerun this setup prompt." Do NOT claim the repo or GitHub is broken.
````

### Prompt 2 — Archive this chat (use at the end of important chats)

```text
Archive GitHub
```

That short command should be enough once setup is done. The longer version, in case ChatGPT loses the skill, is in [`prompts/02-archive-github.md`](prompts/02-archive-github.md).

### Prompt 3 — Recall context (use before asking about recurring people/topics)

```text
Recall Context
```

You can be more specific:

```text
Recall Context

Pull my relationship context before you answer.
```

```text
Recall Context

Pull my work / project context before you answer.
```

The longer version is in [`prompts/03-recall-context.md`](prompts/03-recall-context.md).

---

## How it decides where things go

When you say `Archive GitHub`, the archive skill picks the strongest category and creates a structured Markdown note. Examples:

| You said something like…           | It saves to              |
| ---------------------------------- | ------------------------ |
| "my wife", "my partner"            | `categories/relationship/` |
| "my boss", "my client", "my job"   | `categories/work/`         |
| "my doctor", "anxiety", "sleep"    | `categories/health/`       |
| "vacation", "trip", "flight"       | `categories/travel/`       |
| "my app", "my business idea"       | `categories/projects/` or `categories/business/` |
| "my mom", "my kid", "my sibling"   | `categories/family/`       |
| "my friend", "my neighbor"         | `categories/people/`       |

It also updates the right `_index.md` files and the import log so future recalls can find the note. See [`skills/archive-github/SKILL.md`](skills/archive-github/SKILL.md) for the full rules.

---

## Privacy and safety

- **Your memory repo should be Private.** The template flow defaults to Private. Keep it that way.
- **AI You preserves meaning, not secrets.** The archive skill is told to redact: passwords, API keys, auth tokens, bank details, SSNs, private keys, exact credentials, exact phone numbers, and anything dangerous if leaked.
- **The public repo (`utb2017/ai-you`) must never receive your personal notes.** Both skills are told to refuse writes to the public foundation.
- **You can read, edit, or delete anything any time.** The notes are plain Markdown files in your own GitHub account.

For more, see [`docs/PRIVACY.md`](docs/PRIVACY.md) and [`SECURITY.md`](SECURITY.md).

---

## Troubleshooting (the short version)

ChatGPT says GitHub is connected but cannot write?

1. Make sure your private repo exists, is named correctly, and is granted to ChatGPT in the GitHub connector.
2. Some ChatGPT model surfaces hide the GitHub write tool. If yours does, **switch model** (in our testing, the standard "extended thinking" model exposed the GitHub and memory tools more reliably than Pro). Then rerun the setup prompt.
3. Ask ChatGPT to run the setup smoke test again. If it can create the smoke-test file and read it back, you're good.
4. Confirmation pop-ups are normal. The GitHub connector is allowed to ask you to confirm a write. Press Confirm.

The longer playbook is in [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md).

---

## What's in this repo

```text
ai-you/
  README.md                 - this file
  index.md                  - root index for your private memory repo
  categories/               - one folder per life category
  skills/                   - Archive GitHub + Recall Context instructions
  prompts/                  - the three prompts you paste into ChatGPT
  templates/                - Markdown templates for new notes
  logs/                     - import log + smoke-test folder
  docs/                     - quickstart, FAQ, troubleshooting, privacy, demo guide
  .github/                  - issue + PR templates for this public repo
```

The same structure is copied into your private `ai-you-memory` repo when you create it from the template.

---

## Learn more

- [Quickstart](docs/QUICKSTART.md) — the simplest possible path from zero to working memory.
- [FAQ](docs/FAQ.md) — common questions before and after setup.
- [Troubleshooting](docs/TROUBLESHOOTING.md) — what to try when something is off.
- [Privacy](docs/PRIVACY.md) — what AI You does and does not see.
- [Demo guide](docs/VIDEO_DEMO_SCRIPT.md) — for creators who want to make a video about this.
- [Contributing](CONTRIBUTING.md) — how to suggest improvements (only edits to the public foundation, never anyone's personal data).

---

## License

[MIT](LICENSE). Use it, fork it, remix it, build on it.

---

## One last thing

If this saves you from typing "let me explain my situation again…" one more time, that's the entire goal. Make a copy, run the setup prompt, save your first chat, and move on with your day.
