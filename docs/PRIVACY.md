# Privacy

AI You is a free public template. There is no AI You server, no AI You account, and no AI You database. We do not see, store, or process anything you save.

This page explains the trust model so you can decide what's right for you.

## What runs where

```
You ──► ChatGPT (OpenAI) ──► GitHub connector ──► Your private GitHub repo
```

- **You** type into ChatGPT.
- **ChatGPT** is OpenAI's product, with OpenAI's privacy practices. Read [openai.com/privacy](https://openai.com/privacy) if you want to know what they retain.
- **The GitHub connector** is the bridge ChatGPT uses to read and write files in repos you authorize.
- **Your private repo** lives in your own GitHub account, under your privacy settings, with version history you control.

AI You is the **instructions and templates** that flow through this pipe. We don't sit in the path. We don't see the messages. We don't see the files.

## What goes into your repo

Whatever you tell ChatGPT to archive. By default, that means:

- A short Markdown summary of an important conversation.
- A category folder (relationship, work, etc.).
- An index and log entry pointing at the new file.

The archive skill is told to **redact** the following before writing:

- Passwords
- API keys, auth tokens, secrets
- Bank account numbers, card numbers, CVVs
- SSNs / national IDs
- Private keys
- Exact credentials of any kind
- Exact phone numbers
- Home address details specific enough to locate you

It is told to **preserve meaning, not secrets**. If a chat reveals a password, the skill writes `[redacted]` and continues.

If you ever spot something in a saved note that you didn't want there, delete or edit the file in GitHub. The notes are plain Markdown.

## Public vs private boundary

There are two repos:

- **Public foundation:** [`utb2017/ai-you`](https://github.com/utb2017/ai-you). Contains only instructions, prompts, skills, categories, templates, and docs. No personal data. Ever.
- **Your private memory repo:** the copy you made from the template, default name `ai-you-memory`. Contains your notes. Stays private.

Both skills (`Archive GitHub` and `Recall Context`) are told:

- Personal notes go **only** in your private repo.
- The public foundation is **never** written to.

If a confirmation modal in ChatGPT asks you to approve a write to the public foundation repo, cancel it. That's a model that lost context.

## Sharing screenshots and videos

If you make a video or screenshot of your AI You workflow:

- Be aware your private repo's contents will be visible.
- Names, decisions, and personal context can leak through your repo's index page or note titles.
- Consider creating a **separate demo memory repo** with fictional data when filming.

We recommend a demo repo with names you invent. The video angle works just as well, without leaking your real life.

## Revoking access

You can stop AI You at any time:

- Remove the GitHub connector inside ChatGPT.
- Or remove ChatGPT's access to the specific private repo from your GitHub connector settings.
- Or delete the private repo entirely.

There is nothing else to "uninstall." There is no AI You account.

## What we ask of contributors

If you submit a pull request to the public foundation, do not paste anyone's personal context into the PR. The public foundation must stay generic. See [CONTRIBUTING.md](../CONTRIBUTING.md).

## Reporting a privacy issue

If you spot something in this public template that looks like personal data, open an issue or email the maintainer. See [SECURITY.md](../SECURITY.md).
