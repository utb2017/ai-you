# FAQ

### Is AI You an app?

No. AI You is a free public GitHub template plus two short commands. There is no AI You server, no account to make, no data we collect. Your memory lives in a GitHub repo you own.

### Is this safe?

Your memory repo is **private** by default. Only you and ChatGPT (through the GitHub connector you authorize) can read or write to it. The archive skill is also told to redact passwords, API keys, exact credentials, SSNs, exact phone numbers, and similar dangerous data even though the repo is private.

You can read, edit, or delete any file in your repo at any time. There is no vendor lock-in. The notes are plain Markdown.

### Does AI You see my data?

No. We have no servers and no telemetry. You give ChatGPT access to **your** GitHub. ChatGPT writes to and reads from **your** private repo. Nothing flows through us.

### Do I need to know GitHub?

No. If you can click "Use this template" and copy a prompt into ChatGPT, you can use AI You. You never have to write code, open a terminal, or learn git.

### Why GitHub instead of a fancy app?

- It's already where many of us back up text files.
- It's free at the size your memory will ever be.
- It supports private repos, version history, and easy export.
- ChatGPT can read and write to it through the GitHub connector.
- Markdown is human-readable forever, even without ChatGPT.

### Why two commands instead of one?

`Archive GitHub` and `Recall Context` are different jobs.

- Archive is a closer: end of an important chat, save the durable parts.
- Recall is an opener: start of a new chat about something recurring, pull continuity.

If we collapsed them into one phrase, ChatGPT would have to guess which one you meant, and the workflow would be less reliable. Two commands keep it predictable.

### What if ChatGPT doesn't show GitHub write tools?

The GitHub write action lives behind a confirmation modal, and not every ChatGPT model surface exposes it.

If `Archive GitHub` produces only a summary instead of an actual file in your repo:

1. Try switching ChatGPT models. In our testing, the standard "extended thinking" model exposed the GitHub write surface more reliably than Pro.
2. Re-run the setup prompt. The smoke-test step is the fastest way to find out whether your current session can write.
3. As a last resort, the archive skill is told to produce a complete `LOCAL ARCHIVE RELAY PACKET` — a single Markdown blob you can paste into your repo by hand.

### What if a confirmation pop-up keeps appearing?

That's the GitHub connector's safety check. It's expected. Press Confirm.

If you want to reduce how often you see it, ask for **single packet mode**:

```text
Archive GitHub — single packet mode

Write everything as one combined Markdown file in my private repo at
`logs/relay-packets/YYYY-MM-DD-HHMM-archive-packet.md`
including the full note body and the index/log updates I should apply.
I will reconcile the indexes and logs later.
```

### Can I use a different repo name?

Yes. The default is `ai-you-memory`. If you pick a different name, replace `ai-you-memory` in the setup prompt with your name. Everything else still works.

### Can I add my own categories?

Yes. The skills already mention an `inbox` category as a fallback. To add a new category like `finance` or `parenting`:

1. Create a folder in your private repo: `categories/finance/`.
2. Add a `_index.md` to that folder, similar to the existing ones.
3. Optional: tell ChatGPT to remember the new category.

### Can I share my repo with others?

You can, but think about it first. The data inside is by definition the stuff you didn't want to repeat. If you share it, you are sharing a snapshot of your private life or work. We recommend keeping it private.

If you want to share patterns or a workflow, share **this public template** instead. That's why it exists.

### What about other AI tools?

The folder structure is just Markdown, so any AI assistant that can read GitHub or read Markdown files can use it. The two commands are tuned for ChatGPT today, but the same notes are readable by Claude, Gemini, local models, or any future tool.

### Can I delete everything later?

Yes. Delete the GitHub repo. Or remove ChatGPT's access in the GitHub connector. Or both. Nothing about AI You creates lock-in.

### Is there a paid version?

Not right now. AI You is a free public foundation. If we ever offer paid services (a hosted setup helper, polished templates, a course, or a consumer app), the underlying free template will keep working.

### Why "AI You"?

Because the goal is not to give ChatGPT yet another generic memory. It's to give ChatGPT continuity about **you** — the people, projects, and patterns that make up your life.

### Recall Context pulled my history but the actual reply was thin. What's going on?

This is a known failure mode when you ask ChatGPT to recall and respond in one motion (for example, "Recall Context, then let's talk about my partner"). Some model surfaces will spend most of their output budget on summarizing the retrieved notes and short-change the actual reply.

The recall-context skill in this repo is now told to budget for the response over the retrieval — keep the retrieval summary to 3 to 5 bullets, then go deep on the reply. If you still see thin replies, you can force the budget yourself by asking:

```text
Recall Context. Keep your retrieval summary to 5 bullets max, then give me a full human reply about <topic>.
```

If the chat was a vent rather than a question, you can also say:

```text
Recall Context. I'm not asking for a list, I'm processing. Reflect first, then suggest a next step at the end.
```

The skill is told to recognize venting and respond with depth instead of a bullet list, but a direct nudge from you is the most reliable fix until model surfaces stabilize.

### What's the `Text my <person>` skill?

It's an optional **bonus skill** that turns a request like `Text my mom and tell her I'll be late` into a tappable `sms:` link. Tapping the link opens your phone's Messages app with the recipient and body pre-filled. **You** still press Send. ChatGPT can't send anything on its own — there is no third-party messaging API in the loop. See [`docs/SMS_LINK_SKILL.md`](SMS_LINK_SKILL.md). To install it, see [`prompts/04-install-text-my-person.md`](../prompts/04-install-text-my-person.md).

Real phone numbers go only in your private repo, only in `contacts/contacts.md`. They are never written to the public foundation.
