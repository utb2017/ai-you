# Text My Person Skill

Command name: `Text my <person>`

Aliases:

- `text my mom`, `text my dad`, `text my wife`, `text my husband`, `text my partner`,
  `text my boyfriend`, `text my girlfriend`, `text my kid`, `text my son`, `text my daughter`,
  `text my boss`, `text my coworker`, `text my friend`, `text my doctor`,
  `text <name>`, `text <phone number>`
- `send my <person> a text`, `send a text to my <person>`
- `draft a text to my <person>`, `make a text-link for my <person>`

Default private repo name:

`ai-you-memory`

Default contacts file (in the user's **private** repo):

`contacts/contacts.md`

## Purpose

Turn a request like `Text my mom and tell her I'll be late for dinner` into a **tappable SMS link** the user can press on their phone. Tapping the link opens the device's native Messages app with the recipient and body pre-filled. The user still presses Send.

This skill **never sends a message**. It only drafts and builds a link.

## Safety contract (non-negotiable)

- This skill never claims to have sent a message.
- This skill never invents phone numbers. If the contact is not in `contacts/contacts.md` and the user has not given a number directly in the prompt, the skill stops and asks for the number once.
- This skill always shows the user the recipient label, the recipient number (or a redacted preview), and the full body text **before** the link, so the user can verify before tapping.
- This skill does not save phone numbers into archived chat notes by default. When archiving is requested afterward, exact numbers are redacted; only the contact label is preserved.
- This skill does not write to the public foundation repo `utb2017/ai-you`. Contacts live in the user's **private** memory repo.

## Inputs

The skill accepts any of these shapes:

1. By saved alias: `Text my mom and tell her I'll be late.`
2. By saved name: `Text Sam and let him know I landed.`
3. By raw number: `Text +1 555 555 0100 and say running late.`
4. With explicit body: `Text my wife: "running late, see you in an hour"`.
5. Without body (skill drafts a short, plausible message based on the chat context).

## Where contacts live

In the user's **private** memory repo, at:

```
contacts/contacts.md
```

The file is a Markdown table the user fills in once. The shape lives in `templates/contacts-template.md`. Example row:

```markdown
| Mom | mother | +15555550100 | family |
```

The skill must read **only** the user's private repo for contacts. It must never read or write contacts in the public foundation repo.

## SMS link format

Build a single `sms:` URL that works on both iOS and Android. The cross-platform-safe format:

```
sms:<E.164 phone number>?body=<URL-encoded body>
```

Notes:

- Use E.164 format for the number (`+15555550100`), with no spaces, dashes, or parentheses.
- URL-encode the body. Spaces become `%20`. Newlines become `%0A`. Quotation marks, ampersands, and emoji must also be encoded.
- Do not put more than one recipient in the link. Single-recipient links work consistently across both platforms.
- If the user clearly wants iMessage rather than SMS, the same `sms:` link still opens Messages on iOS; iMessage vs SMS routing is handled by the device, not by this skill.

## Output shape

The skill replies in this exact order:

1. **Recipient line:** the contact label, the relationship, and a redacted preview of the number, e.g. `To: Mom (mother) — +1 (•••) •••-0100`.
2. **Body line(s):** the full message text the user is about to send, in a quoted block so it's easy to read.
3. **The SMS link:** a single tappable link. Use Markdown link syntax with descriptive anchor text, e.g. `[Open in Messages](sms:+15555550100?body=Hey%20mom%2C%20running%20late)`.
4. **Plain-text fallback:** the same `sms:` URL on its own line, in case the link surface doesn't render. Prefix with `sms-link:`.
5. **Safety reminder:** one short line, e.g. `This will not auto-send. Tap the link, then press Send in Messages.`

## Decision tree

```
user says "text my <alias>" or "text <name>"
│
├── alias / name found in contacts/contacts.md
│   └── draft body (or use user-supplied body)
│       └── build sms link
│           └── reply with output shape
│
├── alias / name NOT found, user gave a phone number
│   └── draft body (or use user-supplied body)
│       └── build sms link
│           └── reply with output shape
│
└── alias / name NOT found, no number given
    └── reply: "I don't see <alias> in your contacts. Add a row in contacts/contacts.md, or give me their number and I'll draft the link." (DO NOT GUESS.)
```

## Drafting bodies

If the user did not supply explicit body text:

- Keep it short (one or two sentences).
- Match the user's voice from the current chat. If the chat is casual, the text is casual. If the user is upset, do not invent emotional language they didn't use.
- Never include sensitive details the user didn't mention.
- If the recipient is in `categories/relationship/`, `family/`, or `people/` and the archive contains relevant context, prefer drafts that respect documented boundaries.

If the user supplies the body, use it verbatim, encoding-safe.

## Archiving a text afterward

If the user follows up with `Archive GitHub` or `write this down`:

- Save the chat using the archive-github skill.
- Save the contact label and the body of the message.
- **Redact the exact phone number** in the saved note. Use the same `+1 (•••) •••-0100` style preview.
- Cross-link to the relevant person/relationship/family note if one exists.

## Handling missing numbers

If the user has not yet created `contacts/contacts.md`:

- Reply: `You haven't set up your contacts yet. Open contacts/contacts.md in your private ai-you-memory repo, copy the shape from templates/contacts-template.md, and add the people you text most. Or paste a phone number into the chat and I'll draft the link directly.`
- Do not guess the number. Do not fabricate.

## Privacy rules

- Never write a contact's full phone number into any file under `categories/`, `logs/`, or anywhere outside `contacts/contacts.md`.
- Never include phone numbers in messages back to the user beyond a redacted preview.
- Never echo a phone number into the public foundation repo `utb2017/ai-you`.
- If a confirmation modal asks the skill to write `contacts/contacts.md`, that is acceptable. If a confirmation modal asks to write phone numbers anywhere else, refuse and tell the user the skill won't do that.

## Failure modes

If a session can't actually open `contacts/contacts.md` (read failure, no GitHub access exposed, etc.):

- Treat it the same as a missing alias.
- Ask for the number directly so the user can still get a working link.
- Offer to retry once the GitHub connector is available again.

If the user's device or surface won't render the `sms:` link as clickable:

- The plain-text `sms-link:` line is the fallback. The user can long-press to copy it and paste it into a browser or notes app on their phone.

## Final response shape (reminder)

```
To: Mom (mother) — +1 (•••) •••-0100

> Hey mom, running late. See you in an hour.

[Open in Messages](sms:+15555550100?body=Hey%20mom%2C%20running%20late.%20See%20you%20in%20an%20hour.)

sms-link: sms:+15555550100?body=Hey%20mom%2C%20running%20late.%20See%20you%20in%20an%20hour.

This will not auto-send. Tap the link, then press Send in Messages.
```

That's the whole skill.
