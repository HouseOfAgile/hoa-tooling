# Tool Specification: `activity-log`

Use this tool to maintain a session log in any project. The log records what AI agents did, when, and why — providing continuity across sessions and agents.

## File Location

- **File:** `ACTIVITY_LOG.md` at the project root
- **Gitignored:** Yes — this is local per-machine tracking, not committed

## Format Definition

```markdown
# Activity Log — {Project Name}

> Auto-maintained by AI agents. Tracks sessions, tasks, and decisions.
> This file is gitignored — local per-machine tracking only.

## 2026-02-09

### Session: Short descriptive name
**Agent:** Claude Code / Codex / Cursor / etc.
**Duration:** ~2h (optional)
**Context:** Why this session happened (1-2 lines)

**Tasks:**
- [x] Task that was completed
- [x] Another completed task
- [ ] Task that was started but not finished

**Key decisions:**
- Chose X over Y because Z

**State:** Where things stand now (1-2 lines)
**Pending:** What's left to do
```

## Field Descriptions

| Field | Required | Description |
|-------|----------|-------------|
| Date heading (`## YYYY-MM-DD`) | Yes | Groups sessions by day |
| Session name (`### Session: ...`) | Yes | Short label for the session |
| **Agent** | Yes | Which tool was used (Claude Code, Codex, Cursor, etc.) |
| **Duration** | No | Approximate session length |
| **Context** | Yes | Why the session happened, 1-2 lines |
| **Tasks** | Yes | Checkbox list of completed and incomplete tasks |
| **Key decisions** | No | Significant choices made — only include when non-obvious |
| **State** | No | Where things stand after this session |
| **Pending** | No | What remains to be done |

## Update Rules

1. **Append-only by date.** New sessions go under today's date heading. If today's heading already exists, add the new session below existing ones for that date. Never modify entries from previous dates.

2. **One session = one entry.** Each agent invocation that performs meaningful work gets its own `### Session:` block. Skip logging for trivial interactions (single questions, no file changes).

3. **Update on session end.** Write the log entry at the end of the session, not during. This ensures the entry reflects what actually happened.

4. **Tasks use checkboxes.** Use `- [x]` for completed, `- [ ]` for started-but-incomplete. This gives a quick visual scan of done vs pending.

5. **Keep it concise.** Each field should be 1-3 lines. The log is a reference, not a narrative.

6. **No sensitive data.** Don't log credentials, API keys, or personal information.

## What To Record

**Do log:**
- File changes, refactors, new features
- Bug fixes and what caused them
- Configuration changes (ports, env vars, Docker setup)
- Database operations (migrations, data imports, backups)
- Deployment steps
- Decisions with trade-offs

**Skip logging:**
- Pure Q&A sessions with no file changes
- Reviewing code without modifications
- Reading documentation

## Agent-Specific Setup

### Claude Code

Add to `CLAUDE.md`:

```markdown
## Activity Log
- Maintain `ACTIVITY_LOG.md` at the project root
- Update at the end of each session with tasks completed and current state
- See `tooling/hoa-tooling/tools/activity-log/activity-log-spec.md` for format rules
```

Or add to persistent memory (`MEMORY.md`):

```markdown
## Activity Log Convention
- Each project has `ACTIVITY_LOG.md` (gitignored) tracking agent sessions
- Update it at the end of each session with what was done
- Format: date heading > session name > context + tasks completed + current state + pending items
```

### Codex

Add to `AGENTS.md`:

```markdown
## Activity Log
Maintain ACTIVITY_LOG.md at the project root.
At the end of each session, append an entry under today's date.
Fields: Agent, Context, Tasks (checkboxes), Key decisions, State, Pending.
```

### Cursor

Add to `.cursorrules`:

```
Maintain ACTIVITY_LOG.md at the project root.
At the end of each session, append an entry under today's date with:
- Agent name, context, tasks (checkboxes), key decisions, current state, pending items.
See tooling/hoa-tooling/tools/activity-log/activity-log-spec.md for full format.
```

### GitHub Copilot

Add to `.github/copilot-instructions.md`:

```
Maintain ACTIVITY_LOG.md at the project root.
At the end of each session, append an entry under today's date.
Format: see tooling/hoa-tooling/tools/activity-log/activity-log-spec.md
```

## Example Entry

```markdown
## 2026-02-09

### Session: Worktree setup and code sync
**Agent:** Claude Code
**Context:** Migrated from single directory to two worktrees for live and dev branches.

**Tasks:**
- [x] Stopped stale Docker containers from deleted directory
- [x] Started live stack on port 20080
- [x] Configured dev with parallel ports via .env.dev.local
- [x] Fixed broken submodules in dev (copied from live)
- [x] Backed up live DB and restored to dev
- [ ] Add dev.sondergood.local to /etc/hosts

**Key decisions:**
- Used separate git repos instead of git worktrees for simpler Docker isolation

**State:** Both worktrees running with identical data. Not pushed to remote yet.
**Pending:** Add dev hostname to /etc/hosts, push to remote.
```
