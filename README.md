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

### 🚧 In Development

- **markdown-to-powerpoint** - Convert markdown/text to professionally styled PowerPoint presentations with consistent formatting

## Using Skills from This Repository

### Install Individual Skills

**Personal Installation (Available Across All Projects):**
```bash
# Install from this repo
cp -r skills/<skill-name> ~/.claude/skills/
```

**Project-Specific Installation (Shared via Git):**
```bash
# In your project directory
cp -r /path/to/skills-playground/skills/<skill-name> .claude/skills/
git add .claude/skills/<skill-name>
git commit -m "Add <skill-name> skill"
```

### Clone Entire Collection
```bash
# Clone to use as development workspace
git clone https://github.com/YOUR-USERNAME/claude-code-skills-playground.git
cd claude-code-skills-playground

# Symlink to make all skills available globally
ln -s $(pwd)/skills ~/.claude/skills-playground
```

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
