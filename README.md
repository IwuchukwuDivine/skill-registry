# skill-registry

A community-driven registry of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills. Browse, pick, and install — each skill lives in its own folder, ready to drop into any project.

Contributions welcome! See [Contributing](#contributing) below.

## Available Skills

| Skill | Description |
|-------|-------------|
| `nuxt-conventions` | Enforces Nuxt project conventions — directory structure, component patterns, composables, stores, styling, and TypeScript usage. |
| `workflow-orchestration` | Disciplined task execution with planning, verification, and self-improvement loops. Includes subagent delegation, lessons tracking, and staff-engineer-level verification. |

## Install

### Prerequisites

If you don't have a skills folder yet, create one first:

```bash
# Global skills directory
mkdir -p ~/.claude/skills

# Or project-specific
mkdir -p .claude/skills
```

### All skills

```bash
git clone https://github.com/IwuchukwuDivine/skill-registry ~/.claude/skills/skill-registry
```

### A single skill

Copy just the folder you need:

```bash
# Global (available to all projects)
git clone --depth 1 --filter=blob:none --sparse https://github.com/IwuchukwuDivine/skill-registry ~/.claude/skills/skill-registry
cd ~/.claude/skills/skill-registry
git sparse-checkout set <skill-name>
```

```bash
# Project-specific
git clone --depth 1 --filter=blob:none --sparse https://github.com/IwuchukwuDivine/skill-registry .claude/skills/skill-registry
cd .claude/skills/skill-registry
git sparse-checkout set <skill-name>
```

### Examples

```bash
# Install just workflow-orchestration globally
mkdir -p ~/.claude/skills
git clone --depth 1 --filter=blob:none --sparse https://github.com/IwuchukwuDivine/skill-registry ~/.claude/skills/skill-registry
cd ~/.claude/skills/skill-registry
git sparse-checkout set workflow-orchestration
```

## Skill Structure

Every skill follows this layout:

```
<skill-name>/
├── SKILL.md       # Skill metadata and instructions (required)
├── references/    # Reference docs and examples
└── docs/          # Additional documentation (optional)
```

### SKILL.md format

The `SKILL.md` file must start with a YAML frontmatter block:

```yaml
---
name: your-skill-name
description: >
  A clear description of what the skill does and when Claude should use it.
---

# Instructions, rules, and patterns for Claude go here...
```

## Contributing

We'd love your skills in the registry! Here's how to add one:

1. **Fork** this repo
2. **Create a folder** for your skill at the root (e.g. `my-awesome-skill/`)
3. **Add a `SKILL.md`** with the frontmatter format shown above
4. **Add a `references/` folder** with any supporting docs or examples
5. **Open a PR** with:
   - A short description of what the skill does
   - Example use cases
   - Any dependencies or requirements

### Guidelines

- **One skill per folder** — keep skills self-contained
- **Clear naming** — use lowercase kebab-case (`react-patterns`, not `ReactPatterns`)
- **Good descriptions** — the `description` field in `SKILL.md` tells Claude when to activate the skill, so be specific
- **No secrets or credentials** — don't include API keys, tokens, or sensitive data
- **Test your skill** — make sure Claude picks it up and behaves as expected before submitting

### PR checklist

- [ ] Skill folder at repo root with kebab-case name
- [ ] `SKILL.md` with valid YAML frontmatter (`name` + `description`)
- [ ] `references/` folder with at least one reference file
- [ ] No secrets, credentials, or sensitive data
- [ ] Skill tested locally with Claude Code

## License

MIT
