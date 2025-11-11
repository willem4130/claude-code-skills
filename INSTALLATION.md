# Installation Guide

Quick guide for installing skills from this repository into Claude Code.

## Understanding Skills Location

Claude Code looks for skills in two places:

1. **Global Skills** (`~/.claude/skills/`) - Available in ALL projects
2. **Project Skills** (`.claude/skills/`) - Available in specific project only

## Global Installation (Recommended)

Install once, use everywhere:

```bash
# Copy any skill to global directory
cp -r skills/elite-powerpoint-designer ~/.claude/skills/

# Verify installation
ls -la ~/.claude/skills/elite-powerpoint-designer/
```

**Benefits:**
- Works in any directory
- Available across all projects
- One-time setup
- Automatic activation

## Project Installation

Install for specific project (team sharing):

```bash
# In your project directory
mkdir -p .claude/skills
cp -r /path/to/this-repo/skills/elite-powerpoint-designer .claude/skills/

# Commit to git for team
git add .claude/skills/elite-powerpoint-designer
git commit -m "Add elite PowerPoint designer skill"
git push
```

**Benefits:**
- Team members get skill automatically
- Project-specific customization
- Version controlled with project

## Verifying Installation

Check if Claude can see your skill:

```bash
# For global installation
ls -la ~/.claude/skills/

# For project installation
ls -la .claude/skills/

# Verify SKILL.md exists
cat ~/.claude/skills/elite-powerpoint-designer/SKILL.md | head -5
```

You should see the YAML frontmatter:
```yaml
---
name: elite-powerpoint-designer
description: Create world-class PowerPoint presentations...
---
```

## Using Installed Skills

**Skills are model-invoked** - Claude activates them automatically based on your request.

### Example: Elite PowerPoint Designer

Once installed globally or per-project, just ask naturally:

```
"Create a professional presentation from my-deck.md"
```

Claude will:
1. Detect trigger words ("professional presentation")
2. Load the skill automatically
3. Follow the instructions in SKILL.md
4. Execute the workflow

### Trigger Words

Each skill defines trigger words in its description. For elite-powerpoint-designer:
- "professional presentation"
- "PowerPoint" or "slide deck"
- "world-class"
- "Apple/Microsoft/Google style"
- "pitch deck"

## Installation Status Check

Run this to verify global skills are installed:

```bash
# List all globally installed skills
ls -1 ~/.claude/skills/

# Check if a specific skill is installed
test -d ~/.claude/skills/elite-powerpoint-designer && echo "✅ Installed" || echo "❌ Not installed"
```

## Updating Skills

To update an installed skill:

```bash
# Pull latest from this repo
cd /path/to/claude-code-skills
git pull

# Copy updated skill over existing
cp -r skills/elite-powerpoint-designer ~/.claude/skills/

# Or for project installation
cp -r skills/elite-powerpoint-designer .claude/skills/
```

## Removing Skills

To remove a skill:

```bash
# Remove global skill
rm -rf ~/.claude/skills/elite-powerpoint-designer

# Remove project skill
rm -rf .claude/skills/elite-powerpoint-designer
git add .claude/skills/
git commit -m "Remove elite PowerPoint designer skill"
```

## Troubleshooting

### Skill Not Activating

**Problem**: Claude doesn't seem to use the skill

**Solutions**:
1. Check file location: `ls ~/.claude/skills/[skill-name]/SKILL.md`
2. Use trigger words from skill description
3. Try explicit mention: "Use the [skill-name] skill to..."
4. Restart Claude Code session

### Permission Issues

**Problem**: Script permission denied

**Solution**:
```bash
chmod +x ~/.claude/skills/*/scripts/*.py
chmod +x ~/.claude/skills/*/scripts/*.sh
```

### YAML Syntax Error

**Problem**: Skill not loading due to frontmatter error

**Solution**:
```bash
# Validate YAML
python3 -c "import yaml; yaml.safe_load(open('~/.claude/skills/[skill-name]/SKILL.md').read().split('---')[1])"
```

## Multiple Skills

You can install multiple skills:

```bash
# Install several skills at once
cp -r skills/* ~/.claude/skills/

# List all installed skills
ls -1 ~/.claude/skills/
```

Each skill activates independently based on its trigger words.

## Best Practices

1. **Start Global** - Install globally first to try it out
2. **Move to Project** - Add to project if team needs it
3. **Keep Updated** - Pull latest versions regularly
4. **Check Logs** - Use Claude Code debug mode if issues arise
5. **Read SKILL.md** - Each skill documents its usage

## Quick Reference

```bash
# Install globally (works everywhere)
cp -r skills/elite-powerpoint-designer ~/.claude/skills/

# Install per-project (team sharing)
cp -r skills/elite-powerpoint-designer .claude/skills/

# Verify installation
ls ~/.claude/skills/elite-powerpoint-designer/SKILL.md

# Update skill
git pull && cp -r skills/elite-powerpoint-designer ~/.claude/skills/

# Remove skill
rm -rf ~/.claude/skills/elite-powerpoint-designer
```

## Getting Help

If skills aren't working:

1. Check [Claude Code Skills documentation](https://code.claude.com/docs/en/skills)
2. Review the skill's README.md
3. Open an issue in this repository
4. Verify MCP servers are installed (if required)

## Next Steps

After installation:
1. ✅ Read the skill's README.md for usage examples
2. ✅ Try the examples in the skill's `examples/` folder
3. ✅ Install any required MCP servers
4. ✅ Start using the skill in your projects!
