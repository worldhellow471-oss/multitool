# Installing MULTITOOL

MULTITOOL ships as two skills that work together:

| Skill | Why you need it |
|---|---|
| `multitool` | The router: picks the best skills, plugins, connectors and models for every task |
| `unlazy` | Completion gates that MULTITOOL uses for big jobs and for its own self-updates |

Install **both**. Setup takes about 2 minutes.

---

## Option A: Claude apps (claude.ai, desktop, mobile)

**Requirements:** a Claude plan with Skills enabled, and *Code execution and file creation* turned on in **Settings → Capabilities**.

1. **Download the ready-made skill packages** from the [`dist/`](dist) folder:
   - [`multitool-skill.zip`](dist/multitool-skill.zip)
   - [`unlazy-skill.zip`](dist/unlazy-skill.zip)

   *(Or click **Code → Download ZIP** at the top of this page and find them in `dist/`.)*
2. Open Claude and go to **Settings → Capabilities → Skills**.
3. Click **Upload skill**, choose `multitool-skill.zip`, and confirm.
4. Repeat for `unlazy-skill.zip`.
5. Make sure both skills are switched **on**.

> Don't unzip the files. Upload the `.zip` as it is. Each zip contains one folder with a `SKILL.md` inside.

---

## Option B: Claude Code, one command (recommended)

Inside Claude Code run:
```
/plugin marketplace add worldhellow471-oss/multitool
/plugin install multitool@multitool
```
This installs both `multitool` and `unlazy`. To update later, run `/plugin marketplace update multitool`.

Alternatively, with the open [skills CLI](https://github.com/vercel-labs/skills):
```bash
npx skills add worldhellow471-oss/multitool
```

---

## Option C: Claude Code, manual copy

**Personal install (every project):**

macOS / Linux:
```bash
git clone https://github.com/worldhellow471-oss/multitool.git
mkdir -p ~/.claude/skills
cp -r multitool/skills/multitool multitool/skills/unlazy ~/.claude/skills/
```

Windows (PowerShell):
```powershell
git clone https://github.com/worldhellow471-oss/multitool.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse multitool\skills\multitool, multitool\skills\unlazy "$HOME\.claude\skills\"
```

**Project-only install:** copy the two folders into `.claude/skills/` inside your project instead.

Restart Claude Code (or start a new session) so it picks up the skills.

---

## How to use

```
/multitool <your task>
```

Type `/multitool`, a space, then your task in plain words.

## Check that it works

Start a new chat and type:

```
/multitool what can you do with my current setup?
```

You should get a short summary of your installed tools, grouped by task type. Then try a real task:

```
/multitool make a 3-slide deck about the benefits of sleep
```

MULTITOOL should name the tool it picked and why in one line, and then start working.

---

## Optional: weekly self-review

This lets MULTITOOL suggest improvements to itself once a week. It never saves anything without your approval.

- **Claude apps:** ask Claude *"create a weekly scheduled task on Sundays"* and paste the prompt from [`scheduled/weekly-evolution.md`](scheduled/weekly-evolution.md).
- **Claude Code:** set up a scheduled task or cron job that runs Claude with the same prompt.

When an update is ready, you'll see a skill-update card. Review it and click **Save** if you like it.

---

## Updating

- **Claude apps:** download the new zips from `dist/` and upload them again. The new version replaces the old one.
- **Claude Code:**
  ```bash
  cd multitool && git pull
  cp -r skills/multitool skills/unlazy ~/.claude/skills/
  ```

See [CHANGELOG.md](CHANGELOG.md) for what changed.

## Uninstalling

- **Claude apps:** Settings → Capabilities → Skills → remove `multitool` and `unlazy`.
- **Claude Code:** delete `~/.claude/skills/multitool` and `~/.claude/skills/unlazy`.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| MULTITOOL never triggers | Call it explicitly with `/multitool …`, and check that the skill is switched on |
| "Skill upload failed" | Upload the zip from `dist/` as it is. The zip must contain one folder with `SKILL.md` |
| It suggests a plugin you already have | Make sure the plugin is enabled, then start a new chat |
| A plugin it picks "isn't working" | Some plugins need their own sign-in or local programs (Bun, Python, Git). MULTITOOL tells you what's missing |
| Gates or self-updates don't run | Install `unlazy` too. MULTITOOL depends on it |

Still stuck? [Open an issue](../../issues) and include what you asked, what MULTITOOL chose, and what you expected.
