# claude-harness

A harness project that manages custom skills and configuration files for Claude Code, deploying them to `~/.claude/` via symlinks.

## Setup

```bash
# Clone this repository
git clone <repo-url>
cd claude-harness

# Run the installer in Claude Code
/harness-init

# Set up terminal environment (Ghostty + tmux + yazi + lazygit)
/terminal-init
```

## Project Structure

```
claude-harness/
├── dotfiles/                   # Files deployed to ~/.claude/
│   ├── CLAUDE.md               #   Global instruction file
│   ├── settings.json           #   Claude Code settings
│   ├── statusline-command.sh   #   Status line script (TokyoNight theme)
│   ├── ghostty/config          #   Ghostty terminal config
│   ├── tmux.conf               #   tmux config
│   ├── yazi/yazi.toml          #   yazi file manager config
│   └── lazygit/config.yml      #   lazygit config
├── skills/                     # Skills deployed to ~/.claude/skills/
│   ├── briefing/               #   Morning briefing (calendar, email, weather)
│   ├── calendar/               #   Google Calendar check
│   └── email-check/            #   Gmail inbox check
├── .claude/skills/
│   ├── harness-init/           #   Claude Code config deployer (project-level)
│   └── terminal-init/          #   Terminal environment setup (project-level)
└── CLAUDE.md                   # Project-specific instructions
```

## Skills

| Skill | Description |
|-------|-------------|
| `/harness-init` | Deploy Claude Code config to `~/.claude/` |
| `/terminal-init` | Install and configure Ghostty + tmux + yazi + lazygit |
| `/briefing` | Morning summary of calendar, email, and weather |
| `/calendar` | Check Google Calendar events |
| `/email-check` | Check Gmail inbox |

## Integrations

| Service | Method |
|---------|--------|
| Gmail | Cloud MCP (Anthropic) |
| Google Calendar | Cloud MCP (Anthropic) |
| Slack | Cloud MCP (Anthropic Slack Connector) |

## Development Workflow

1. Edit files in `skills/` or `dotfiles/`
2. Run `/harness-init` to deploy Claude Code config to `~/.claude/`
3. Run `/terminal-init` to set up terminal environment
4. Test in another project

All config files are deployed as symlinks, so a `git pull` updates all environments instantly.

## Secret Management

Never put secrets in `settings.json`. Export API keys via shell profile (`~/.zshrc`, etc.).
