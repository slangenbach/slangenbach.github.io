# Tooling

The site is a [Quarto](https://quarto.org/docs/guide/) website, driven through [Task](https://taskfile.dev/). Reach for a built-in Quarto feature before anything custom: ADR 0001 rules out custom EJS templates, Lua filters and JavaScript.

## Task

`taskfile.yml` is the source of truth for commands (`task --list`). The ones Posts need:

- `task new-post POST_TYPE=<default|til|fpe|cmt> POST_NAME=<slug>` copies the template from `posts/_templates/` into `posts/<slug>/index.qmd`. It does nothing when the folder already exists.
- `task new-talk TALK_NAME=<slug>` does the same for a Talk, from `talks/_templates/talk.qmd`.
- `task preview` runs `quarto preview` to check a page locally. In a session without Quarto, run `quarto render` where it is installed, or leave the check to Stefan.

Series Post slugs follow `<series>-<YYYY-MM>`: `til-2026-11`, `fpe-2026-06`, `cmt-2026-11`.

## Quarto features to use

- **Front matter:** `title`, `description` (shown in the blog listing), `date` (`YYYY-MM-DD`), `categories`, `draft`.
- **Categories** are Topics and Series slugs: `this-month-i-learned`, `favorite-podcast-episodes`, `closing-my-tabs`, plus lowercase Topics like `ai` or `documentary`.
- **Drafts:** `draft: true`. `_quarto.yml` sets `draft-mode: unlinked`, so a draft on `main` is rendered and reachable by its URL, only left out of listings, the feed and the sitemap.
- **Videos:** `{{< video <url> >}}` shortcode.
- **Callouts:** `::: {.callout-note}` (also `tip`, `warning`, `important`, `caution`).
- **Emoji:** add `from: markdown+emoji` to the front matter, then write `:shrug:`.
- **Links between Posts:** point at the file, `../<slug>/index.qmd`. Quarto rewrites it to the page URL.
- **Listing:** `blog.qmd` lists `posts/` by date, newest first, with categories and the RSS feed. New Posts appear there automatically.

Look anything else up in the [Quarto guide](https://quarto.org/docs/guide/) before building it yourself.

## Publishing

A push to `main` runs `.github/workflows/deploy.yml`, which renders the site and publishes it to the `gh-pages` branch. `IDEAS.md` and other `.md` files don't render: `_quarto.yml` only renders `.qmd` files.
