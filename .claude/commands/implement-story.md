# Implement User Story

You are implementing the user story specified by the user: $ARGUMENTS

## Instructions

1. **Read the Story**:
   - Read the story file completely
   - Understand all acceptance criteria
   - Note the technical specifications
   - Check dependencies (ensure prerequisite stories are done)

2. **Read Related Files**:
   - Read all files mentioned in the Resources section
   - Understand existing patterns and code structure
   - Identify where new code should be added

3. **Create Implementation Plan**:
   - Break down the work into specific tasks
   - Order tasks by dependency (what must be done first)
   - Estimate which files need to be created or modified

4. **Implement Each Acceptance Criterion**:
   For each criterion:
   - Write the necessary code
   - Follow existing project patterns
   - Add appropriate error handling
   - Consider edge cases from the testing scenarios

5. **Write Tests**:
   - Create tests based on the Gherkin scenarios
   - Cover happy path and error cases
   - Ensure all acceptance criteria are verified

6. **Code Review Checklist**:
   - [ ] All acceptance criteria implemented
   - [ ] Tests written and passing
   - [ ] Code follows project patterns
   - [ ] No security vulnerabilities (OWASP Top 10)
   - [ ] Accessibility requirements met (WCAG 2.1 AA)
   - [ ] Performance considerations addressed
   - [ ] Error handling is appropriate
   - [ ] No hardcoded values that should be configurable

7. **Update Story Status**:
   - Change status in frontmatter to `in_progress` when starting
   - Change to `completed` when all criteria are met
   - Update `stories/backlog.md` accordingly

8. **Prepare Commit**:
   - Stage all changed files
   - Write a descriptive commit message referencing the story ID
   - Example: "feat(feature-area): implement story-XXX - short description"

## Implementation Guidelines

- **Don't over-engineer**: Only implement what's in the acceptance criteria
- **Follow patterns**: Match existing code style and architecture
- **Test thoroughly**: Every acceptance criterion should have a test
- **Document changes**: Update relevant documentation if needed
- **Ask if unclear**: If requirements are ambiguous, ask before implementing
