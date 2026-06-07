# Contributing Guidelines

Thank you for helping grow the Mon NLP ecosystem. This list is a curated index, so additions are held to a quality bar. Please read these guidelines before opening a pull request.

## What belongs here

A resource is a good fit if it is:

- **Specific to Mon** (`mnw`), or directly usable for Mon NLP (e.g. a multilingual model that explicitly supports Mon, a font that covers the Mon characters, a corpus containing Mon text).
- **Useful** — software people can run, models people can load, data people can use, or research people can cite.
- **Available** — the link works and the resource is publicly accessible. Paywalled or login-only resources are discouraged unless there is no open alternative.

We avoid: dead or abandoned projects with no working artifacts, pure marketing pages, duplicate entries, and self-promotional links with no substance behind them.

## How to add a resource

1. Fork the repository and create a branch.
2. Add your entry to the most appropriate section, keeping entries within a section ordered sensibly (group related tools together).
3. Match the existing entry format exactly:

   ```
   - [Name](https://example.com) - Description of what it is.
   ```

   - Use the resource's real name as the link text.
   - The description starts with a capital letter and ends with a period.
   - Keep it to one factual sentence — say what the thing *is*, not why it is great.
   - Link to `https://` (not `http://`). Prefer the canonical home (repo, model card, or project site).
4. If you are adding a new section, also add it to the **Contents** table of contents so the list stays navigable.
5. Open a pull request and fill out the checklist in the template.

## Style rules (enforced by CI)

This list follows the [awesome](https://github.com/sindresorhus/awesome) standard and is checked automatically with [`awesome-lint`](https://github.com/sindresorhus/awesome-lint) and a link checker on every pull request. Before submitting, you can run the same checks locally:

```sh
npx awesome-lint
```

Pull requests must pass CI before they can be merged. If the linter reports an issue, fix the formatting it points to — the rules cover capitalization, punctuation, link formatting, the table of contents, and dead links.

## Code of Conduct

By participating, you agree to abide by the [Code of Conduct](CODE_OF_CONDUCT.md).
