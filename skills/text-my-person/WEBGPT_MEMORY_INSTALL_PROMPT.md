# WebGPT Memory Install Prompt — Text My Person

Paste this once if you want ChatGPT to remember the `Text my <person>` skill across future chats. The optional setup prompt at `prompts/04-install-text-my-person.md` includes this, so most users won't need it separately.

```markdown
Please remember this as a durable AI You command:

Command: `Text my <person>` (and equivalents like "text my mom", "text my wife", "text Sam", "text my boss", "send a text to my friend", "draft a text to my husband")

When I use that command, run the AI You text-my-person skill from the public foundation:
`utb2017/ai-you/skills/text-my-person/SKILL.md`

Operating rules:

- This skill never sends a message. It builds a tappable `sms:` link that opens my phone's Messages app with the recipient and body pre-filled. I still press Send.
- Look up the contact in my private repo at `contacts/contacts.md`. The shape is defined in `templates/contacts-template.md`.
- If a contact is missing, ask me for the phone number once. Do not guess and do not fabricate.
- Use E.164 phone format and URL-encode the body.
- Reply in this order: a recipient line with a redacted phone preview, the body in a quote block, the tappable Markdown link, a plain-text `sms-link:` fallback, and a one-line safety reminder.
- Never write phone numbers anywhere outside `contacts/contacts.md`. Never write contacts or phone numbers to the public foundation repo `utb2017/ai-you`.
- If I follow up with `Archive GitHub`, redact the exact number when saving and cross-link to the right person / relationship / family note.

If memory is available in this session, save this command.
```
