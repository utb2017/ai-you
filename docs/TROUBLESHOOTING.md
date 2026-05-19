# Troubleshooting

If something is off, walk this list in order. Most issues are model surface or connector permission, not the prompts or your repo.

## 1. Setup smoke test never produced a file

**Symptom:** You ran Prompt 1, ChatGPT said it was working, but you don't see a file inside `logs/smoke-tests/` in your private repo.

**Try:**

1. **Confirm the repo exists and is named correctly.** Open `https://github.com/<your-username>/ai-you-memory`. If it's not there, go back to step 3 of [Quickstart](QUICKSTART.md).
2. **Confirm ChatGPT has access to it.** In ChatGPT, open the GitHub connector settings. If you used "Only select repositories," make sure `ai-you-memory` is in the allowed list.
3. **Re-paste the setup prompt.** Sometimes ChatGPT lost the conversation halfway through. A fresh paste in a fresh chat is faster than debugging.
4. **Check for a missed confirmation pop-up.** Some sessions show a small "approve this write" modal. If you ignored it, ChatGPT may report success without an actual write. Press Confirm next time.

## 2. ChatGPT says it can't write to GitHub

**Symptom:** ChatGPT replies with something like "I don't have a write tool available" or "I can only read this repo."

**Try:**

1. **Switch ChatGPT models.** The GitHub write action is not exposed identically across every model surface. In our testing, the standard "extended thinking" model exposed GitHub and memory tools more reliably than Pro. Switch model and rerun the setup prompt.
2. **Reconnect the GitHub connector.** Toggle it off and on, and re-grant access to your private repo.
3. **Use the relay packet fallback.** Even when GitHub write is unavailable, the archive skill is told to produce a `LOCAL ARCHIVE RELAY PACKET` — a single Markdown blob containing the file body, the index updates, and the log row. Copy that packet into your repo by hand.

## 3. Archive GitHub made one shallow note instead of organizing the chat

**Symptom:** ChatGPT saved the whole conversation as one generic summary and did not split obvious topics, update category indexes, update `logs/import-log.md`, or verify writes.

**Try:**

1. **Switch out of instant/fast mode.** Use a reasoning/extended-thinking mode for archive work.
2. **Paste the long archive prompt** from [`prompts/02-archive-github.md`](../prompts/02-archive-github.md).
3. Add this line:
   ```text
   Run the full archive workflow. Split major topics into separate notes when needed, update category indexes, update logs/import-log.md, and verify the files by reading them back.
   ```
4. If the chat is messy or very long, archive in chunks: relationship first, work/project second, health/travel third.

Instant/fast answers are useful for quick replies. They are not the best surface for careful archive execution.

## 4. ChatGPT keeps asking me to confirm writes

That's the GitHub connector's safety check. It's normal. Press Confirm.

If you want fewer pop-ups, switch the archive into single-packet mode:

```text
Archive GitHub — single packet mode

Write everything as one combined Markdown file in my private repo at
`logs/relay-packets/YYYY-MM-DD-HHMM-archive-packet.md`
including the full note body and the index/log updates I should apply.
I will reconcile the indexes and logs later.
```

That collapses the archive into one write and one confirmation.

## 5. Recall returns a generic answer that ignores my repo

**Symptom:** You said `Recall Context` but ChatGPT answered like a fresh chat, with no reference to anything you've archived.

**Try:**

1. **Add a domain hint:** "Recall Context. Pull my **relationship** context before you answer."
2. **Make sure there's something to recall.** Open your private repo and confirm `categories/<category>/` actually has notes inside. If it's empty, go archive a chat first.
3. **Re-run the setup prompt.** It may have forgotten the recall skill. The setup prompt re-installs both commands.
4. **Paste the long form** of `prompts/03-recall-context.md` to force the skill into the current chat.

## 6. The archive saved to the wrong category

**Symptom:** A relationship chat ended up in `inbox`, or a work chat ended up in `people`.

**Try:**

1. **Move the file by hand** in GitHub. The archive skill is just picking the strongest category at the moment of save; nothing stops you from moving it.
2. **Add a category hint** when archiving:
   ```text
   Archive GitHub — save this to my relationship category.
   ```

## 7. Confirmation modal asks about a public repo

If a confirmation modal mentions writing to `utb2017/ai-you` (the public foundation) instead of your private repo, **do not press Confirm**. Cancel, and re-run the setup prompt. The archive skill is told to refuse personal writes to the public foundation, but a model that lost context might still try; the modal is your last line of defense.

## 8. `sms:` links don't open Messages

**Symptom:** The Text My Person skill creates a link, but clicking it does not open Messages.

**Try:**

1. **Use the link on a phone.** Desktop browsers may not know what to do with `sms:` links.
2. **Long-press the `sms-link:` line** in the reply (the plain-text fallback). Copy it. Paste it into your phone's browser address bar. Most phones will then offer to open Messages.
3. **Check the link is actually a `sms:` URL.** Some surfaces wrap the URL in trackers — if it starts with `https://` instead of `sms:`, ChatGPT misformatted it. Ask: `Re-do the link as a raw sms: URL with the body URL-encoded.`
4. **Check the number format.** It must be E.164: `+15555550100`, no spaces, no dashes, no parentheses.
5. **Test with yourself first.** Replace one row in `contacts/contacts.md` with your own number, then run `Text myself: testing.` Tap the link. If that works, the issue is the number formatting in the original row.

The skill never auto-sends. It should only open Messages with the recipient and body filled in.

## 9. I want to start over

You can:

- Delete your private memory repo on GitHub and create a new one from the template.
- Revoke ChatGPT's GitHub access from the connector and re-grant it later.
- Edit any file directly in GitHub. They're plain Markdown.

Nothing in AI You creates lock-in.

## Still stuck?

Open an issue on the public foundation:

[github.com/utb2017/ai-you/issues](https://github.com/utb2017/ai-you/issues)

Don't paste your private notes into the issue. Describe what failed and the model / connector you used.
