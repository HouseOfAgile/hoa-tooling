# Create New User Story

You are helping the user create a new user story following the LLM-optimized format.

## Instructions

1. **Gather Requirements**: Ask the user about:
   - What feature or functionality they want to build
   - Who is the target user (user role)
   - What problem does it solve / what value does it provide
   - Any technical constraints or preferences

2. **Research the Codebase**: Before writing the story:
   - Explore related existing code to understand patterns
   - Check existing stories in `stories/by-feature/` for context
   - Identify the appropriate feature area folder

3. **Determine Story ID**:
   - Check `stories/backlog.md` for the highest existing story ID
   - Use the next sequential number (e.g., if highest is story-115, use story-116)

4. **Create the Story File**:
   - Copy the template from `stories/STORY-TEMPLATE.md`
   - Save to `stories/by-feature/{feature-area}/story-{ID}-{slug}.md`
   - Fill in ALL sections with specific, actionable details

5. **Fill in Each Section**:
   - **Frontmatter**: Set appropriate priority, stack, feature, complexity
   - **User Story**: Clear "As a... I want... so that..." format
   - **Business Outcome**: Why this matters to the business
   - **Technologies**: Specific frameworks, components, services
   - **Acceptance Criteria**: 5-8 specific, testable criteria
   - **Technical Specifications**: API contracts, component structure, database changes
   - **Testing Scenarios**: Gherkin Given/When/Then format
   - **Resources**: Links to related files with line numbers
   - **Dependencies**: Other stories this depends on or blocks
   - **Notes**: Security, performance, accessibility considerations
   - **Definition of Done**: Standard checklist

6. **Update the Backlog**:
   - Add the new story to `stories/backlog.md`
   - Place it in the appropriate section based on priority
   - Update the story counts

7. **Review**: Ensure the story is:
   - Complete (all sections filled)
   - Clear (unambiguous requirements)
   - Testable (verifiable acceptance criteria)
   - Implementable (has all technical details needed)

## Quality Checklist

Before finishing, verify:
- [ ] Story ID is unique and sequential
- [ ] All template sections are filled in
- [ ] Acceptance criteria are specific and testable
- [ ] Technical specs include API contracts where applicable
- [ ] Testing scenarios cover happy path and edge cases
- [ ] Security and accessibility notes are included
- [ ] Story is added to backlog.md
- [ ] File is in correct by-feature subdirectory
