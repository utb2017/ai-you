# Prompt 4 — Install Text My Person (optional)

Run this **once**, after the main setup is working, if you want ChatGPT to remember the `Text my <person>` skill.

This prompt does three things:

1. Reads the `text-my-person` skill from the public foundation.
2. Creates `contacts/contacts.md` in your private memory repo from the template (with placeholder rows).
3. Installs `Text my <person>` as a durable command in ChatGPT memory.

Paste everything inside the code block below into ChatGPT.

````markdown
Install the AI You "Text my <person>" skill for me.

Use the GitHub connector / app.

Public foundation repo:
`utb2017/ai-you`

My private memory repo:
`ai-you-memory`

Steps:

1. Read the public skill file:
   - `utb2017/ai-you/skills/text-my-person/SKILL.md`
2. Read the public template:
   - `utb2017/ai-you/templates/contacts-template.md`
3. In my private `ai-you-memory` repo, create or update:
   - `contacts/contacts.md`
   - Use the table shape from the template.
   - Use placeholder rows only (Mom / Sam / Mark / Iris / Dr. Patel with 555-prefix fictional numbers like +15555550100). Do NOT invent real numbers and do NOT prompt me for real numbers during install.
   - Tell me to fill in the file by hand later, in GitHub or any text editor.
4. Verify the file exists by reading it back from my private repo.
5. If memory is available in this session, remember this durable command:
   - `Text my <person>` (and equivalents like "text my mom", "text my wife", "text Sam", "text my boss", "send a text to my friend") means: run the AI You text-my-person skill, look up the contact in `contacts/contacts.md`, draft an appropriate body, and reply with a tappable `sms:` link plus a plain-text fallback. Do NOT auto-send. Always show the recipient and body before the link.

Operating rules to remember:

- Phone numbers go only in my private repo, only in `contacts/contacts.md`, never in the public foundation.
- The skill never sends. It only drafts and builds the link. I press Send in Messages.
- If a contact is missing when I use the skill later, ask me once for the phone number. Do not guess and do not fabricate.
- When I follow up with `Archive GitHub`, redact the phone number in the saved note.

Confirm install is complete only after:

- `contacts/contacts.md` exists in my private repo with the placeholder rows,
- you have read it back from GitHub,
- you have stored the command in memory if memory was available,
- you have summarized in 4 lines or less how I should use it.

If GitHub write actions are not visible in this session:

- Search / list / discover the GitHub connector / app actions before giving up.
- If this model surface still cannot write, tell me clearly: "This session does not expose a GitHub write action. Switch to a different ChatGPT model and rerun this install prompt." Do NOT claim GitHub or my repo is broken.
````

## What success looks like

- `contacts/contacts.md` exists in your private `ai-you-memory` repo with placeholder rows.
- ChatGPT confirms it remembers the `Text my <person>` command.
- A short note from ChatGPT explaining how to fill in your real contacts later.

To test, open the file in GitHub, replace one placeholder row with a real contact (use yourself!), and ask ChatGPT in a new chat:

```text
Text myself: testing the new AI You SMS skill.
```

You should get back a tappable link, a body preview, and the safety reminder. Tap the link on your phone — Messages opens to you, with the body waiting. Press Send to confirm the loop. Don't send.
