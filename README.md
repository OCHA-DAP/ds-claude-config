# Claude config for Data Science team

## Editing

Edit the `CLAUDE.dsci.md` directly, and commit directly in `main`.

## Syncing

To keep this file synced on your machine:

1. Add this to your `~/.zshrc`:

```
curl -s https://raw.githubusercontent.com/OCHA-DAP/ds-claude-config/main/CLAUDE.dsci.md > ~/.claude/CLAUDE.dsci.md
```

This will then grab the most recent version of this config file everytime you open a new terminal. Or, simply run the command in the terminal to sync manually.

2. Make sure you have the following line in your personal `~/.claude/CLAUDE.md` file:

```
@~/.claude/CLAUDE.dsci.md
```

This will import the team `CLAUDE.dsci.md` config.
