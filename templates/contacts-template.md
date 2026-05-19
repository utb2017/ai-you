# Contacts

Your private contacts file lives at `contacts/contacts.md` in your **private** `ai-you-memory` repo. This file is the template you copy from. The example rows use [555-prefix fictional numbers](https://en.wikipedia.org/wiki/555_(telephone_number)) reserved for examples — replace them with your real ones.

> Never put real phone numbers in the public AI You foundation repo (`utb2017/ai-you`). Numbers go only into your private memory repo.

## Shape

A simple Markdown table. Add as many rows as you want. Aliases let `Text my mom` work without typing a name.

```markdown
| Label | Relationship | Phone (E.164) | Aliases | Notes |
| --- | --- | --- | --- | --- |
| Mom | mother | +15555550100 | mom, mother | birthday Jan 1 |
| Sam | partner | +15555550111 | sam, my partner, my wife, my husband, my girlfriend, my boyfriend | only one partner alias should be active at a time |
| Mark | boss | +15555550122 | mark, my boss | prefers texts after 9am |
| Iris | kid | +15555550133 | iris, my kid, my daughter | pickup logistics |
| Dr. Patel | doctor | +15555550144 | dr patel, my doctor | clinic line, do not text outside hours |
```

## Rules of thumb

- Use **E.164** format (`+15555550100`). No spaces, no parentheses, no dashes. The `text-my-person` skill expects this shape.
- The **Aliases** column is what makes `text my <person>` work. Put every short phrase you might use (`my mom`, `my mama`, `mom`, `mother`).
- **One partner alias active at a time.** If you have past partners in your contacts, keep them in the file but don't give them the alias `my partner` / `my wife` / etc. — otherwise the skill will guess wrong.
- Add a **Notes** column for anything that should affect drafting: preferred tone, hours not to text, language, accessibility needs.

## Privacy

- Keep this file in your private repo. The `contacts/` folder in the public foundation is only a placeholder.
- The `text-my-person` skill is told never to copy phone numbers into archived chat notes; it redacts them as `+1 (•••) •••-0100`.
- If you ever share a screenshot or video of your repo, scrub or redact this file first. The cleanest demo is a fake contacts file with placeholder names.
