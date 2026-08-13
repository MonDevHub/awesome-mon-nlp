# Contributing Guidelines

This list is a curated index, so additions are held to a bar. Read this before opening a pull request.

## What belongs here

A resource is a good fit if it is:

- **Specific to Mon** (`mnw`), or directly usable for Mon NLP (e.g. a multilingual model that explicitly supports Mon, a font that covers the Mon characters, a corpus containing Mon text).
- **Useful** — software people can run, models people can load, data people can use, or research people can cite.
- **Available** — the link works and the resource is publicly accessible. Paywalled or login-only resources are discouraged; if it is the only thing that exists for the job, say so in the pull request and we will decide there.

We avoid: dead or abandoned projects with no working artifacts, pure marketing pages, duplicate entries, and self-promotional links with nothing behind them.

## How to add a resource

1. Fork the repository and create a branch.
2. Add your entry to the most appropriate section, keeping entries within a section ordered sensibly (group related tools together).
3. Match the existing entry format exactly:

   ```
   - [Name](https://example.com) - Description of what it is.
   ```

   - Use the resource's real name as the link text.
   - The description starts with a capital letter and ends with a period.
   - Lead with one sentence saying what the thing *is* rather than why it is good. A short follow-up earns its place if it says where to install or try it, or flags a caveat the reader needs; no entry runs past three sentences.
   - Link to `https://` (not `http://`). Prefer the canonical home (repo, model card, or project site).
4. If you are adding a new section, also add it to the **Contents** table of contents so the list stays navigable.
5. Open a pull request and fill out the checklist in the template.

## Style rules

This list follows the [awesome](https://github.com/sindresorhus/awesome) standard, checked with [`awesome-lint`](https://github.com/sindresorhus/awesome-lint). Run it locally before opening a pull request:

```sh
npx awesome-lint
```

It exits 1 on a clean checkout, before you change anything:

```
  README.md:1:1
  ✖  1:1  The repository should have "awesome" as a GitHub topic       remark-lint:awesome-github
  ✖  1:1  The repository should have "awesome-list" as a GitHub topic  remark-lint:awesome-github

  2 errors
```

Both are repository settings that only a maintainer can change. No edit of yours will clear them, so ignore them. Anything else it reports is yours: capitalization, punctuation, link formatting, the table of contents.

## Code of Conduct

By participating, you agree to abide by the [Code of Conduct](CODE_OF_CONDUCT.md).
