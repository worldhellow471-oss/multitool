---
name: multitool-fast
description: MULTITOOL on Haiku for quick, simple tasks (rewrite, list, captions, rename, short answer) to save limits. Claude Code only. Use when the user types /multitool-fast <task>.
model: haiku
disable-model-invocation: true
argument-hint: <quick task>
---

Run the task with the `multitool` skill's rules for an S/M task, on this fast model.
If the task turns out to need hard reasoning, research or a high-stakes result, say in one line: "This needs a stronger model: run /multitool-deep <task>" and stop before doing low-quality work.
