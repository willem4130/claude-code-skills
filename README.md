# Claude Code Skills Playground

Development workspace and collection of custom skills for [Claude Code](https://code.claude.com) - extending Claude's capabilities with modular, reusable workflows.

## Repository Structure

```
skills-playground/
├── skills/              # Production-ready skills
│   └── <skill-name>/   # Each skill in its own directory
├── templates/          # Shared templates across skills
├── scripts/            # Shared utility scripts
├── examples/           # Example inputs/outputs
├── docs/               # Development guides and references
└── .claude/            # Local Claude Code configuration
```

## What are Skills?

Skills are model-invoked capabilities that Claude autonomously uses based on context. They consist of:
- **SKILL.md**: Instructions with YAML frontmatter (name + description)
- **scripts/**: Python/shell scripts for complex operations
- **templates/**: Reusable templates and patterns
- **examples/**: Sample inputs and outputs

## Available Skills

### ✅ Production Ready

#### **elite-powerpoint-designer** - World-Class Presentation Design
Create Apple/Microsoft/Google-level presentations with professional design, consistent branding, and sophisticated animations.

**Features:**
- 5 professional brand styles (Tech Keynote, Corporate, Creative, Financial Elite, Startup Pitch)
- Intelligent markdown-to-template mapping
- Professional animation system with timing guidelines
- Complete design systems (typography, colors, spacing, effects)
- Content analyzer for automatic style detection
- 25+ slide template mappings

**Perfect for:** Product launches, investor pitches, business reports, keynotes, and any presentation requiring world-class design quality.

[View Documentation →](./skills/elite-powerpoint-designer/)

## Installation

### Quick Install (Global - Recommended)

Install once, use everywhere:

```bash
# Clone this repository
git clone https://github.com/willem4130/claude-code-skills.git
cd claude-code-skills

# Install globally (works in all projects)
cp -r skills/elite-powerpoint-designer ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/elite-powerpoint-designer/
```

Done! The skill is now available in all your Claude Code sessions.

### Alternative: Project-Specific Installation

Install for a specific project (team sharing):

```bash
# In your project directory
mkdir -p .claude/skills
cp -r /path/to/claude-code-skills/skills/elite-powerpoint-designer .claude/skills/

# Commit to git so team gets it
git add .claude/skills/elite-powerpoint-designer
git commit -m "Add elite PowerPoint designer skill"
```

**📖 See [INSTALLATION.md](./INSTALLATION.md) for detailed setup instructions and troubleshooting.**

## Developing Your Own Skills

This repository is set up as a development playground. Here's the workflow:

### 1. Create Skill Structure
```bash
mkdir skills/my-skill-name
cd skills/my-skill-name
touch SKILL.md
mkdir -p scripts templates examples
```

### 2. Write SKILL.md
```yaml
---
name: my-skill-name
description: What it does AND when Claude should use it (trigger words)
---

# My Skill

[Instructions for Claude to follow]
```

### 3. Develop & Test
- Use `scripts/` for shared utilities
- Use `templates/` for reusable templates
- Add examples to `examples/`
- Test by using trigger words from description
- Iterate based on Claude's usage

### 4. Publish
- Move completed skills to `skills/` directory
- Push to GitHub
- Share with the community!

See [CLAUDE.md](./CLAUDE.md) for detailed development guidelines and quality checks.

## Contributing

Skills that would be useful to others are welcome! Please:
- Follow the structure guidelines in CLAUDE.md
- Test thoroughly before submitting
- Include examples in the skill's `examples/` folder
- Document any dependencies or setup requirements

## License

MIT - Feel free to use and modify for your projects.

## Resources

- [Claude Code Documentation](https://code.claude.com/docs)
- [Skills Documentation](https://code.claude.com/docs/en/skills)
- [MCP Integration](https://code.claude.com/docs/en/mcp)
