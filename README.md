# ⚠️ Superseded — moved into the team knowledge base

This repo's `CLAUDE.dsci.md` is **replaced by
[`ds-knowledge-base/claude/CLAUDE.dsci.md`](https://github.com/OCHA-DAP/ds-knowledge-base/blob/main/claude/CLAUDE.dsci.md)**,
which every team machine loads directly from its auto-syncing KB clone (one `@import`
line — no copies, no drift). Team skills (`ds-team:*`) ship the same way.

**Set up / migrate in one command** (also removes this repo's legacy config from your
machine automatically):

```bash
bash <(gh api repos/OCHA-DAP/ds-knowledge-base/contents/scripts/setup_team_claude.sh \
       -H "Accept: application/vnd.github.raw")
```

Docs: [ds-knowledge-base/docs/USING.md](https://github.com/OCHA-DAP/ds-knowledge-base/blob/main/docs/USING.md).
This repo is kept read-only for history.
