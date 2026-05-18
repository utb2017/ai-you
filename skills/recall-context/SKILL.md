# Recall Context Skill

Command name: `Recall Context`

Aliases:

- `pull context`
- `pull my context`
- `check my memory`
- `check GitHub memory`
- `look up my context`
- `look up my relationship`
- `pull my relationship data`
- `pull my work context`
- `pull project context`
- `before you answer, check my GitHub`

Default private repo name:

`ai-you-memory`

## Purpose

When the user asks about a recurring person, relationship, project, work situation, health issue, trip, idea, or memory, retrieve relevant context from their private AI You GitHub memory repo before answering.

This is retrieval, not archiving. If the user asks to save the current chat, use `skills/archive-github/SKILL.md`.

## Strong Retrieval Triggers

Explicit commands:

- `Recall Context`
- `pull context`
- `check my memory`
- `check GitHub memory`
- `look up my relationship`
- `pull my relationship data`
- `pull my work context`
- `pull project context`

Person/relationship triggers:

- `my wife`
- `my husband`
- `my partner`
- `my spouse`
- `my girlfriend`
- `my boyfriend`
- `my kid`
- `my child`
- `my daughter`
- `my son`
- `my mom`
- `my dad`
- `my parent`
- `my boss`
- `my coworker`
- `my friend`
- `my neighbor`
- `my doctor`
- `my therapist`
- `my shrink`
- `my client`
- `my customer`

Project/category triggers:

- `my work`
- `my job`
- `my project`
- `my business`
- `my app`
- `my health`
- `my trip`
- `my vacation`
- `my idea`
- `my memory`

Do not over-trigger on every proper noun. If the user names a person/project in a high-context way and asks for perspective, retrieve. If the user asks a quick factual question, answer normally unless context is clearly needed.

## Retrieval Algorithm

1. Identify the likely domain:
   - relationship/person
   - work/project/business
   - health
   - travel
   - family
   - ideas/memories
2. Read root `index.md`.
3. Read likely category indexes.
4. Search notes for exact names, aliases, projects, and repeated terms.
5. Prefer recent high-confidence notes, but include older notes when they explain the current pattern.
6. Read only the most relevant notes needed to answer.
7. Answer with a short context-grounded summary first, then the actual help.

## Response Shape

Start with:

`I pulled your AI You context. The relevant pattern is...`

Then summarize:

- who/what the user is talking about
- what the archive says matters
- what is relevant to the current question
- a practical next step

Do not over-explain the retrieval mechanics unless asked.

## Archive Handoff

If new durable context appears and the user says:

- `archive this`
- `write this down`
- `save this to GitHub`
- `Archive GitHub`

switch to `skills/archive-github/SKILL.md`.

