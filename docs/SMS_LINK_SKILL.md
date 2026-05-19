# SMS Link Skill — How It Works (and Doesn't)

The `Text my <person>` skill turns a request like:

> Text my mom and tell her I'll be late for dinner.

into a tappable link that opens your phone's Messages app with the recipient and body pre-filled, so all you have to do is press **Send**.

This page explains the safety model, the URL scheme behind the link, and how it interacts with the rest of AI You.

## What it does

- ChatGPT looks up the contact in your private repo at `contacts/contacts.md`.
- ChatGPT drafts a short message body (or uses your exact words if you supplied them).
- ChatGPT builds a single `sms:` URL with the phone number and the URL-encoded body.
- ChatGPT replies with the recipient label, a redacted phone preview, the message body in a quote block, the tappable link, a plain-text fallback, and a one-line safety reminder.

## What it does **not** do

- It never sends a message. There is no API key, no Twilio integration, no automated dispatch. The link is a deep link to your own Messages app.
- It does not store full phone numbers anywhere outside `contacts/contacts.md`.
- It does not write contacts to the public foundation repo (`utb2017/ai-you`). Contacts only ever live in your private memory repo.
- It does not silently broadcast. There is no group sending in this skill.

## The URL scheme

The skill builds a single SMS URL in this cross-platform-safe shape:

```
sms:<E.164 number>?body=<URL-encoded body>
```

For example, `Hey mom, running late, see you in an hour.` to `+15555550100` becomes:

```
sms:+15555550100?body=Hey%20mom%2C%20running%20late%2C%20see%20you%20in%20an%20hour.
```

- **iOS**: tapping the link opens Messages with the recipient and body filled in. iMessage vs SMS routing is decided by the device, not the link.
- **Android**: tapping the link opens the default messaging app with the recipient and body filled in.

## Why this is the safe shape for AI texting

LLMs and tools that send messages on your behalf are powerful and risky. The most common failure modes are:

- the wrong recipient,
- the wrong tone,
- a draft you didn't actually want sent,
- a draft sent to a group instead of an individual.

By making the **send button physically yours**, every one of those failure modes becomes a near-miss instead of a real problem. ChatGPT does the boring work — finding the number, drafting the body, encoding the URL. You do the irrevocable part.

## Setup in 2 minutes

1. Run [`prompts/04-install-text-my-person.md`](../prompts/04-install-text-my-person.md). It creates `contacts/contacts.md` in your private repo with placeholder rows.
2. Open `contacts/contacts.md` in your private repo and replace the placeholders with your real contacts. Use [`templates/contacts-template.md`](../templates/contacts-template.md) as a reference.
3. In a new chat, say: `Text my mom and tell her I'll be twenty minutes late.`
4. Tap the link on your phone.

That's it.

## Privacy details

- Real phone numbers belong **only** in your private `ai-you-memory` repo, **only** in `contacts/contacts.md`.
- The skill is told to redact phone numbers when archiving — saved chat notes preserve labels (e.g. "Mom") but show numbers as `+1 (•••) •••-0100`.
- For demos, screenshots, or videos, use a fake contacts file with invented names and 555-prefix fictional numbers (`+15555550100` through `+15555550199`).

## What if my session can't access my private repo?

If ChatGPT's current session can't read your private repo, you can still get a working link by giving the number directly:

```text
Text +1 555 555 0100 saying running late.
```

The skill builds the link from the number you supplied. It never guesses numbers it wasn't told.

## What if the link doesn't render as clickable?

Some surfaces in some apps don't render `sms:` links as tappable. The skill always includes a plain-text `sms-link:` line as a fallback. Long-press to copy the URL, then paste it into your phone's browser or notes app — it will still open Messages.

## What if I want to delete the skill later?

- Remove the `Text my <person>` rule from ChatGPT's memory.
- Delete `contacts/contacts.md` from your private repo (or just clear it out).
- The public foundation has no record of you ever installing it.

## Future skills built on this same pattern

The "deep link to a native app" pattern works beyond SMS. Future AI You skills could use the same shape for `tel:`, `mailto:`, calendar event URLs, or other safe actions. The same safety contract applies: the skill drafts; you act.
