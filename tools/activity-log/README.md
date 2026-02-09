# Activity Log

Track AI agent sessions across any project with a standardized, append-only markdown log.

## What This Tool Provides

- A format for recording agent sessions, tasks, and decisions
- A copy-ready template for new projects
- A specification defining update rules and agent integration
- Works with any AI agent (Claude Code, Codex, Cursor, Copilot, etc.)

## Files

- `ACTIVITY-LOG-TEMPLATE.md`: copy-ready template for new projects
- `activity-log-spec.md`: format definition, update rules, and agent setup

## How To Use In Another Project

From your project root:

```bash
cp tooling/hoa-tooling/tools/activity-log/ACTIVITY-LOG-TEMPLATE.md ACTIVITY_LOG.md
echo "ACTIVITY_LOG.md" >> .gitignore
```

Then edit the `{Project Name}` placeholder in `ACTIVITY_LOG.md`.

## Agent Setup

Add the following instruction to your agent's configuration file:

**Claude Code** (`CLAUDE.md`):
```
## Activity Log
- Maintain `ACTIVITY_LOG.md` at the project root
- Update at the end of each session with tasks completed and current state
- See `tooling/hoa-tooling/tools/activity-log/activity-log-spec.md` for format rules
```

**Codex / Cursor / Other** (`AGENTS.md`, `.cursorrules`, etc.):
```
Maintain ACTIVITY_LOG.md at the project root.
At the end of each session, append an entry under today's date.
Format: see tooling/hoa-tooling/tools/activity-log/activity-log-spec.md
```

## Agent Prompt (Recommended)

After adding `hoa-tooling` as submodule, tell your agent:

- `set up the activity log for this project`

## Notes

- `ACTIVITY_LOG.md` is gitignored by default — it's local per-machine tracking.
- This tool is stack-agnostic and agent-agnostic.
