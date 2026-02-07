---
id: story-004
priority: high
status: backlog
stack: [backend, database, infrastructure]
feature: generation
estimated_complexity: high
---

# Synchronous Image Generation Endpoint

## User Story
As a **user**, I want to **submit a prompt and settings and receive a generated image immediately**, so that **I can iterate quickly in the playground**.

## Business Outcome
Delivers the core product value with minimal infrastructure complexity before introducing asynchronous workers.

## Technologies
- Backend: NestJS generation endpoint/service
- Rendering: ImageMagick via safe `spawn(args)`
- Database: `generations` table + selected asset linkage
- Storage: `/data/generated` mounted volume

## Acceptance Criteria
- [ ] `POST /api/generate` executes synchronously and returns generation result.
- [ ] Endpoint selects best asset using ranked search result.
- [ ] Renderer supports `png`, `jpg`, `webp` with quality rules for lossy formats.
- [ ] Supports settings: width, height, bgColor, transparent, wireframe, fitMode, padding.
- [ ] Generation record is persisted with prompt/settings/selected asset/output/status/error.

## Technical Specifications

### API Details
- **Endpoint**: `POST /api/generate`
- **Request**: prompt + settings object
- **Response**: generation id, output URL/path, selected asset info, score details

### Backend Details
- Reuse `story-003` search service for best asset selection
- Render with contain/cover behavior and centered placement
- Optional wireframe overlay with bbox/crosshair and unobtrusive label
- Persist output filename and mime type

### Database Changes
- Add `generations` table (status success/fail, error nullable)

## Testing Scenarios
```gherkin
Given a matching asset exists for the prompt
When I call POST /api/generate with valid settings
Then generation succeeds and output file is created
And generation metadata is persisted

Given no asset matches prompt
When generation is requested
Then API returns controlled failure and logs generation as failed
```

## Validation Tasks
- [ ] Generate PNG/JPG/WebP outputs and verify mime + dimensions.
- [ ] Validate quality impacts JPG/WebP file size and output remains valid.
- [ ] Verify transparent mode behavior for supported formats.
- [ ] Verify wireframe overlay visibility and bbox accuracy.
- [ ] Add automated API/integration tests for success + failure paths.

## Resources
- Related Files:
  - `api/src/assets/assets.service.ts`
  - `api/Dockerfile`

## Dependencies
- Depends on: `story-003`
- Blocks: `story-005`, `story-006`, `story-007`

## Notes
- Keep the service interface ready for async upgrade, but execution remains sync in this story.

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
