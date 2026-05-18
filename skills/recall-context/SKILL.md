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

When the user asks about a recurring person, relationship, project, work situation, health issue, trip, idea, or memory, retrieve relevant context from the user's private AI You GitHub memory repo before answering.

This is a **retrieval** task. If the user asks to save the current chat, switch to the archive-github skill instead.

## Strong retrieval triggers

Explicit commands:

- `Recall Context`
- `pull context`
- `check my memory`
- `check GitHub memory`
- `look up my relationship`
- `pull my relationship data`
- `pull my work context`
- `pull project context`

Person / relationship triggers:

- `my wife`, `my husband`, `my partner`, `my spouse`, `my girlfriend`, `my boyfriend`
- `my kid`, `my child`, `my daughter`, `my son`
- `my mom`, `my dad`, `my parent`, `my sibling`
- `my boss`, `my coworker`, `my client`, `my customer`
- `my friend`, `my neighbor`
- `my doctor`, `my therapist`, `my shrink`

Project / category triggers:

- `my work`, `my job`
- `my project`, `my business`, `my app`, `my company`
- `my health`, `my sleep`, `my anxiety`, `my medication`
- `my trip`, `my vacation`, `my flight`
- `my idea`, `my memory`

Do not over-trigger on every proper noun. Use judgment:

- If the user clearly names a person / project in a high-context way and asks for advice or perspective, retrieve.
- If the user asks a quick factual question that has nothing to do with their life history, answer normally without searching.
- If the user explicitly says `Recall Context`, always retrieve, even for a small question.

## Retrieval algorithm

1. **Identify the likely domain** from the user's wording: relationship, work, health, travel, family, projects, business, ideas, memories.
2. **Read root `index.md`** of the private repo to get the overall map.
3. **Read the relevant category `_index.md` files** to find candidate notes.
4. **Search note bodies** for exact names, aliases, projects, and repeated terms from the user's message.
5. **Prefer recent high-confidence notes**, but include older notes when they explain the current pattern.
6. **Read only the most relevant notes**. Don't dump the whole repo.
7. **Answer with a short context-grounded summary first**, then the actual help the user asked for.

If the repo has no relevant notes yet, say so honestly: "I checked your AI You context and didn't find anything yet on this topic. Want me to archive what we discuss now so it's there next time?"

## Response shape

Open the reply with a short proof-of-retrieval line, like:

> I pulled your AI You context. The relevant pattern is …

Then summarize, in this order:

1. **Who or what** the user is talking about.
2. **What the archive says matters** (recurring patterns, decisions, boundaries, recent events).
3. **What is relevant to the current question**.
4. **A practical next step**, given that context.

Do not over-explain the retrieval mechanics unless the user asks. Do not list every file you read. Do not paste raw notes back at the user. Synthesize.

## Privacy and boundaries

- Read **only** the user's private memory repo, not the public `utb2017/ai-you` repo.
- Never write personal notes to the public foundation repo.
- If the user asks you to save what you just retrieved or discussed, switch to the archive-github skill.

## Archive handoff

If during a recall the user says any of the following, switch to the archive-github skill and run that flow instead:

- `archive this`
- `write this down`
- `save this to GitHub`
- `Archive GitHub`
- `save this memory`
