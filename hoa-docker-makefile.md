# HOA Docker Makefile Blueprint

This document defines a clean, reusable Makefile pattern for Docker-managed projects.

## Principles

- One command per intent (`up`, `down`, `logs`, `test`, `migrate`)
- Quiet defaults, explicit output when needed
- Works with plain Docker Compose
- Override-friendly via environment variables

## Example Makefile

```makefile
SHELL := /bin/bash
.DEFAULT_GOAL := help

COMPOSE ?= docker compose
COMPOSE_FILE ?= docker-compose.yml
ENV_FILE ?= .env
PROJECT ?= app

.PHONY: help up down restart ps logs build pull test lint fmt migrate seed sh

help:
\t@echo "Targets:"
\t@echo "  up        Start services in background"
\t@echo "  down      Stop services"
\t@echo "  restart   Restart services"
\t@echo "  ps        Show service status"
\t@echo "  logs      Follow logs"
\t@echo "  build     Build images"
\t@echo "  pull      Pull images"
\t@echo "  test      Run tests in app container"
\t@echo "  lint      Run lint in app container"
\t@echo "  fmt       Run format in app container"
\t@echo "  migrate   Run DB migrations in app container"
\t@echo "  seed      Run DB seed in app container"
\t@echo "  sh        Shell into app container"

up:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) up -d --build

down:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) down

restart: down up

ps:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) ps

logs:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) logs -f --tail=200

build:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) build

pull:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) pull

test:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec -T $(PROJECT) npm test

lint:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec -T $(PROJECT) npm run lint

fmt:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec -T $(PROJECT) npm run format

migrate:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec -T $(PROJECT) npm run migration:run

seed:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec -T $(PROJECT) npm run seed

sh:
\t$(COMPOSE) -f $(COMPOSE_FILE) --env-file $(ENV_FILE) exec $(PROJECT) sh
```

## Optional Extensions

- Add `profile-*` targets for local/ci/prod compose profiles.
- Add health checks (`wait-db`, `wait-api`) for CI reliability.
- Add `check` target chaining `lint + test`.

## Team Convention

- Keep Makefile at repository root.
- Keep target names stable across projects.
- If stack differs, adapt command internals but keep target names unchanged.
