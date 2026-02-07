# Product Backlog

**Last Updated**: 2026-02-07
**Total Stories**: 8
**Completed**: 2
**In Progress**: 0
**Backlog**: 6

---

## Current Sprint (High Priority)

### In Progress
_No stories in progress_

### Completed
- [x] `story-001` JWT Auth Foundation With Dev Login  
  `stories/by-feature/auth/story-001-auth-foundation.md`
- [x] `story-002` Asset Upload And URL Import With Security Controls  
  `stories/by-feature/assets/story-002-asset-ingestion.md`

---

## Next Up

- [ ] `story-101` Automated Validation Suite For Stories 001 And 002  
  `stories/by-feature/testing/story-101-m1-m2-validation-suite.md`
- [ ] `story-003` Ranked Asset Search Endpoint  
  `stories/by-feature/search/story-003-ranked-asset-search.md`
- [ ] `story-004` Synchronous Image Generation Endpoint  
  `stories/by-feature/generation/story-004-sync-generation-endpoint.md`

---

## By Feature Area

### User Auth
- `story-001` (completed)

### Assets
- `story-002` (completed)

### Search
- `story-003` (backlog)

### Generation
- `story-004` (backlog)

### Web
- `story-005` (backlog)

### Admin
- `story-006` (backlog)

### Infra
- `story-007` (backlog)

### Testing
- `story-101` (backlog)

---

## Future Enhancements (Icebox)

- Story for first multi-asset composition mode (v2)
- Story for per-user generation history and quota controls
- Story for background cleanup/retention policy for generated files

---

## Story Statistics

| Priority | Count |
|----------|-------|
| High     | 5     |
| Medium   | 3     |
| Low      | 0     |

| Status      | Count |
|-------------|-------|
| Completed   | 2     |
| In Progress | 0     |
| Backlog     | 6     |

| Complexity | Count |
|------------|-------|
| High       | 2     |
| Medium     | 6     |
| Low        | 0     |

---

## Technical Debt & Infrastructure

- [ ] Add API linting/test framework baseline (Jest + supertest + scripts)
- [ ] Add CI pipeline step for migrations + story validation suite
- [ ] Add smoke test script that validates health/auth/assets flows in docker

---

## Documentation Needs

- [ ] Add API examples collection for auth/assets/search/generate endpoints
- [ ] Add runbook for whitelist and import security settings
- [ ] Add runbook for ImageMagick operational troubleshooting

---

## Notes

- All stories follow the LLM-optimized template in `STORY-TEMPLATE.md`
- Each implementation story should include **Validation Tasks** with explicit checks
- Completed status means code merged; production deployment tracked separately
- Claude workflow commands are defined in `.claude/commands/`

---

**How to Use This Backlog:**

1. **Start a Story**: `/implement-story stories/by-feature/[area]/story-XXX.md`
2. **Track Progress**: update story frontmatter `status`
3. **Validate**: execute Validation Tasks and attach evidence in PR
4. **Review**: run `/review-story` before marking completed
5. **Link Tests**: tie acceptance criteria to automated tests whenever possible

---

> This backlog is a living document. Keep story status and validation evidence current.
