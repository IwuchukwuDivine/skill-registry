# skill-registry

A community-driven registry of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills.
Browse, pick, and install — each skill lives in its own folder, ready to drop into Claude's `skills` directory.

Contributions welcome! See [Contributing](#contributing) below.

---

## Available Skills

| Skill | Description |
|---|---|
| `nuxt-conventions` | Enforces Nuxt project conventions — directory structure, component patterns, composables, stores, styling, and TypeScript usage. |
| `workflow-orchestration` | Disciplined task execution with planning, verification, and self-improvement loops. |

---

## How Claude Loads Skills

Claude **only reads folders directly inside the `skills` directory**.

✅ **Correct structure:**
```
.claude/
└── skills/
    ├── nuxt-conventions/
    └── workflow-orchestration/
```

❌ **Incorrect structure** (won't be detected automatically):
```
.claude/
└── skills/
    └── skill-registry/
        ├── nuxt-conventions/
        └── workflow-orchestration/
```

Because of this, you should **clone the registry somewhere else**, then copy the skill folders into the skills directory.

---

## Install

Skills can be installed **globally** (available to all projects) or **per project**.

| Type | Location |
|---|---|
| Global | `~/.claude/skills` |
| Per project | `<project>/.claude/skills` |

### Step 1 — Create the skills folder

**macOS / Linux**
```bash
mkdir -p ~/.claude/skills
```

**Windows (PowerShell)**
```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.claude\skills" | Out-Null
```

---

### Install All Skills

**macOS / Linux**
```bash
git clone https://github.com/IwuchukwuDivine/skill-registry ~/skill-registry
cp -R ~/skill-registry/* ~/.claude/skills/
rm -rf ~/skill-registry
```

**Windows (PowerShell)**
```powershell
git clone https://github.com/IwuchukwuDivine/skill-registry "$HOME\skill-registry"
Copy-Item "$HOME\skill-registry\*" "$HOME\.claude\skills\" -Recurse -Force
Remove-Item "$HOME\skill-registry" -Recurse -Force
```

---

### Install a Single Skill

Uses Git sparse checkout to pull only one skill.

**macOS / Linux**
```bash
git clone --depth 1 --filter=blob:none --sparse https://github.com/IwuchukwuDivine/skill-registry ~/skill-registry
cd ~/skill-registry
git sparse-checkout set workflow-orchestration
cp -R workflow-orchestration ~/.claude/skills/
cd ~ && rm -rf ~/skill-registry
```

**Windows (PowerShell)**
```powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/IwuchukwuDivine/skill-registry "$HOME\skill-registry"
cd "$HOME\skill-registry"
git sparse-checkout set workflow-orchestration
Copy-Item "$HOME\skill-registry\workflow-orchestration" "$HOME\.claude\skills\" -Recurse -Force
cd $HOME
Remove-Item "$HOME\skill-registry" -Recurse -Force
```

---

### Project-Specific Install

To scope skills to a single project, copy them into the project directory instead:

```
my-project/.claude/skills/
```

Claude will load both global and project-level skills automatically.

---

## Skill Structure

Every skill must follow this layout:

```
<skill-name>/
├── SKILL.md       # Required: metadata + instructions
├── references/    # Reference docs and examples
└── docs/          # Optional additional documentation
```

### SKILL.md format

Each `SKILL.md` must begin with YAML frontmatter:

```yaml
---
name: your-skill-name
description: >
  A clear description of what the skill does and when Claude should use it.
---
```

The skill instructions go below the frontmatter.

---

## Contributing

### Steps

1. Fork the repo
2. Create a folder at the repo root: `my-awesome-skill/`
3. Add a `SKILL.md` and a `references/` folder
4. Open a PR

### Guidelines

- One skill per folder
- Use lowercase kebab-case names (e.g. `react-patterns`)
- No secrets or credentials
- Test your skill locally with Claude Code before submitting

---

## License

MIT
