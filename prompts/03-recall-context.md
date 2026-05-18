# Prompt 3 — Recall Context

Use this at the **start** of a chat about a recurring person, project, problem, relationship, work topic, health pattern, or trip. It tells ChatGPT to read your private `ai-you-memory` repo before answering, so it sounds like it actually remembers you.

## Short form

```text
Recall Context

Pull the relevant context from my GitHub memory before you answer.
```

## Targeted forms

If you want to point at one area of your life:

```text
Recall Context

Pull my relationship context before you answer.
```

```text
Recall Context

Pull my work / project context before you answer.
```

```text
Recall Context

Pull my health context before you answer. Look for recurring patterns, doctors, and medications.
```

```text
Recall Context

Pull travel / trip context before you answer.
```

## Long form (if ChatGPT seems to have forgotten the skill)

````markdown
Recall Context.

Use the recall-context skill from the public foundation:
`utb2017/ai-you/skills/recall-context/SKILL.md`

Read my private `ai-you-memory` repo and pull the most relevant context before you answer my next question.

Steps:

1. Identify the likely domain (relationship, work, health, travel, family, projects, business, ideas, memories).
2. Read the root `index.md` and the relevant `categories/<category>/_index.md`.
3. Search notes for exact names, projects, and repeated terms.
4. Prefer recent high-confidence notes, but include older notes that explain the current pattern.
5. Read only the notes you actually need.

Open your reply with a short context-grounded line that proves you read the repo, like:

`I pulled your AI You context. The relevant pattern is …`

Then summarize:

- who or what I am talking about,
- what the archive says matters,
- what is relevant to my current question,
- a practical next step.

Do not ask me to re-explain background that is already in the repo. Do not over-explain how retrieval worked unless I ask.
````

## When to skip Recall Context

If you are asking a quick factual question that doesn't depend on your life history, you don't need to run this. The point of `Recall Context` is to bring continuity into chats where the model would otherwise reset and ask you to re-explain yourself.
