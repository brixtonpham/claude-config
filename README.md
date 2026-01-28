# Claude Code Configuration

Personal Claude Code configuration with custom agents, skills, and principles.

## Quick Setup

### 1. Clone Repository

**Fresh install (SSH):**
```bash
git clone git@github.com:brixtonpham/claude-config.git ~/.claude
```

**Fresh install (HTTPS):**
```bash
git clone https://github.com/brixtonpham/claude-config.git ~/.claude
```

**If ~/.claude already exists (chezmoi-style):**
```bash
cd ~/.claude
git init
git remote add origin https://github.com/brixtonpham/claude-config.git
git fetch origin
git reset --hard origin/main
git branch --set-upstream-to=origin/main main
```

**Future updates:**
```bash
cd ~/.claude && git pull
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
