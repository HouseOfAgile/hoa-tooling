# Story System

Reusable story framework for planning, implementing, and validating software work with AI-assisted workflows.

## What This Tool Provides

- Story template with required structure
- Example backlog structure
- Example stories demonstrating quality level
- Command docs for story lifecycle workflows

## Files

- `STORY-TEMPLATE.md`
- `backlog.example.md`
- `examples/by-feature/`
- `commands/new-story.md`
- `commands/review-story.md`
- `commands/implement-story.md`

## How To Use In Another Project

From your project root:

```bash
mkdir -p stories/by-feature
cp tooling/hoa-tooling/tools/story-system/STORY-TEMPLATE.md stories/STORY-TEMPLATE.md
cp tooling/hoa-tooling/tools/story-system/backlog.example.md stories/backlog.md
mkdir -p .claude/commands
cp tooling/hoa-tooling/tools/story-system/commands/*.md .claude/commands/
```

Then:

1. Replace example backlog items with your own stories.
2. Keep acceptance criteria testable.
3. Require `Validation Tasks` in every implementation story.

## Workflow Commands

```text
/new-story
/review-story stories/by-feature/<area>/story-XXX-<slug>.md
/implement-story stories/by-feature/<area>/story-XXX-<slug>.md
```

## Notes

- `examples/by-feature/` is reference content, not required scope.
- This tool is stack-agnostic and intended for any project type.
