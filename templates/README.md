# Templates

These are the Markdown shapes the skills use when saving notes. You don't need to memorize them — ChatGPT reads them when it works. They're here so you (and reviewers) can see what notes will look like.

## Note templates

| Template | When the archive skill picks it |
| --- | --- |
| [`chat-summary-template.md`](chat-summary-template.md) | Default for any archived chat. |
| [`person-note-template.md`](person-note-template.md) | When the chat is mostly about one specific person. |
| [`project-note-template.md`](project-note-template.md) | When the chat is mostly about a specific project, app, or company. |
| [`relationship-note-template.md`](relationship-note-template.md) | When the chat is about an ongoing relationship pattern. |
| [`decision-template.md`](decision-template.md) | When the chat is centered on a decision being made. |

## Skill data templates

| Template | Used by |
| --- | --- |
| [`contacts-template.md`](contacts-template.md) | The `Text my <person>` skill. Defines the shape of `contacts/contacts.md` in your private repo. |

## Adding your own template

In your private memory repo, drop a new `.md` file into `templates/` and tell ChatGPT about it the next time you archive:

```text
Archive GitHub

Use my custom template at `templates/<your-template>.md` for this note.
```

Templates are starting points, not constraints. The archive skill is allowed to skip sections that don't apply.
