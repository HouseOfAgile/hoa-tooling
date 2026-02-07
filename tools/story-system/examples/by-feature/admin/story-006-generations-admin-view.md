---
id: story-006
priority: medium
status: backlog
stack: [frontend, backend]
feature: admin
estimated_complexity: medium
---

# Admin Generations Monitoring Views

## User Story
As an **admin**, I want to **view generations list and detail records**, so that **I can monitor output quality and diagnose failures quickly**.

## Business Outcome
Improves operational visibility and debugging efficiency for generation pipeline behavior.

## Technologies
- Frontend: React Admin resources/pages
- Backend: generations list/detail endpoints

## Acceptance Criteria
- [ ] Admin list page shows generations with status, prompt, format, created_at.
- [ ] Detail view shows settings, selected asset, score details, output preview.
- [ ] Failed generations show error message clearly.
- [ ] List supports pagination and sorting.
- [ ] Access restricted to admin role.

## Technical Specifications

### Frontend Details
- Add React Admin resource for generations
- Columns: id, status, prompt excerpt, selected asset id, created_at
- Detail: settings JSON + output image + error block

### Backend Details
- Add authenticated admin endpoints for generation list/detail

## Testing Scenarios
```gherkin
Given I am an authenticated admin
When I open generations list
Then I can browse recent generation records

Given a generation failed
When I open its detail page
Then I can see failure reason and settings used
```

## Validation Tasks
- [ ] Verify admin-only access control for generation list/detail routes.
- [ ] Verify pagination/sorting consistency across multiple pages.
- [ ] Verify output preview rendering for successful generations.
- [ ] Verify failed generation details include error context.
- [ ] Add UI/API tests for list/detail behavior.

## Resources
- Related Files:
  - `admin/`
  - `api/`

## Dependencies
- Depends on: `story-004`
- Blocks: none

## Notes
- Prioritize inspectability over visual polish.

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
