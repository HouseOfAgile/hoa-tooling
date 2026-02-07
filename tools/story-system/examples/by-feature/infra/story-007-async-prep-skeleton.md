---
id: story-007
priority: medium
status: backlog
stack: [backend, infrastructure]
feature: infra
estimated_complexity: medium
---

# Async Preparation Skeleton (Jobs + BullMQ)

## User Story
As a **platform engineer**, I want to **introduce a generation job abstraction and disabled queue skeleton**, so that **the system can shift from sync to async with minimal refactor**.

## Business Outcome
Reduces migration risk when load increases and asynchronous processing becomes necessary.

## Technologies
- Backend: service interface abstraction for generation execution
- Infrastructure: Redis + BullMQ scaffolding behind feature flag

## Acceptance Criteria
- [ ] Introduce generation execution interface usable by sync path.
- [ ] Add queue adapter skeleton (BullMQ) behind disabled config flag.
- [ ] Add compose-ready Redis service (optional profile or disabled by default).
- [ ] No behavior regression in current synchronous flow.
- [ ] Document flip strategy from sync to async.

## Technical Specifications

### Backend Details
- `GenerationExecutor` interface with sync implementation
- Queue implementation stub with no-op or feature-flag gate
- Central config to switch strategy

### Infrastructure Details
- Redis service stub in compose profile
- Env flags for queue enabling and Redis URL

## Testing Scenarios
```gherkin
Given queue mode is disabled
When generation endpoint is called
Then synchronous executor is used

Given queue mode is enabled in non-production test setup
When generation request is submitted
Then request path can route through queue abstraction safely
```

## Validation Tasks
- [ ] Verify sync mode remains default and fully functional.
- [ ] Verify queue flag toggles implementation selection.
- [ ] Verify app boots with queue disabled even if Redis is absent.
- [ ] Verify docs explain rollout strategy and operational caveats.
- [ ] Add tests for executor selection behavior.

## Resources
- Related Files:
  - `api/`
  - `docker-compose.yml`

## Dependencies
- Depends on: `story-004`
- Blocks: future async worker stories

## Notes
- Keep this story as scaffolding only; full async processing is out of scope.

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
