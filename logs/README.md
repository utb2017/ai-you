# Logs

This folder tracks imports, setup events, and workflow notes.

| File / folder | What it's for |
| --- | --- |
| [`import-log.md`](import-log.md) | One row per archived chat. The archive skill appends to it. |
| [`smoke-tests/`](smoke-tests/) | Tiny verification files that prove ChatGPT can write to your private repo. |
| [`relay-packets/`](relay-packets/) | Optional. Created automatically when you ask for "single packet mode," or when GitHub write fails and ChatGPT falls back to a relay packet. |

## When you'd actually open these

- **`import-log.md`** — when you want a one-page list of everything that's been archived. The archive skill keeps it tidy on its own.
- **`smoke-tests/`** — only during setup or when you're debugging. Once setup works, you can ignore it. Old smoke-test files are safe to delete.
- **`relay-packets/`** — when you want to copy a relay packet by hand into the right places, or when you're investigating a failed write.

Nothing in this folder is sacred. You can delete old files freely.
