---
name: capture-idea
description: Capture an Idea for a Post into the Idea inbox (IDEAS.md). Use when Stefan tells you an idea, a link or a thought to blog about later, or asks to move, change or drop an Idea.
---

Stefan dictates on his phone, so the session is short. Capture, commit, push, confirm in one line.

## Steps

1. **Sync.** `git fetch origin && git checkout -B capture origin/main` so the commit lands on the latest `main`.
2. **Write each Idea** into `IDEAS.md`, under the section for its destination (format below). One message may carry several Ideas: one entry each. Done when every Idea in the message has an entry.
3. **Commit and push.** Commit with the message `Capture idea: <heading>` (`Capture ideas: <n> new` for several), then `git push origin HEAD:main`.
   - If the push is refused (a cloud session may only be allowed to push its own branch), push the session's branch, open a PR titled `Capture ideas`, and tell Stefan it needs a merge.
4. **Confirm** in one line per Idea: heading and section. Example: "Raycast deep dive → TIL".

## Destination

Pick the section from what Stefan said. When he says nothing, choose and name your choice in the confirmation, so he can correct it.

- **TIL:** something he learned or tried (a tool, a concept).
- **FPE:** a podcast episode.
- **CMT:** a link or tab he wants to mention briefly.
- **Standalone:** anything he calls standalone, or a topic big enough to carry its own argument.

"Make this standalone" (or any move) moves the entry to the other section. It leaves no copy behind.

## Entry format

```markdown
### <Short heading in English>

- **Captured:** YYYY-MM-DD
- **Said:** <Stefan's words, verbatim, including his typos>
- **Links:** <URLs he gave, or "none">
- **Notes:** <only facts he stated beyond the idea itself, e.g. "could become a Talk proposal"; omit the line when empty>
```

Keep **Said** verbatim: the draft later quotes his wording. Look nothing up at capture time. Research happens when the Post is written.
