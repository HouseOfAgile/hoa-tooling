# hoa-tooling

Reusable tooling repository for HOA projects.

This repo centralizes project-agnostic delivery tooling so it can be plugged into any stack (Nest, Symfony, Next, Laravel, etc.) with consistent workflows.

## Included

- `stories/`
  - LLM-optimized story system
  - story template
  - backlog structure
  - example feature stories
- `.claude/commands/`
  - `/new-story`
  - `/review-story`
  - `/implement-story`
- `hoa-docker-makefile.md`
  - conventions + clean Docker-oriented Makefile blueprint

## Goal

Keep planning, execution, and validation processes consistent across projects, independent of language/framework.

## Recommended Integration In A Project

### Option A: Git Submodule

```bash
git submodule add <github-url>/hoa-tooling.git tooling/hoa-tooling
git submodule update --init --recursive
```

### Option B: Git Subtree

```bash
git subtree add --prefix tooling/hoa-tooling <github-url>/hoa-tooling.git main --squash
```

## Suggested Usage Pattern

1. Keep upstream tooling in `hoa-tooling`.
2. In each project, consume from `tooling/hoa-tooling`.
3. Copy or reference:
   - `stories/STORY-TEMPLATE.md`
   - `stories/README.md`
   - `.claude/commands/*`
   - `hoa-docker-makefile.md`
4. Project-specific stories live in project repo; shared process stays in tooling repo.

## Versioning

Tag releases when process changes are stable:
- `v0.1.0` initial baseline
- `v0.2.0` testing policy updates
- etc.
