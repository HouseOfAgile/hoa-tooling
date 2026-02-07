---
id: story-003
priority: high
status: backlog
stack: [backend, database]
feature: search
estimated_complexity: medium
---

# Ranked Asset Search Endpoint

## User Story
As a **generation service**, I want to **search assets by prompt with ranking**, so that **the best candidate can be selected quickly for rendering**.

## Business Outcome
Improves output relevance and generation speed using Postgres full-text search without introducing external search infrastructure.

## Technologies
- Backend: NestJS assets/search endpoint
- Database: Postgres `asset_search_index` with GIN `tsvector` index

## Acceptance Criteria
- [ ] `GET /api/assets/search?prompt=...` returns ranked matches.
- [ ] Query uses `plainto_tsquery('simple', normalizedPrompt)` and `ts_rank`.
- [ ] Response includes score and linked asset metadata.
- [ ] Empty or invalid prompts return validation error.
- [ ] Ranking is deterministic for equal inputs and same dataset.

## Technical Specifications

### API Details
- **Endpoint**: `GET /api/assets/search?prompt={text}&limit={n}`
- **Response**:
  - `results[]` with `asset`, `rank`, and optional debug terms

### Backend Details
- Normalize prompt (trim/lowercase/basic cleanup)
- Query `asset_search_index` joined with `assets`
- Default `limit` (e.g. 10), max limit guard

## Testing Scenarios
```gherkin
Given assets with different keyword/tag relevance
When I call GET /api/assets/search with a prompt
Then the API returns assets sorted by descending rank

Given prompt is missing or blank
When search is requested
Then the API returns validation error
```

## Validation Tasks
- [ ] Seed at least 5 assets with varied keywords/tags and rebuild search index.
- [ ] Run search for 3 prompts and verify top result relevance manually.
- [ ] Confirm SQL plan uses GIN index (EXPLAIN).
- [ ] Verify empty prompt and excessive limit are rejected.
- [ ] Add automated tests mapping each acceptance criterion.

## Resources
- Related Files:
  - `api/src/assets/assets.service.ts`
  - `api/src/database/migrations/1700000000100-CreateAssetsAndSearchIndexTables.ts`

## Dependencies
- Depends on: `story-002`
- Blocks: `story-004`

## Notes
- Keep implementation Postgres-native; avoid introducing Elasticsearch/Meilisearch for v1.

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
