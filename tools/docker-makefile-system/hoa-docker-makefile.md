# Tool Definition: `hoa-docker-makefile`

Use this tool to bootstrap a production-oriented Docker Makefile in any project.

The generated Makefile must follow the requirements below.

## Project Context (fill these in first)

- Project name: `<PROJECT_NAME>`
- Main application service name in `docker-compose.yml`: `<SERVICE_NAME>`
- Tech stack: `<STACK>`
- Database type: `<DB_TYPE>` (`postgresql`, `mysql`, `mongodb`, `none`)
- Database service name: `<DB_SERVICE>`
- Package manager: `<PKG_MANAGER>`
- Cache system: `<CACHE_SYSTEM>` (`redis`, `memcached`, `file-based`, `none`)
- Working directory inside container: `<WORKDIR>`
- Docker compose files structure: `<COMPOSE_STRUCTURE>`
- Additional services to manage: `<EXTRA_SERVICES>`

## 1) Environment Management

- Support `dev`, `staging`, `prod`
- Default: `ENV ?= dev`
- Validate ENV at parse time and fail if invalid
- All targets must respect current `ENV`

## 2) Dotenv File Handling

Load dotenv files in Symfony-style precedence (later overrides earlier):

1. `.env`
2. `.env.local`
3. `.env.<ENV>`
4. `.env.<ENV>.local`

Requirements:

- Use `-include` + `$(wildcard ...)`
- Missing files must not fail parsing
- Use `.EXPORT_ALL_VARIABLES:`
- Add `env-init` target:
  - create `.env` from `.env.example` or `.env.dist` if missing
  - print follow-up message

## 3) Docker Compose File Resolution

- Always include base file (`docker-compose.yml` or `docker-compose.base.yml`)
- Include `docker-compose.<ENV>.yml` if present
- Include `docker-compose.local.yml` if present
- Build:

```makefile
COMPOSE = docker compose $(addprefix -f ,$(DC_FILES))
```

- Add `print-dc-cmd` target

## 4) Core Docker Targets

Required targets:

- `up`
- `down`
- `stop`
- `restart`
- `rebuild`
- `logs`
- `logs-<svc>` (pattern target)
- `status`
- `ps`

`up` must print `env-info` first.

## 5) Shell & Exec Access

Required targets:

- `sh`: open interactive shell in main service (`bash` fallback to `sh`)
- `exec`: `make exec CMD="<command>"` with usage message if CMD missing

Also add stack-specific shortcut targets (examples):

- Symfony/PHP: `console`, `composer`, `phpunit`
- Node: `npm`, `yarn`, `pnpm`
- Django: `manage`, `pip`
- Rails: `rails`, `bundle`, `rake`
- Go: `go-run`, `go-test`

Each shortcut should support `CMD="..."`.

## 6) Database Backup & Restore

Required targets:

- `backup-db`
- `restore-db`
- `backup-full`
- `restore-full`
- `list-backups`
- `cleanup-backups`
- `backup-status`
- `backup-help`

Rules:

- Create `data/backups` automatically
- Optional `TAG` support for backup names
- `restore-*` asks confirmation unless `FORCE=1`
- Use compose service names, never container names
- Use DB-type-specific dump/restore commands:
  - PostgreSQL: `pg_dump` + `pg_restore` (`.pgdump`)
  - MySQL: `mysqldump` + `mysql`
  - MongoDB: `mongodump` + `mongorestore`

## 7) Cache Clearing

Required:

- `cache-clear`
- `cache-clear-all` (dev-oriented deep clean)

Implement by stack + cache system:

- Symfony: `php bin/console cache:clear`
- Laravel: artisan cache/config/view clear
- Django: clear cache command or cache dir
- Rails: `rails tmp:clear`
- Node/Next: remove build caches
- Redis cache layer: `redis-cli FLUSHDB`

## 8) Environment Info & Diagnostics

Required targets:

- `env-info`
- `env-check`

`env-info` should show:

- current `ENV`
- loaded dotenv files (in order)
- selected compose files
- key variables (service/db/pkg/cache)
- likely app URL

## 9) Dependencies & Setup

Required targets:

- `install`
- `setup` (`env-init + up + install + db-migrate` if applicable)

## 10) Testing

Required targets:

- `test`
- `test-all`

## 11) Local Overrides

At end of Makefile:

```makefile
-include Makefile.local
```

## 12) Help Target

- Default target must be `help`
- Group targets by section (Docker, Shell & Commands, Database, etc.)
- Header format:

```text
Usage: make [target] [ENV=dev|staging|prod]
```

## Style & Conventions

- Use `.PHONY` for non-file targets
- Use `@` on informative echo/printf lines
- Use clear section headers (`# ==== ... ====`)
- Use `UPPER_SNAKE_CASE` vars
- Show explicit error messages for missing parameters
- Prefer `$(COMPOSE) exec` over `docker exec`
- Never hardcode container names
- Use correct shell chaining in recipes

## Output Expectation From Agent

When asked:

`bootstrap makefile following the tool definition hoa-docker-makefile`

agent should deliver:

1. Root `Makefile` (from this tool definition)
2. Short explanation of detected/assumed context values
3. Notes on stack-specific commands it selected
4. Any manual follow-up required

## Reference Template

Use `tools/docker-makefile-system/Makefile.template` as the base implementation.
