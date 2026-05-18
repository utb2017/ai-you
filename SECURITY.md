# Security

AI You is a public template. There is no AI You server, no shared infrastructure, and no central database. The "security" surface is the template itself: prompts, skills, and docs.

## What we want to know about

Open an issue (or use GitHub's private vulnerability reporting) if you find:

- A prompt or skill in this public repo that **leaks personal data** (names, addresses, anything that looks like a real person's life).
- A prompt or skill that could **trick ChatGPT into writing personal content into the public foundation repo** instead of a user's private repo.
- A prompt or skill that could **cause ChatGPT to leak credentials, tokens, or secrets** into a saved Markdown note.
- A confirmation flow that could be bypassed silently.
- A documentation step that could mislead a non-technical user into making their memory repo **public** by mistake.
- A category or template that nudges ChatGPT to store dangerous data unredacted.

## What this template is **not** responsible for

- The privacy practices of OpenAI / ChatGPT.
- The privacy practices of GitHub.
- What you choose to type into ChatGPT.
- Whether your private repo is actually set to private. That's your responsibility.

## How to report

- Public issue: [github.com/utb2017/ai-you/issues](https://github.com/utb2017/ai-you/issues). Don't paste personal data into the issue body.
- Private report: use GitHub's [private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) on this repo.

## Redaction in archived notes

The archive skill is told to redact:

- passwords
- API keys, auth tokens, secrets
- bank account numbers, card numbers, CVVs
- SSNs / national IDs
- private keys
- exact credentials of any kind
- exact phone numbers
- precise home address details
- anything dangerous if leaked

If you spot a prompt or skill in this repo that **does not** enforce that redaction or that nudges ChatGPT to ignore it, please report it.

## Threat model in plain words

The biggest realistic risks are:

1. A user accidentally creates a **public** memory repo.
2. A user shares a screenshot or video that exposes their private repo's contents.
3. A user pastes credentials into ChatGPT and the model writes them into a note before redacting.
4. A misconfigured connector grants ChatGPT write access to repos beyond `ai-you-memory`.

Mitigations the template recommends:

- The setup docs repeatedly tell users to choose Private when creating their memory repo.
- The skill files explicitly require redaction and explicitly forbid writing personal notes to the public foundation.
- The video demo guide tells creators to use a fake demo repo with invented names instead of their real memory.
- The Quickstart and FAQ tell users to grant ChatGPT access only to the specific private memory repo, not all repos.
