# Fastify-Drizzle-BE

## Intro

This repo is template for Node.js (Drizzle, Postgress) project at Softonix and also this repo includes full stack crash course documentation: [FullStack Course](./FullStackCourse.md)

## Prerequisites

- Node.js >= 22.14.0
- pnpm >= 11 (enable via `corepack enable` — version is pinned in `package.json`)
- Docker + Docker Compose (for local Postgres)

> This project uses **pnpm**. `engine-strict` is on, so a wrong Node/pnpm version is rejected.
> Supply-chain settings live in `pnpm-workspace.yaml` (`ignoreScripts`, `blockExoticSubdeps`,
> `minimumReleaseAge` — packages younger than 1 week are refused).

## Setup

1. Clone the repository:

   ```bash
   git clone <repo-url>
   ```

2. Install dependencies:

   ```bash
   pnpm install
   ```

3. Create `.env` from the template and adjust values (validated by `src/types/EnvSchema.ts` at startup):

   ```bash
   cp .env.example .env
   ```

4. Start local Postgres (reads `PG*` vars from `.env`):

   ```bash
   pnpm local:env
   ```

5. Apply database migrations:

   ```bash
   pnpm db:migration:run
   ```

6. Start the dev server (hot reload via nodemon):

   ```bash
   pnpm local
   ```

   API runs at `http://<HOST>:<PORT>` (e.g. `http://0.0.0.0:3000`).

## Useful commands

| Command | Purpose |
| --- | --- |
| `pnpm local` | Start dev server with hot reload |
| `pnpm local:env` | Start local Postgres via Docker Compose |
| `pnpm build` | Type-check and compile to `dist/` |
| `pnpm production` | Run compiled server from `dist/` |
| `pnpm lint` / `pnpm lint:fix` | Lint (and auto-fix) |
| `pnpm db:migration:generate` | Generate migration from schema changes |
| `pnpm db:migration:run` | Apply pending migrations |
| `pnpm db:migration:studio` | Open Drizzle Studio |

CI/CD installs with a frozen lockfile:

```bash
pnpm install --frozen-lockfile
```

## API docs

Swagger UI available at `/api/documentation` when `NODE_ENV` is `local` or `staging`
(basic auth: `SWAGGER_USER` / `SWAGGER_PWD`). Health check: `GET /api/health`.

# Project structure

```
src/
├── api/                                      # API module
│   ├── api.ts                                # Server setup
│   ├── errors/                               # Error handling
│   ├── hooks/                                # Route hooks
│   ├── plugins/                              # Fastify plugins
│   └── routes/                               # API routes
│       ├── autohooks.ts                      # Hooks for automatic execution
│       ├── entity/                           # Group of routes for entities
│       │   ├── :entityId/                    # Dynamic routes with entityId parameter
│       │   │   └── entity-id.route.ts        # Operations with a specific entity
│       │   └── entities.route.ts             # General operations with entities
│       └── schemas/                          # Validation schemas for routes
│           ├── CreateEntityReqSchema.ts      # Schema for creating an entity
│           ├── GetEntityByIdRespSchema.ts    # Schema for getting an entity
│           └── UpdateEntityReqSchema.ts      # Schema for updating an entity
├── consumers/                                # Message queue consumers
├── controllers/                              # Controllers
│   ├── entity/                               # Entity controllers
│   │   ├── create-entity.ts                  # Create entity
│   │   ├── update-entity.ts                  # Update entity
│   │   ├── delete-entity.ts                  # Delete entity
│   │   ├── get-entity-by-id.ts               # Get entity by ID
│   │   └── get-entities.ts                   # Get entities
├── lambdas/                                  # Lambda functions
├── services/                                 # Services
│   ├── aws/                                  # AWS integrations
│   │   ├── cognito/                          # Authentication
│   │   ├── kms/                              # Encryption
│   │   ├── s3/                               # File storage
│   │   └── sqs/                              # Message queues
│   ├── drizzle/                              # Database
│   ├── env/                                  # Environment configuration
│   ├── sendgrid/                             # Email service
│   └── uuid/                                 # ID generation
├── repos/                                    # Database repositories
├── types/                                    # TypeScript types
```