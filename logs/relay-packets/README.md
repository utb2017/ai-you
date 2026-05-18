# Relay Packets

This folder holds **archive relay packets**.

A relay packet is a single Markdown file that contains:

- the full body of the note(s) ChatGPT wanted to save,
- the index updates that should be applied,
- the import-log row that should be added,
- a suggested commit message.

It exists for two reasons.

## 1. "Single packet mode"

If you want fewer GitHub confirmation pop-ups, you can ask ChatGPT to write **one** combined file here instead of four separate files:

```text
Archive GitHub — single packet mode

Write everything as one combined Markdown file in my private repo at
`logs/relay-packets/YYYY-MM-DD-HHMM-archive-packet.md`
including the full note body and the index/log updates I should apply.
I will reconcile the indexes and logs later.
```

That collapses the archive into one write and one confirmation. You can split the packet into the proper places later, or leave it here forever — it's still durable Markdown.

## 2. GitHub write fallback

If ChatGPT's current model surface can't actually write to GitHub, the archive skill is told to produce a relay packet inline (or as a downloadable file) so the memory is not lost. You can paste that packet here, then reconcile.

## Naming

```text
YYYY-MM-DD-HHMM-archive-packet.md
```

Example:

```text
2026-05-18-1530-archive-packet.md
```

You can delete old packets after you've reconciled them into the proper category folders.
