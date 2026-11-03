# Contributing to MULTITOOL

Thanks for helping make MULTITOOL better!

## Good first contributions
- **Cheat-sheet rows:** a task type plus the skills/plugins that handle it best.
- **Ranking rules:** a case where MULTITOOL picked the wrong tool, and the rule that would have fixed it.
- **Bug reports:** what you asked, what it chose, what you expected.

## Rules for changes to `skills/multitool/SKILL.md`
MULTITOOL changes itself using the same discipline it asks of Claude. Every PR must:
1. Keep all sections `0..11` (no regressions).
2. Make new rules specific: name a tool, a trigger and an action. No vague advice.
3. Keep the frontmatter valid: `name: multitool`, description of 1024 characters or fewer.
4. Add one dated line to the Changelog with the next version.
5. Not weaken section 10 (Safety & ethics).
6. Keep the file under ~250 lines. Prune rules that never fire.

## Pull requests
- One focused change per PR.
- Explain the *evidence*: what went wrong or what new tool appeared.
- Be kind in reviews.
