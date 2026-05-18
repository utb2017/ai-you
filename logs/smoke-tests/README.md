# Smoke Tests

This folder is where ChatGPT writes small "did the write actually go through" files during setup.

If everything is wired correctly:

1. The setup prompt asks ChatGPT to create a file here.
2. ChatGPT writes the file (you may see one GitHub confirmation pop-up — press Confirm).
3. ChatGPT reads it back to prove the write persisted.
4. Setup is complete.

## Filename format

```text
YYYY-MM-DD-HHMM-github-write-smoke-test.md
```

Example:

```text
2026-05-18-1530-github-write-smoke-test.md
```

## File body

The default smoke-test body is one line:

```text
AI You GitHub write contact established.
```

That's it. Short on purpose, so a single confirmation modal handles the whole thing.

## When to delete old smoke-test files

Anytime. They are not used after setup. Clearing them out is fine. The presence of any one current file confirms a working write surface.

## Sample

A sample smoke-test file is checked into this folder as `SAMPLE-github-write-smoke-test.md` so you can see the shape. ChatGPT will create real ones with timestamped filenames.
