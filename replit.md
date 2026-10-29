# FairBot Audit

A beginner-friendly browser app for reviewing chatbot responses for preliminary signs of gender, age, disability, and language bias.

## Run & Operate

- FairBot Audit needs no database, API key, or paid service. To run it from a terminal:
  - `pnpm install`
  - `pnpm --filter @workspace/fairbot-audit run dev`
- `pnpm --filter @workspace/fairbot-audit run test` — run the automated bias-rule regression cases
- In Replit, start the `artifacts/fairbot-audit: web` workflow to open the app preview.
- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- The existing API server and database packages are separate workspace scaffolding; FairBot Audit does not use them.

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/fairbot-audit/` — FairBot Audit browser app
- `artifacts/api-server/` and `lib/db/` — separate API and database scaffolding
- `lib/api-spec/` — shared API contract

## Architecture decisions

- The FairBot audit runs locally in the browser with transparent, phrase-based rules; it does not send or persist submitted responses.
- Findings are preliminary indicators for human review, not proof of discrimination.

## Product

- Explains responsible AI and chatbot bias in beginner-friendly terms.
- Checks one response or compares two responses across gender, age, disability, and language categories.
- Shows matched evidence, severity, and improvement suggestions, with CSV export.

## User preferences

_Populate as you build — explicit user instructions worth remembering across sessions._

## Gotchas

_Populate as you build — sharp edges, "always run X before Y" rules._

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
