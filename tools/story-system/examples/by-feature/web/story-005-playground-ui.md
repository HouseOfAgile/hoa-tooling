---
id: story-005
priority: high
status: backlog
stack: [frontend, backend]
feature: web
estimated_complexity: medium
---

# Web Playground For Prompt Generation

## User Story
As a **visitor**, I want to **configure prompt and render settings from the homepage and preview/download output**, so that **I can test image generation without using API clients**.

## Business Outcome
Provides the first user-facing interface to the core generation capability.

## Technologies
- Frontend: Next.js form + preview UI
- Backend: `/api/generate` integration

## Acceptance Criteria
- [ ] Homepage has form fields for prompt and generation settings.
- [ ] Form submits to generation API and handles loading/error states.
- [ ] Successful generation shows image preview and download link.
- [ ] Input validation prevents invalid width/height/quality values.
- [ ] UI works on desktop and mobile breakpoints.

## Technical Specifications

### Frontend Details
- Page: `/` in `web/`
- Form fields: prompt, width, height, bgColor, format, quality, transparent, wireframe, fitMode, padding
- Display selected asset/debug summary when available

## Testing Scenarios
```gherkin
Given generation API is available
When I submit a valid prompt and settings
Then I see a rendered preview and download option

Given API returns an error
When form submission completes
Then I see a clear error state without page crash
```

## Validation Tasks
- [ ] Verify form validation for min/max values and required prompt.
- [ ] Verify preview and download for each supported format.
- [ ] Test loading/error behavior with mocked API failure.
- [ ] Run responsive checks on mobile and desktop widths.
- [ ] Add frontend tests for core interactions.

## Resources
- Related Files:
  - `web/`
  - `api/`

## Dependencies
- Depends on: `story-004`
- Blocks: none

## Notes
- Keep UI minimal but production-oriented and clear.

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
