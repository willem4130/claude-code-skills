# Claude Code Skills Repository

Repository for custom Claude Code skills - modular, reusable capabilities that extend Claude's functionality.

## Project Structure

```
skills-playground/
├── .claude/
│   └── settings.local.json      # Local permissions configuration
├── skills/                       # Production-ready skills
│   └── markdown-to-powerpoint/  # Example: PowerPoint generation skill
│       ├── SKILL.md            # Skill instructions + metadata
│       ├── scripts/            # Skill-specific scripts
│       ├── templates/          # Skill-specific templates
│       └── examples/           # Skill-specific examples
├── templates/                   # Shared templates across skills
├── scripts/                     # Shared utility scripts
├── examples/                    # Global examples and demos
├── docs/                        # Development documentation
├── CLAUDE.md                    # This file
└── README.md                    # User-facing documentation
```

## Organization Rules

**Skills directory (`skills/`) contains production-ready skills:**
- One skill per folder with lowercase-kebab-case naming in `skills/`
- Each skill is self-contained: `SKILL.md` + optional `scripts/`, `templates/`, `examples/`
- Keep skills focused on single capabilities
- Skills can reference shared resources from root `templates/` and `scripts/`

**Shared resources organization:**
- `templates/` - Reusable templates across multiple skills
- `scripts/` - Utility scripts used by multiple skills
- `examples/` - Global examples and demonstrations
- `docs/` - Development guides, patterns, best practices

**SKILL.md requirements:**
```yaml
---
name: skill-name-in-kebab-case
description: What it does AND when to use it (max 1024 chars)
---

# Skill Title
[Markdown instructions that Claude follows]
```

**Script organization:**
- Python/shell scripts in `scripts/` subdirectory
- Scripts run via Bash, only output enters context
- Include validation, parsing, or generation logic
- Make scripts executable with proper shebangs

**Template organization:**
- JSON/markdown templates in `templates/` directory
- Group by type: business, academic, creative
- Document template variables clearly

## Code Quality - Zero Tolerance

**Before committing any skill:**

1. **Validate YAML frontmatter:**
```bash
python -c "import yaml; yaml.safe_load(open('*/SKILL.md').read().split('---')[1])"
```

2. **Test skill execution:**
- Invoke skill in Claude Code session
- Verify Claude recognizes and uses it appropriately
- Test with example inputs from `examples/`

3. **Check script syntax:**
```bash
python -m py_compile scripts/*.py
shellcheck scripts/*.sh
```

Fix ALL errors before committing. Skills with broken syntax will not load.

## Skill Development Workflow

1. Create skill directory: `mkdir my-new-skill`
2. Write `SKILL.md` with clear description and workflow
3. Add supporting scripts/templates if needed
4. Test in Claude Code: Claude should auto-invoke when relevant
5. Iterate based on actual usage
6. Document examples in `examples/` folder

**Testing tips:**
- Use specific trigger words from description
- Test progressive disclosure (does it load only when needed?)
- Verify scripts execute correctly and output is useful
- Check token efficiency (avoid loading unnecessary content)
