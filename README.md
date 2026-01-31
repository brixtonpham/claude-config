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

### 3. CLI Proxy Setup (Required)

This config uses a **local proxy** to route Claude API calls through custom endpoints.

**Environment variables in `settings.json`:**
```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "sk-dummy",
    "ANTHROPIC_BASE_URL": "http://127.0.0.1:8317",
    "ANTHROPIC_MODEL": "gemini-claude-opus-4-5-thinking"
  }
}
```

**What this does:**
- Routes all API calls to `localhost:8317` (your proxy server)
- Uses custom model names that the proxy translates
- `sk-dummy` is a placeholder - the proxy handles real auth

**You need:**
1. A running proxy server on port `8317` (e.g., [ProxyPal](https://github.com/brixtonpham/proxypal) or similar)
2. The proxy must handle Anthropic API format and route to your preferred backend

**Without proxy:** If you want to use Anthropic directly, update `settings.json`:
```json
{
  "env": {
    "ANTHROPIC_API_KEY": "sk-ant-your-real-key",
    "ANTHROPIC_BASE_URL": "https://api.anthropic.com"
  }
}
```

### 4. Create Local Settings (Optional)

Create `~/.claude/settings.local.json` for machine-specific overrides:
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

## Key Features

### WebSearch Hook
WebSearch is routed through Gemini CLI (bypasses US-only restriction):
```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "WebSearch",
      "hooks": [{
        "command": "node $HOME/.claude/web_search/index.cjs"
      }]
    }]
  }
}
```

### Model Routing
Custom model aliases in proxy:
| Alias | Routes To |
|-------|-----------|
| `gemini-claude-opus-4-5-thinking` | Your preferred Opus model |
| `gemini-claude-sonnet-4-5-thinking` | Your preferred Sonnet model |

## Structure

| Directory | Purpose |
|-----------|---------|
| `CLAUDE.md` | Global instructions |
| `principles/` | Core principles (delegation, SE, cognitive) |
| `agents/` | 34 custom agents |
| `skills/` | 78+ skills |
| `hooks/` | Session & activation hooks |
| `commands/` | Custom commands |
| `web_search/` | WebSearch hook implementation |

## Notes
- `settings.local.json` is gitignored - create manually on each machine
- `plugins/local/` contains machine-specific plugin configs (gitignored)
- Run `claude` to verify agents/skills are loaded
