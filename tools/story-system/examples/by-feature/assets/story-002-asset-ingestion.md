---
id: story-002
priority: high
status: completed
stack: [backend, database, infrastructure]
feature: assets
estimated_complexity: high
---

# Asset Upload And URL Import With Security Controls

## User Story
As an **admin**, I want to **upload assets or import them from approved URLs with metadata extraction**, so that **the platform can build a trusted asset library for generation**.

## Business Outcome
Creates a secure ingestion pipeline for image assets and stores normalized metadata required for matching and generation.

## Technologies
- Backend: NestJS assets module, multipart upload, URL import service
- Database: Postgres `assets` + `asset_search_index`
- Other: ImageMagick `identify`, DNS/IP checks for SSRF mitigation

## Acceptance Criteria
- [x] Admin-only `POST /api/assets/upload` stores file on disk and metadata in DB.
- [x] Admin-only `POST /api/assets/import-url` only accepts whitelist hosts.
- [x] URL import rejects IP literals, private/local resolved addresses, and unsafe redirects.
- [x] Metadata (`width`, `height`, `mime`) is extracted via ImageMagick identify.
- [x] `asset_search_index` upserts aggregated text from keywords/tags on asset create.

## Technical Specifications

### API Details
- **Endpoints**:
  - `GET /api/assets`
  - `POST /api/assets/upload`
  - `POST /api/assets/import-url`
- **Upload form fields**:
  - `file` (multipart)
  - `keywords` (`csv` or JSON array string)
  - `tags` (JSON object string)

### Backend Details
- Files stored under `ASSET_STORAGE_DIR` (default `/data/assets`)
- File size cap controlled by `ASSET_IMPORT_MAX_BYTES`
- MIME type allowlist enforced
- URL import flow validates host and re-validates each redirect location
- Metadata extraction uses `spawn('magick', ['identify', ...])` with args array

### Database Changes
- `assets` table with file metadata + keywords/tags
- `asset_search_index` table with `tsvector` and GIN index

## Testing Scenarios
```gherkin
Given I am authenticated as admin
When I upload a valid PNG asset with keywords and tags
Then the API stores the file and returns an asset record with width/height/mime

Given I try to import an asset from a non-whitelisted host
When I call POST /api/assets/import-url
Then the API rejects the request

Given I upload an invalid or oversized file
When the API validates mime/size
Then the request fails with an explicit error
```

## Validation Tasks
- [ ] Obtain admin token via `/api/auth/dev-login` and confirm `/api/assets` requires admin role.
- [ ] Upload one PNG and one JPG; verify files exist in `data/assets/` and DB rows have extracted dimensions.
- [ ] Attempt import from non-whitelisted host and confirm rejection.
- [ ] Attempt import from whitelisted host with redirect to non-whitelisted host and confirm rejection.
- [ ] Verify `asset_search_index` row exists per created asset and contains flattened keywords/tags text.

## Resources
- Related Files:
  - `api/src/assets/assets.controller.ts`
  - `api/src/assets/assets.service.ts`
  - `api/src/assets/asset.entity.ts`
  - `api/src/assets/asset-search-index.entity.ts`
  - `api/src/database/migrations/1700000000100-CreateAssetsAndSearchIndexTables.ts`

## Dependencies
- Depends on: `story-001`
- Blocks: `story-003`

## Notes
- SSRF protections are host-based + DNS/IP checks and redirect validation.
- `data/assets` is a mounted local volume in compose.

## Definition of Done
- [x] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [x] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
