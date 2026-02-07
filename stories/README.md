# User Stories - LLM-Optimized Format

This directory contains user stories structured in an LLM-optimized format designed to work seamlessly with Claude Code and other AI development tools.

## Quick Start

### Creating a New Story
```bash
# Option 1: Use the slash command (if configured):
/new-story

# Option 2: Manually:
# 1. Copy stories/STORY-TEMPLATE.md
# 2. Create new file in stories/by-feature/{area}/story-{ID}-{slug}.md
# 3. Fill in all sections
# 4. Add to stories/backlog.md
```

### Implementing a Story
```bash
# Use the slash command:
/implement-story stories/by-feature/feature-area/story-010-feature-name.md

# Claude will:
# 1. Read and understand the story
# 2. Create an implementation plan
# 3. Implement all acceptance criteria
# 4. Write tests
# 5. Review the code
# 6. Help you commit changes
```

### Reviewing a Story
```bash
# Use the slash command:
/review-story stories/by-feature/feature-area/story-010-feature-name.md

# Claude will provide feedback on:
# - Completeness
# - Clarity
# - Testability
# - Security and accessibility
# - Suggestions for improvement
```

## Directory Structure

```
stories/
├── README.md                      # This file
├── STORY-TEMPLATE.md              # Template for new stories
├── backlog.md                     # Master backlog with all stories
└── by-feature/                    # Stories organized by feature area
    ├── user-auth/
    │   ├── story-001-user-login.md
    │   └── ...
    ├── feature-area-2/
    │   └── ...
    └── feature-area-n/
        └── ...
```

## Story File Structure

Each story follows this structure:

```markdown
---
id: story-XXX                      # Unique ID
priority: high|medium|low          # Priority level
status: backlog|in_progress|completed  # Current status
stack: [frontend, backend, ...]    # Tech stack components
feature: feature-area              # Feature area
estimated_complexity: low|medium|high  # Effort estimate
---

# Story Title

## User Story
As a [user role], I want [action], so that [benefit].

## Business Outcome
Clear statement of business value

## Technologies
Specific tech stack components involved

## Acceptance Criteria
- [ ] Testable criterion 1
- [ ] Testable criterion 2
...

## Technical Specifications
Detailed implementation specs (API contracts, components, etc.)

## Testing Scenarios
Gherkin-style Given/When/Then scenarios

## Resources
Links to related files, mockups, docs

## Dependencies
Links to prerequisite stories

## Notes
Important context, security, accessibility, performance notes

## Definition of Done
Completion checklist
```

## Why This Format?

This format is optimized for AI-assisted development:

1. **Structured Sections**: LLMs process separated sections (technologies, requirements, specs) better than free-form text
2. **Frontmatter Metadata**: Easy for AI to parse and filter stories
3. **File References**: Claude can navigate to related files with specific line numbers
4. **Gherkin Scenarios**: Clear, testable specifications
5. **Explicit Tech Stack**: Claude knows exactly what frameworks/tools to use
6. **Comprehensive Context**: All information needed for implementation in one place

## Claude Code Slash Commands

Create custom slash commands in `.claude/commands/` to streamline working with stories:

### `/new-story`
Creates a new user story by:
- Gathering requirements from you
- Researching the codebase for context
- Filling in the template with all sections
- Adding the story to the backlog

### `/implement-story`
Implements a story by:
- Reading the story and related files
- Creating a detailed todo list
- Implementing all acceptance criteria
- Writing tests based on scenarios
- Reviewing code for security/accessibility
- Helping with git commit

### `/review-story`
Reviews a story for:
- Completeness (all sections filled)
- Clarity (unambiguous requirements)
- Testability (verifiable criteria)
- Security (OWASP Top 10 considerations)
- Accessibility (WCAG 2.1 AA compliance)
- Consistency (follows project patterns)

## Command Sources

The story system is paired with command definitions stored in:

- `.claude/commands/new-story.md`
- `.claude/commands/implement-story.md`
- `.claude/commands/review-story.md`

These files are the operational instructions for Claude-based workflows.  
When updating story format or backlog workflow, update these command files in the same change to keep behavior aligned.

## Story + Testing Policy

For this repository, every implementation story must include:

- `Acceptance Criteria` with explicit, testable outcomes
- `Testing Scenarios` in Gherkin format
- `Validation Tasks` with concrete command/evidence checks

Recommended flow:

1. Create/refine story (`/new-story`)
2. Review quality/security/testability (`/review-story`)
3. Implement and close criteria/tasks (`/implement-story`)
4. Add/maintain automated tests that map to story criteria

## Best Practices

### Writing Stories

0. **Include Validation Tasks**:
   - Add a dedicated `## Validation Tasks` section in every story
   - Keep tasks executable and evidence-based (command + expected result)
   - Add at least one negative/security test task when relevant

1. **Be Specific**: Vague requirements lead to confusion
   - Bad: "Make it fast"
   - Good: "Load list in under 2 seconds for 1000 items"

2. **Include Examples**: Show don't tell
   - API request/response examples
   - UI mockups or wireframes
   - Data model examples

3. **Think About Edge Cases**:
   - What if the API fails?
   - What if the list is empty?
   - What if the user has no permissions?
   - What about mobile vs desktop?

4. **Security First**:
   - Input validation rules
   - Authentication/authorization requirements
   - Rate limiting needs
   - Data privacy concerns

5. **Accessibility Always**:
   - WCAG 2.1 AA compliance
   - Keyboard navigation
   - Screen reader support
   - Color contrast

### Implementing Stories

1. **Read First**: Understand the full story before coding
2. **Check Dependencies**: Ensure prerequisite stories are done
3. **Follow the Plan**: Use task tracking to monitor progress
4. **Test Thoroughly**: Verify all acceptance criteria and close all `Validation Tasks`
5. **Review Your Work**: Check for security, performance, accessibility
6. **Update Docs**: Keep documentation in sync

### Managing the Backlog

1. **Regular Grooming**: Review and refine stories weekly
2. **Update Priorities**: Adjust based on business needs
3. **Mark Completed**: Update status when stories are done
4. **Track Dependencies**: Update when stories become unblocked
5. **Add New Stories**: Capture ideas as they emerge

## Story Lifecycle

1. **Backlog**: Story is written but not started
   - Status: `backlog`
   - Refined and ready to implement

2. **In Progress**: Story is being actively worked on
   - Status: `in_progress`
   - One person/pair working on it

3. **Completed**: Story is done and deployed
   - Status: `completed`
   - All acceptance criteria met
   - Code reviewed and merged
   - Tests passing
   - Deployed to production

## Estimating Complexity

- **Low (1-2 days)**:
  - Simple UI changes
  - Minor bug fixes
  - Configuration updates

- **Medium (3-5 days)**:
  - New pages with standard CRUD
  - API endpoints with moderate logic
  - Integration with external services

- **High (5+ days)**:
  - Complex features with multiple components
  - Major refactoring
  - Performance optimizations
  - New architectural patterns

## Tips for Success

1. **Start Small**: Begin with high-priority, low-complexity stories
2. **Iterate**: Refine stories based on implementation learnings
3. **Document Decisions**: Add notes about tradeoffs and alternatives
4. **Keep Current**: Update the backlog as priorities shift
5. **Learn from Completed Stories**: Use them as examples for new ones
6. **Use the Tools**: Leverage the Claude Code slash commands
7. **Communicate**: Share story progress with the team

---

**Remember**: Good stories lead to good implementations. Take time to write clear, complete stories and the coding will be much smoother!
