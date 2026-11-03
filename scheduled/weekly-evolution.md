# Weekly self-review — scheduled task prompt

Create a scheduled task (e.g. every Sunday) with this prompt to let MULTITOOL evolve on its own. It never saves anything by itself; it only proposes updates for you to approve.

```
Weekly review of the `multitool` skill, following its "Evolution loop" section with unlazy discipline.

1. Read the current multitool SKILL.md in full.
2. Gather evidence: list installed plugins and search the plugin directory for the cheat-sheet topics
   (video, photo, social, design, docs, research, automation, learning). Find installed plugins that are
   missing from the cheat-sheet and new official plugins that close gaps.
3. If nothing meaningful changed, send one short message "MULTITOOL is up to date" and stop.
4. Otherwise, BEFORE editing write GATES: all sections 0..11 present; new rows are specific;
   frontmatter name=multitool and description <= 1024 chars; one new dated Changelog line with the next
   version; safety section 10 not weakened; file <= ~250 lines. Make the smallest change, verify every gate
   with a script, and only if all pass propose the full new version for approval. Show plugins worth
   installing as install suggestions. Never install or save anything yourself.
```
