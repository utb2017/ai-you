# Prompt 1 — Setup AI You

Run this **once**, in a fresh ChatGPT chat, after you have:

1. Logged into GitHub.
2. Connected the GitHub connector / app inside ChatGPT.
3. Used [the public template link](https://github.com/utb2017/ai-you/generate) to create a private repo named `ai-you-memory` in your own GitHub account.

Then paste everything inside the code block below into ChatGPT.

````markdown
Set up AI You for me.

Use the GitHub connector / app.

Read the public foundation repo:
`utb2017/ai-you`

I have already created my private memory repo from the public template at:
`https://github.com/utb2017/ai-you/generate`

Default private repo name:
`ai-you-memory`

If `ai-you-memory` does not exist yet, tell me to open the template link, create a private copy named `ai-you-memory`, and rerun this prompt after I confirm.

Once my private repo exists:

1. Read the two skill files from the public foundation repo:
   - `skills/archive-github/SKILL.md`
   - `skills/recall-context/SKILL.md`
2. Read the two prompt files from the public foundation repo:
   - `prompts/02-archive-github.md`
   - `prompts/03-recall-context.md`
3. Run a GitHub write smoke test in my private repo:
   - Create one file at this path: `logs/smoke-tests/YYYY-MM-DD-HHMM-github-write-smoke-test.md`
   - File body: `AI You GitHub write contact established.`
   - Read the file back from GitHub after writing it.
   - If GitHub asks me to confirm the write, trigger the confirmation modal and wait for me to press Confirm.
   - Do NOT archive any personal content during setup. Only create the smoke-test file.

If memory is available in this ChatGPT session, please remember these two durable commands:

- `Archive GitHub` means save the durable context from the current chat into my private `ai-you-memory` repo using the archive-github skill.
- `Recall Context` means read my private `ai-you-memory` repo and pull the relevant context before answering, using the recall-context skill.

Operating rules to remember:

- My personal notes go only in my private `ai-you-memory` repo, never in the public `utb2017/ai-you` repo.
- Do not ask me to choose folders, filenames, categories, or dates by default. Make the best reasonable choice.
- Redact dangerous secrets (passwords, API keys, exact credentials, SSNs, exact phone numbers, anything dangerous if leaked).
- When archiving, write the main note file first, then update indexes and logs.
- Verify GitHub writes by reading back what was written.

Confirm setup is complete only after:

- the smoke-test file exists in my private repo,
- you have read the smoke-test file back from GitHub,
- you have stored the two commands in memory if memory was available,
- you have summarized in 5 lines or less what is now installed and how I should use it.

If GitHub write actions are not visible in this session:

- First, search/list/discover the GitHub connector or app actions before giving up.
- Look for actions named like: create file, update file, repository contents, save file, commit file, create private GitHub file, or create-or-update-file-contents.
- Do not invent low-level routes that are not exposed.
- If this model surface still cannot write, tell me clearly: "This session does not expose a GitHub write action. Switch to a different ChatGPT model (the standard extended-thinking model has worked best in testing) and rerun this setup prompt." Do NOT claim the repo or GitHub is broken.
````

## What success looks like

When setup finishes correctly, you should see:

- A new file inside your private `ai-you-memory` repo at `logs/smoke-tests/YYYY-MM-DD-HHMM-github-write-smoke-test.md` that says `AI You GitHub write contact established.`
- A short confirmation in the chat that the file was created and read back.
- ChatGPT acknowledging that it remembers the two commands `Archive GitHub` and `Recall Context`.

If any of those three things are missing, setup is not complete. See [`docs/TROUBLESHOOTING.md`](../docs/TROUBLESHOOTING.md).
