# Contributing to skill-registry

Thanks for contributing! This registry grows through community submissions.

## Adding a Skill

1. **Fork** this repo and create a new branch
2. **Create a folder** at the repo root using lowercase kebab-case (e.g. `my-skill-name/`)
3. **Add the required files:**

```
my-skill-name/
├── SKILL.md         # Required — metadata + instructions
├── references/      # Required — supporting docs or examples
└── docs/            # Optional — additional documentation
```

4. **Open a Pull Request**

## SKILL.md Format

Your `SKILL.md` must start with YAML frontmatter:

```yaml
---
name: my-skill-name
description: >
  A clear description of what the skill does and when Claude should use it.
  Be specific — this is how Claude decides when to activate your skill.
---

# Your instructions, rules, and patterns for Claude go below...
```

- `name` — must match your folder name
- `description` — tell Claude **what** the skill does and **when** to use it

## Guidelines

- **One skill per folder** — keep skills self-contained
- **Kebab-case naming** — `react-patterns`, not `ReactPatterns` or `react_patterns`
- **Be specific in descriptions** — vague descriptions mean Claude won't know when to use your skill
- **Include references** — add example files, docs, or patterns in `references/` so Claude has context
- **No secrets or credentials** — never include API keys, tokens, or sensitive data
- **Test before submitting** — install your skill locally and verify Claude picks it up and behaves correctly

## Testing Locally

1. Copy your skill folder into `.claude/skills/` (global or project-level)
2. Start a Claude Code session
3. Trigger a prompt that should activate your skill
4. Verify Claude follows your instructions

## PR Checklist

Before submitting, make sure:

- [ ] Skill folder at repo root with kebab-case name
- [ ] `SKILL.md` with valid YAML frontmatter (`name` + `description`)
- [ ] `name` in frontmatter matches the folder name
- [ ] `references/` folder with at least one reference file
- [ ] No secrets, credentials, or sensitive data
- [ ] Tested locally with Claude Code

## Questions?

Open an [issue](https://github.com/IwuchukwuDivine/skill-registry/issues) if you have questions or need help with your submission.
