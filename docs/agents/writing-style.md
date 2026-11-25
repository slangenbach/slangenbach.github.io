# Writing style

How Stefan writes Posts. Read it before drafting a Post, and check every draft against it before committing. It grows after each published Post: the retro in the `write-post` skill adds what Stefan changed in the draft.

Sources: the published Posts (`draft: false`) and the About page. Drafts on `main` are partly AI-written, so they are not a source.

## Voice

- **First person, plain and short.** Say a thing once and move on. Most Posts are one to three short paragraphs, or a TL;DR plus a few sections of one to three sentences each.
- **Start from how Stefan found it.** "I first discovered…", "I stumbled upon a gem last week…", "In his recent conversation with…".
- **Concrete details instead of adjectives.** "MacBook Air M2 with 16 RAM", "a super cheap Hetzner server", "Caddy, Docker Compose and Zitadel". Name the tool, the version, the person.
- **Understated praise.** "I really liked this episode", "can only recommend it", "the trailer already looks great", "won't go back". One adjective at most.
- **Honest limits.** Say what didn't work or isn't ready: "they don't yet replace frontier models", "I might just need to invest in beefier hardware".
- **Casual asides.** "AFAIK", "rabbit hole", "took … for a ride", "Stay tuned, this might deserve its own blog post".
- **Glossary terms.** Use the vocabulary in `GLOSSARY.md` when the text names a Series or a Post.

## Shapes

- **Standalone find:** one paragraph (50–120 words), optionally followed by a `{{< video >}}` shortcode.
- **Series Post (TIL, FPE, CMT):**
  - **Title:** the items' names, joined with commas and "and". Example: "Pi, Data-Intensive Applications and OpenCode".
  - **Description:** fixed per Series, for example "This month I learned: March 2026 edition". The templates in `posts/_templates/` hold it.
  - **TL;DR:** bullets, one per item, each with a link. FPE bullets name the guest and show: "[Building Pi][1] with Mario Zechner and Armin Ronacher".
  - **Sections:** one `##` section per item, in TL;DR order. TIL sections run one paragraph, FPE and CMT sections one to three sentences.
  - **Intro (optional):** a Series Post may open with one paragraph on why the Series exists (see FPE April 2026, CMT November 2026).
- **Standalone Post with an argument:** a TL;DR of one or two sentences, then `##` sections. Keep it under 400 words unless Stefan asks for more.
- **Headings:** sentence case, plain nouns: "Quarto", "Small Language Models", "Building OpenCode".
- **Length:** never longer than Stefan's longest Post of the same shape. A short draft is better than a padded one.

## Links

- **Link every tool, person, organisation, book and episode** the first time it appears, usually on the name itself.
- **Reference style:** `[Quarto][1]` in the text, with all definitions at the bottom of the file after two blank lines, numbered in order of first use.
- **Reuse a number** when the same target comes up again, also in the TL;DR.
- **Internal links** point at the other Post's file: `[Cult Repo's][8]` with `[8]: ../cult-repo-movies/index.qmd`.
- **Videos** use the shortcode `{{< video https://www.youtube.com/embed/… >}}` instead of a link.
- **Check every link** before committing: it has to resolve, and it has to say what the sentence claims.

## Facts

- **Every claim comes from Stefan's words** (the Idea and the interview) or from a page the Post links to. When neither covers a sentence, write `TODO(Stefan): <what's missing>` instead of guessing.
- **Opinions are Stefan's.** Write "I liked X because Y" only when he said Y.

## Avoid

These make a draft read as AI-written. Use the plain alternative instead:

- **Em dashes** → commas, colons or two short sentences.
- **Hook openers** that set up a cliché and then claim to break it ("Most About pages follow a predictable script…") → start with how Stefan found the thing.
- **Big words:** "legendary", "pure magic", "game-changing", "blew my mind", "bleeding edge", "delve", "game-changer", "in today's fast-paced world" → a concrete fact.
- **CV clichés:** "bridging the gap", "heavy lifting", "robust", "leverage", "mastering", "fully immersed" → what he actually did.
- **"Not X, it's Y" lines** ("Training a model is easy, but running it in production is where the real challenge lies") → state the point directly.
- **Title-case or chapter-style headings** ("Phase 1: Silicon, Floppies & The Golden Age") → plain sentence-case nouns.
- **Closing summaries** that repeat what the Post already said → end after the last point, or with one aside like "Stay tuned".
