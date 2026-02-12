# Log Activity

You are logging the current session's activity to `ACTIVITY_LOG.md` at the project root.

## Instructions

1. **Read the Spec**: Read `tooling/hoa-tooling/tools/activity-log/activity-log-spec.md` for format rules.

2. **Check If File Exists**: If `ACTIVITY_LOG.md` doesn't exist yet:
   - Copy from `tooling/hoa-tooling/tools/activity-log/ACTIVITY-LOG-TEMPLATE.md`
   - Replace `{Project Name}` with the actual project name
   - Ensure `ACTIVITY_LOG.md` is in `.gitignore`

3. **Review What Happened This Session**: Gather context by examining:
   - Recent git diff (staged + unstaged changes)
   - Recently modified files
   - Any tasks completed or in progress (check todo lists, task trackers)
   - Key decisions made during the conversation

4. **Compose the Entry** following the spec format:
   ```markdown
   ## YYYY-MM-DD

   ### Session: Short descriptive name
   **Agent:** Claude Code
   **Context:** Why this session happened (1-2 lines)

   **Tasks:**
   - [x] Completed tasks
   - [ ] Started but unfinished tasks

   **Key decisions:**
   - Only include if non-obvious choices were made

   **State:** Where things stand now
   **Pending:** What's left to do
   ```

5. **Append to ACTIVITY_LOG.md**:
   - If today's date heading (`## YYYY-MM-DD`) already exists, add the new session block below existing sessions for that date
   - If today's date doesn't exist, add a new date heading
   - Never modify entries from previous dates
   - Place new dates at the bottom of the file

6. **Keep It Concise**: Each field should be 1-3 lines. The log is a reference, not a narrative.

## Rules

- **Append-only**: Never edit previous session entries
- **Skip trivial sessions**: Don't log pure Q&A with no file changes
- **No sensitive data**: Never log credentials, API keys, or personal information
- **One entry per session**: Each meaningful work session gets one block
