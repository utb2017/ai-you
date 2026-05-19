# Quickstart

The shortest path from "I just heard about AI You" to "ChatGPT now remembers me."

You'll need:

- A GitHub account (free).
- ChatGPT (free or paid). The GitHub connector must be available to your account.
- About 10 minutes.

## 1. Connect GitHub to ChatGPT

In ChatGPT, open connectors / apps and turn on GitHub. When GitHub asks which repos ChatGPT can read and write, you can pick:

- **All repositories**, or
- **Only select repositories** (recommended). You can add the repo we're about to make in a moment.

OpenAI's help docs:

- [Connecting GitHub to ChatGPT](https://help.openai.com/en/articles/11145903-connecting-github-to-chatgpt)
- [Connectors in ChatGPT](https://help.openai.com/en/articles/11487775)

## 2. Make your private memory repo

Click [Use this template](https://github.com/utb2017/ai-you/generate).

- Repository name: `ai-you-memory` (recommended; you can pick a different name and change it in the prompts).
- Visibility: **Private**.
- Click **Create repository from template**.

If you chose "Only select repositories" in step 1, go back to GitHub's connector settings now and add `ai-you-memory` to the allowed list.

## 3. Run the setup prompt

Open a new ChatGPT chat. Paste the contents of [`prompts/01-setup-ai-you.md`](../prompts/01-setup-ai-you.md) (the markdown block inside it).

ChatGPT should:

1. Read this public foundation repo.
2. Confirm your private `ai-you-memory` repo is reachable.
3. Read the two skill files.
4. Run a smoke test: create one small file in `logs/smoke-tests/` and read it back.
5. Memorize the two commands.

If a confirmation pop-up appears asking whether ChatGPT can write a file in your private repo, press **Confirm**. That's the GitHub connector's safety check, and it's expected.

## 4. Verify it worked

Open your `ai-you-memory` repo on GitHub. You should see:

- A new file inside `logs/smoke-tests/`, dated today, that says `AI You GitHub write contact established.`

If you see that file, setup worked. If not, see [Troubleshooting](TROUBLESHOOTING.md).

## 5. Try a real save and recall

In the same chat, say a few sentences about a real recurring topic in your life — a relationship pattern, a project you keep coming back to, a health routine. Then say:

```text
Archive GitHub
```

Watch ChatGPT pick a category, write a Markdown note in your private repo, and update the index and import log. Open the repo to confirm.

Now open a brand-new ChatGPT chat and say:

```text
Recall Context

Pull my [topic] context before you answer.
```

then ask a follow-up question about that same topic.

If ChatGPT opens its reply with something like "I pulled your AI You context. The relevant pattern is …" and references what you wrote earlier, AI You is working.

## You're done

From here on, your loop is:

- meaningful chat → `Archive GitHub`
- new chat about a recurring topic → `Recall Context`

Everything else is optional.

## Optional bonus skill: `Text my <person>`

If you want ChatGPT to draft texts and build tappable `sms:` links to your saved contacts, run [`prompts/04-install-text-my-person.md`](../prompts/04-install-text-my-person.md). It does not auto-send. You still press Send in Messages. See [`docs/SMS_LINK_SKILL.md`](SMS_LINK_SKILL.md) for the full safety model.
