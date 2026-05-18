# Contributing to AI You

Thanks for wanting to help. This is a public foundation, not a personal archive, so contributions need to stay clean and generic.

## Hard rules

1. **No personal data.** Pull requests must not include anyone's real names, real relationships, real medical context, real workplaces, or anything that looks like a private life. Use placeholders like `Sam`, `Mark`, `Iris`, `Dr. Patel`.
2. **No secrets.** No API keys, tokens, credentials, real phone numbers, real addresses.
3. **Public foundation only.** This repo is the template. Don't add user-specific notes here. User notes belong in users' own private repos.
4. **English-first, plain-English.** The audience is non-technical ChatGPT users. Aim for sentences a curious teenager could read.
5. **No new dependencies.** The whole product is Markdown plus prompts. Resist the urge to add tooling.

## Good first contributions

- Improving the wording of `README.md`, `docs/QUICKSTART.md`, `docs/FAQ.md`, or `docs/TROUBLESHOOTING.md` for clarity.
- Adding new categories that are general enough for most users (consider whether you'd want this category in your own life).
- Adding new templates that capture common life situations (decision-making, weekly recap, conversation summary).
- Reporting prompts or skills that produce inconsistent behavior across ChatGPT model surfaces.
- Adding non-English translations of the user-facing docs.

## Things to avoid

- Adding scripts, build tooling, or CI configuration. The product is a copy-pasteable Markdown template; don't gate that on a build.
- Renaming the two commands (`Archive GitHub`, `Recall Context`) without a discussion in an issue first. They are the user-facing surface.
- Adding ChatGPT prompts that bypass the GitHub connector's confirmation modal.
- Adding telemetry, analytics, or third-party links that track users.

## How to propose a change

1. Open an issue describing the change first if it's non-trivial.
2. Fork the repo, make a branch, and make the smallest possible PR.
3. In the PR description, include:
   - what you changed,
   - why,
   - how you tested it (which ChatGPT model, which step you ran).
4. Be patient with reviews. AI You is a side project running on side-project time.

## Style

- Use plain Markdown. No raw HTML, no tables that need rendering tricks.
- Use sentence case for headings.
- Avoid emoji unless it's already in the file.
- Code fences should be language-tagged (`markdown`, `text`, `bash`, etc.).
- Filenames inside the foundation should be lowercase, hyphenated, no spaces.

## License

By contributing, you agree your contributions are licensed under the MIT [LICENSE](LICENSE) of this repo.
