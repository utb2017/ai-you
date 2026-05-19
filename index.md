# AI You — Index

This is the root index for an AI You memory archive. In **your private** `ai-you-memory` repo, this file is what ChatGPT scans first when you say `Recall Context`. In the public foundation repo, this file is empty of personal data and just shows the shape.

## Categories

- [Relationship](categories/relationship/_index.md)
- [Work](categories/work/_index.md)
- [People](categories/people/_index.md)
- [Family](categories/family/_index.md)
- [Health](categories/health/_index.md)
- [Travel](categories/travel/_index.md)
- [Projects](categories/projects/_index.md)
- [Business](categories/business/_index.md)
- [Ideas](categories/ideas/_index.md)
- [Memories](categories/memories/_index.md)
- [Inbox](categories/inbox/_index.md)

## Skill data

- [Contacts](contacts/_index.md) — used by the optional `Text my <person>` skill.

## Recent Imports

No imports yet.

## Logs

- [Import log](logs/import-log.md)
- [Smoke tests](logs/smoke-tests/)
- [Relay packets](logs/relay-packets/)

## How this index gets updated

The archive skill updates this file when an archive is **major or recurring**. Smaller archives only touch the relevant category `_index.md` and the import log, to avoid stuffing the root index with everything.

If you ever want to clean it up by hand, you can. It's plain Markdown.
