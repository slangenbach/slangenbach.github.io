---
name: write-post
description: Turn Ideas from the Idea inbox (IDEAS.md) into a published Post - interview Stefan, draft, run the retro on his edits, publish. Use for the mid-month and end-of-month routine runs, when Stefan asks to write a Post, or when he says he is done polishing a draft.
---

The pipeline has four phases. A routine run starts at phase 1. When Stefan says he is done with a draft (in any words; ask "Done polishing, so should I run the retro and prepare the merge?" when unsure), start at phase 4 on that Post's PR.

Read `docs/agents/writing-style.md` and `docs/agents/tooling.md` before phase 3.

## 1. Pick the Ideas

- **Mid-month run (15th):** every Idea under `## Standalone`, plus a one-line status per Series: "TIL: 3 Ideas, FPE: 1, CMT: 0".
- **End-of-month run (28th):** every Idea under `## TIL`, `## FPE` and `## CMT`, one Post per Series for the current month.
- **Stefan asks for a Post:** the Ideas he names.

When a run finds nothing due, end with one line ("Nothing due this run") and stop.

Show Stefan the picked Ideas grouped by Post, in one short message. He may drop, defer or move Ideas ("make this standalone" moves it to `## Standalone` for the next mid-month run). Done when he has confirmed the grouping.

## 2. Interview

Ask per Post, all of its Ideas in one round:

- **TIL:** What did you learn? Why does it matter to you? Which link should a reader start with?
- **FPE:** Which episode, with link? Why did it stick? One takeaway?
- **CMT:** Which tabs, and one line on each?
- **Standalone:** run the `grilling` skill on the Post's argument. Where it isn't installed, grill by hand: numbered rounds of questions, each with your recommended answer, until the argument, its evidence and its examples are settled.

Do the research yourself (official sites, episode pages, docs) and ask Stefan only for what research can't answer: his experience and his opinion. Done when every Idea has an answer to each question, or Stefan dropped it.

## 3. Draft

1. **Branch** from the latest `main`: `post/<slug>`.
2. **File:** if `posts/<slug>/index.qmd` exists (Series drafts often do), extend it and keep what's there. Otherwise `task new-post POST_TYPE=<type> POST_NAME=<slug>`, or copy the template by hand without Task.
3. **Write the full draft** to `writing-style.md`: every section filled, every link checked, `TODO(Stefan): …` only where neither his answers nor a source covers a sentence. Keep `draft: true` and the date as it is.
4. **Check** the draft against every item under "Avoid" in the style guide, and fix what you find.
5. **Commit** the draft alone as `Draft <slug>`: phase 4 diffs against this commit. Push and open a PR, with the TODOs listed in its body.

Tell Stefan the PR is ready to polish and stop. He pushes his edits to the branch.

## 4. Retro and publish

1. **Retro.** Diff the `Draft <slug>` commit against the branch head for the Post's file. For every change Stefan made, ask what rule would have produced his version, and add the rules that will recur to `writing-style.md` (one-off fact fixes are not rules). Commit as `Update writing style from <slug>`. Done when every hunk of his diff is either covered by a rule or judged a one-off.
2. **Style fixes.** Check Stefan's final text against "Avoid" and fix any hits and obvious typos, changing nothing else. Commit as `Style fixes for <slug>`. Skip the commit when there is nothing to fix.
3. **Publish commit.** Set `draft: false` and `date` to today, and remove the used Ideas from `IDEAS.md`. Commit as `Publish <slug>`.
4. **Ask Stefan to approve the PR**, listing the three commits in one line each. Merge only after his yes: `gh pr merge --squash --delete-branch`. The push to `main` deploys the site.
