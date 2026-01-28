# Claude Code Configuration

Personal Claude Code configuration with custom agents, skills, and principles.

## Quick Setup

### 1. Clone Repository

**Fresh install:**
```bash
git clone git@github.com:brixtonpham/claude-config.git ~/.claude
```

**If ~/.claude already exists:**
```bash
# Backup existing config (optional)
mv ~/.claude ~/.claude.bak

# Clone
git clone git@github.com:brixtonpham/claude-config.git ~/.claude
```

**Or overwrite without backup:**
```bash
rm -rf ~/.claude && git clone git@github.com:brixtonpham/claude-config.git ~/.claude
```

### 2. Install Claude Code
```bash
npm install -g @anthropic-ai/claude-code
```

### 3. Authenticate
```bash
claude login
```

### 4. Create Local Settings (if needed)
Create `~/.claude/settings.local.json` for machine-specific settings:
```json
{
  "env": {
    "ANTHROPIC_API_KEY": "your-key-here"
  }
}
```

### 5. Verify Setup
```bash
claude --version
claude
```

## Structure

| Directory | Purpose |
|-----------|---------|
| `CLAUDE.md` | Global instructions |
| `principles/` | Core principles (delegation, SE, cognitive) |
| `agents/` | 34 custom agents |
| `skills/` | 78+ skills |
| `hooks/` | Session & activation hooks |
| `commands/` | Custom commands |

## Notes
- `settings.local.json` is gitignored - create manually on each machine
- Run `claude` to verify agents/skills are loaded
