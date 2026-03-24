---
summary: 'Claude Code skill for Peekaboo CLI automation'
read_when:
  - Setting up Peekaboo with Claude Code
  - Installing the peekaboo-cli skill
---

# Claude Code Skill for Peekaboo

Peekaboo provides a Claude Code skill that enables AI agents to control macOS desktop automation through natural language commands.

## What is a Skill?

A Claude Code skill is a markdown file that teaches Claude how to use a tool. When you install the `peekaboo-cli` skill, Claude gains the ability to:

- Capture screenshots and analyze UI elements
- Click buttons, type text, and press keys
- Manage windows and applications
- Navigate menus and control the dock
- Perform complex automation workflows

## Installation

### Option 1: Copy to Skills Directory

```bash
# Create skills directory if it doesn't exist
mkdir -p ~/.claude/skills/peekaboo-cli

# Copy the skill file
cp skills/peekaboo-cli/SKILL.md ~/.claude/skills/peekaboo-cli/
```

### Option 2: Symlink (for development)

```bash
# Clone the repository
git clone https://github.com/steipete/Peekaboo.git

# Create a symlink to keep it updated
ln -s $(pwd)/Peekaboo/skills/peekaboo-cli ~/.claude/skills/peekaboo-cli
```

## Prerequisites

Before using the skill, ensure:

1. **Peekaboo CLI is installed**:
   ```bash
   brew install steipete/tap/peekaboo
   ```

2. **Permissions are granted**:
   ```bash
   peekaboo permissions status
   peekaboo permissions grant  # if needed
   ```

## Usage

Once installed, simply ask Claude to perform automation tasks:

```
"Take a screenshot of the current window"
"Click the Submit button in Safari"
"Open Notes and create a new note with 'Hello World'"
"List all running applications"
```

Claude will use the Peekaboo CLI to execute these commands.

## Skill vs MCP Server

Peekaboo offers two integration options:

| Feature | Skill | MCP Server |
|---------|-------|------------|
| Setup complexity | Simple (copy file) | Moderate (config) |
| Direct tool access | CLI commands | Structured tools |
| Best for | CLI workflows | Complex integrations |

The skill is recommended for most Claude Code users. Use the MCP server if you need:
- Structured JSON schemas
- Multiple MCP clients
- Direct tool invocation

## Troubleshooting

### Skill not loading
- Verify the file is at `~/.claude/skills/peekaboo-cli/SKILL.md`
- Restart Claude Code after installation

### Permission errors
```bash
peekaboo permissions status
```

### Element not found
Ask Claude to re-capture the UI first:
```
"Capture the current UI and find the login button"
```

## Files

- `skills/peekaboo-cli/SKILL.md` - The skill definition
- `docs/commands/` - Detailed command documentation

## References

- [Claude Code Skills Documentation](https://docs.claude.com/claude-code/skills)
- [Peekaboo Command Reference](commands/README.md)
