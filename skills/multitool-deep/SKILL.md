---
name: multitool-deep
description: MULTITOOL on Opus for hard tasks (architecture, tricky bug, big research, final high-stakes review). Claude Code only. Use when the user types /multitool-deep <task>.
model: opus
disable-model-invocation: true
argument-hint: <hard task>
---

Run the task with the `multitool` skill's rules on this strong model.
Spend the strong model on thinking and checking; hand bulky mechanical parts to the `mt-fast` agent and ordinary production parts to `mt-worker` so Opus limits go only where they matter.
