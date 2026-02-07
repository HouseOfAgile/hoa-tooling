---
id: story-XXX
priority: [high|medium|low]
status: backlog
stack: [frontend, backend, database, infrastructure]
feature: [feature-area]
estimated_complexity: [low|medium|high]
---

# [Short Story Title]

## User Story
As a **[user role]**, I want to **[action/capability]**, so that **[benefit/value]**.

## Business Outcome
[Describe the desired business outcome and why this story is valuable]

## Technologies
- Frontend: [frameworks, components, hooks]
- Backend: [routes, middleware, services]
- Database: [tables, relationships]
- Other: [Docker, external APIs, libraries]

## Acceptance Criteria
- [ ] [Specific, testable criterion 1]
- [ ] [Specific, testable criterion 2]
- [ ] [Specific, testable criterion 3]
- [ ] [Specific, testable criterion 4]
- [ ] [Specific, testable criterion 5]

## Technical Specifications

### API Details (if applicable)
- **Endpoint**: `[METHOD] /api/[path]`
- **Request**:
  ```json
  {
    "field": "type"
  }
  ```
- **Response**:
  ```json
  {
    "field": "value"
  }
  ```

### Frontend Details (if applicable)
- **Pages**: [pages route]
- **Components**: [Component.tsx]
- **State**: [hooks/store]
- **API**: [API route or direct backend call]

### Backend Details (if applicable)
- **Route**: [routes/file.js]
- **Services**: [service modules]
- **Validation**: [validation rules]

### Database Changes (if applicable)
- **Tables**: [table names]
- **Migrations**: [describe changes]
- **Relationships**: [describe relationships]

## Testing Scenarios
```gherkin
Given [initial context/state]
When [action taken]
Then [expected outcome]
And [additional verification]

Given [another scenario context]
When [action taken]
Then [expected outcome]
```

## Resources
- Mockup/Design: [link or path to design files]
- Related Files:
  - `path/to/file.tsx:line_number`
  - `path/to/file.js:line_number`
- API Documentation: [link to API docs]
- External Dependencies: [links to libraries, services]

## Dependencies
- Depends on: [story-ID, story-ID]
- Blocks: [story-ID]

## Notes
- [Any implementation notes, gotchas, or important context]
- [Security considerations]
- [Performance considerations]
- [Accessibility requirements]
- [Browser compatibility notes]

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
