---
id: story-001
priority: high
status: completed
stack: [backend, database, infrastructure]
feature: user-auth
estimated_complexity: medium
---

# JWT Auth Foundation With Dev Login

## User Story
As an **administrator/developer**, I want to **authenticate with JWT and role guards (plus a dev-only login route)**, so that **secure access control is available from the first milestone while keeping local development fast**.

## Business Outcome
Establishes reliable authentication and authorization early, reducing risk of insecure endpoints and enabling admin workflows for later asset/generation features.

## Technologies
- Backend: NestJS auth module, guards, DTO validation, JWT strategy
- Database: Postgres `users` table with role enum
- Infrastructure: Docker Compose + migration-on-start API container

## Acceptance Criteria
- [x] `POST /api/auth/register` creates a user with role `user` only.
- [x] `POST /api/auth/login` returns a valid JWT and user payload.
- [x] `POST /api/auth/dev-login` works only in `NODE_ENV=development` and requires `DEV_LOGIN_SECRET`.
- [x] `GET /api/auth/admin-check` requires valid JWT and `admin` role.
- [x] Database migration creates `users` table with unique email + role enum.

## Technical Specifications

### API Details
- **Endpoints**:
  - `POST /api/auth/register`
  - `POST /api/auth/login`
  - `POST /api/auth/dev-login`
  - `GET /api/auth/admin-check`
- **Auth**: Bearer JWT (`Authorization: Bearer <token>`)

### Backend Details
- Auth service issues JWT with `sub`, `email`, `role`
- Role protection uses `@Roles(...)` decorator + guard
- Register endpoint prevents privilege escalation to admin role

### Database Changes
- `users` table
  - `id uuid`
  - `email unique`
  - `password_hash`
  - `role enum('admin','user')`
  - `created_at`

## Testing Scenarios
```gherkin
Given no account exists for user@example.com
When I call POST /api/auth/register with valid email/password
Then I receive a JWT response
And the user role in response is "user"

Given I call POST /api/auth/dev-login in production mode
When the request is processed
Then the API returns forbidden

Given I have a non-admin JWT
When I call GET /api/auth/admin-check
Then the API denies access
```

## Validation Tasks
- [ ] Run `docker compose up --build` and confirm API container runs migrations successfully.
- [ ] Register a user and verify role is `user` even if role field is sent in payload.
- [ ] Login with valid credentials and use token against `/api/auth/admin-check` expecting denial for non-admin.
- [ ] Call `/api/auth/dev-login` with valid secret in development and verify admin token is returned.
- [ ] Re-run `/api/auth/dev-login` with wrong secret and verify unauthorized response.

## Resources
- Related Files:
  - `api/src/auth/auth.controller.ts`
  - `api/src/auth/auth.service.ts`
  - `api/src/auth/strategies/jwt.strategy.ts`
  - `api/src/common/guards/roles.guard.ts`
  - `api/src/database/migrations/1700000000000-CreateUsersTable.ts`

## Dependencies
- Depends on: none
- Blocks: `story-002`

## Notes
- Dev-login is intentionally local-only behavior.
- JWT secret must be replaced for non-local environments.

## Definition of Done
- [x] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [x] Documentation updated
- [ ] Deployed to staging
- [ ] QA approved
- [ ] Deployed to production
