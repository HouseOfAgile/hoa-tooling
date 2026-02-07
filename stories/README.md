# User Stories System

Reusable story framework for AI-assisted and human-assisted implementation.

## Purpose

This `stories/` folder is portable. Copy it into any project and adapt the content to your domain.

## Included Files

- `STORY-TEMPLATE.md`: canonical story format
- `backlog.md`: backlog structure example
- `by-feature/*`: example stories demonstrating expected quality level

## Important

The files in `by-feature/` are examples, not required project scope.

When integrating into a real project:
- keep `STORY-TEMPLATE.md`
- keep backlog structure
- replace example stories with your own

## Quick Usage

1. Create new story from template.
2. Add it to backlog with status and priority.
3. Run review before implementation.
4. Implement with explicit validation tasks.
5. Add/update automated tests mapped to acceptance criteria.

## Minimum Quality Bar For Every Story

- Clear `User Story` and `Business Outcome`
- 5+ testable `Acceptance Criteria`
- `Testing Scenarios` in Given/When/Then
- `Validation Tasks` with executable checks
- explicit dependencies and references

## Recommended Command Workflow

- `/new-story`
- `/review-story stories/by-feature/<area>/story-XXX-<slug>.md`
- `/implement-story stories/by-feature/<area>/story-XXX-<slug>.md`

Command definitions live in `.claude/commands/`.
