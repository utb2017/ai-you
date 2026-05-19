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

## Output budget (important)

The user's request is almost always **recall AND respond in one motion** — for example, "Recall Context, then let's talk about my partner." If you spend most of your output on retrieval bullets, the actual response will feel shallow and cold. Treat retrieval as preparation, not the deliverable.

Default budget for the visible reply:

- Retrieval summary: short. 3 to 5 bullets, maximum 8 lines.
- Response to the user's actual question or feeling: the rest of the reply, with depth.

If you find yourself summarizing more than ~8 lines of retrieved context, cut. Prefer cutting retrieval over cutting response depth. The retrieval is there to serve the response, not the other way around.

If the retrieved context is very large, do not list all of it. Pull the 2 to 3 patterns most relevant to the user's current message, and keep the rest in working knowledge silently.

## Venting and emotional context

If the user's message reads like venting, processing, or emotional offload (sentences without a clear question, repeated topic, frustration, sadness, exhaustion):

- The response is **not** a bulleted list of takeaways. The response is a human reply that uses the retrieved context to feel grounded.
- Reflect what is happening before suggesting anything. The archive's job is to make you sound like someone who has been listening.
- A practical next step is still welcome at the end, but it is the close, not the lede.
- Do not over-coach. Do not pivot to a tools list.
- Do not push the user to archive again right now if they are mid-vent. Offer the archive at the end if it fits.

## When recall and response are in one prompt

When the user asks to recall and to respond in the same message ("Recall Context, then let's talk about X"):

- Run the retrieval silently or with minimal narration.
- Open with the short proof-of-retrieval line so the user knows you read the repo.
- Spend the rest of the reply on the actual response.
- Do not narrate "I read these N files" or restate every section. The user already knows you ran retrieval.

## Anti-patterns to avoid

- Replying with retrieval-only output and no real response.
- Pasting bullet summaries of every note you opened.
- Treating an emotional message as an information request.
- Repeating the user's situation back to them in flat list form when they are venting.
- Spending so many tokens on retrieval that the actual reply is two to four short sentences.

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
