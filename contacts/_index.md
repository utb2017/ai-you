# Contacts

This folder is where the **`Text my <person>`** skill looks up phone numbers when you ask it to draft a text.

In your **private** `ai-you-memory` repo, this folder should contain one file:

```
contacts/contacts.md
```

The shape is in [`templates/contacts-template.md`](../templates/contacts-template.md).

## Why this folder exists in the public foundation

So the path is reserved and the skill knows where to look when you copy this template into your private repo. **No real phone numbers should ever live in the public foundation.** Real contacts are written into your private repo and stay there.

## What goes here in the user's private repo

- `contacts.md` — a Markdown table of the people you text most, with E.164 phone numbers and aliases like `my mom`, `my wife`, `my boss`.

That's the entire folder. Keep it simple.

## What does NOT go here

- Long notes about people. Use `categories/people/`, `categories/relationship/`, `categories/family/`, or `categories/work/` for that.
- Email addresses. The current text-my-person skill is SMS only.
- Group chats. The `sms:` URL scheme is most reliable with single recipients across iOS and Android.

## Privacy reminder

- Keep your private memory repo private.
- The `Text my <person>` skill is told never to copy numbers from this file into archived notes; it redacts them.
- For YouTube / Instagram / TikTok demos, use a **separate fake contacts file** with invented names like Mom, Sam, Mark, Iris, Dr. Patel and 555-prefix fictional numbers.
