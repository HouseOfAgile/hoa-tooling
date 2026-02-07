# Product Backlog (Example)

> This file is a **template example** showing how to organize a backlog.
> Replace all example stories with your project-specific backlog.

**Last Updated**: YYYY-MM-DD
**Total Stories**: 5
**Completed**: 1
**In Progress**: 1
**Backlog**: 3

---

## Current Sprint (High Priority)

### In Progress
- [ ] `story-102` Implement checkout fraud checks  
  `stories/by-feature/payments/story-102-checkout-fraud-checks.md`

### Completed
- [x] `story-101` User login with MFA  
  `stories/by-feature/auth/story-101-login-mfa.md`

---

## Next Up

- [ ] `story-103` Product search autocomplete
- [ ] `story-104` Order status timeline
- [ ] `story-105` Notification delivery retries

---

## By Feature Area

### Auth
- `story-101` (completed)

### Payments
- `story-102` (in_progress)

### Search
- `story-103` (backlog)

### Orders
- `story-104` (backlog)

### Notifications
- `story-105` (backlog)

---

## Story Statistics

| Priority | Count |
|----------|-------|
| High     | 3     |
| Medium   | 2     |
| Low      | 0     |

| Status      | Count |
|-------------|-------|
| Completed   | 1     |
| In Progress | 1     |
| Backlog     | 3     |

| Complexity | Count |
|------------|-------|
| High       | 1     |
| Medium     | 3     |
| Low        | 1     |

---

## Technical Debt & Infrastructure

- [ ] Add CI check for story validation tasks
- [ ] Add automated traceability from acceptance criteria to tests

---

## Documentation Needs

- [ ] Add contributor guide for story lifecycle
- [ ] Add examples for backend-only and frontend-only stories

---

## How To Use This Example

1. Copy this file to your project as `stories/backlog.md`.
2. Replace example stories with your own IDs/titles/paths.
3. Keep sections and counters updated weekly.
4. Require validation evidence before marking stories completed.
