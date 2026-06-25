# Architecture

## Stack

- Next.js App Router
- TypeScript
- Tailwind CSS
- shadcn/ui
- PostgreSQL
- Prisma
- Auth.js
- Zod
- Vitest
- Playwright later

## Application Shape

FutureFit Careers should use a modular feature structure. Route files live in `app`, reusable UI in `components`, feature-specific logic in `features`, and shared infrastructure in `lib`.

Recommended top-level folders:

- `app`: Next.js App Router routes, layouts, route handlers, and server actions.
- `components`: shared presentational components and shadcn/ui components.
- `features`: domain-specific UI, services, schemas, and tests.
- `lib`: cross-cutting infrastructure for auth, database, AI, security, and GDPR helpers.
- `prisma`: Prisma schema, migrations, and seed scripts.
- `types`: shared TypeScript types.
- `config`: application configuration.
- `tests`: shared test utilities and integration tests.
- `docs`: product, architecture, security, and AI guidance.
- `scripts`: local maintenance scripts.

## Route Groups

Suggested route groups:

- `app/(auth)`: sign-in and authentication pages.
- `app/(dashboard)`: authenticated specialist workspace.
- `app/api`: route handlers for APIs that cannot be expressed as server actions.

Initial dashboard routes:

- `/dashboard`
- `/client-groups`
- `/opportunities`
- `/review-queue`
- `/email-generator`
- `/tracking-export`
- `/transparency`

## Feature Modules

Each feature module should keep related code close together:

- `schemas.ts`: Zod schemas for inputs and forms.
- `types.ts`: feature-level TypeScript types.
- `queries.ts`: read operations.
- `mutations.ts`: write operations.
- `components/`: feature-specific UI.
- `__tests__/`: feature-specific tests when useful.

Example:

```text
features/client-groups/
  schemas.ts
  queries.ts
  mutations.ts
  components/
```

## Data Access

- Prisma is the only database access layer.
- Server components, server actions, and route handlers may call feature queries and mutations.
- Client components should not directly access Prisma or secrets.
- All write inputs must be validated with Zod before persistence.

## Authentication And Authorization

- Auth.js handles authentication and sessions.
- Authorization checks should happen server-side.
- Roles should be explicit and narrow:
  - `ADMIN`: user management, settings, audit logs.
  - `SPECIALIST`: client groups, opportunities, draft generation, exports.
  - `REVIEWER`: review queue actions and reviewer notes.

## AI Integration Boundary

AI calls should be isolated in `lib/ai` and feature services.

AI requests must:

- Use anonymised group data.
- Include purpose-specific prompts.
- Avoid personal data.
- Return structured output where possible.
- Save generation metadata for auditability.
- Route client-impacting outputs to human review.

## UI Direction

The MVP is an internal operational tool. The interface should be quiet, dense, readable, and fast to scan.

Recommended UI patterns:

- Left navigation for core sections.
- Data tables for client groups, opportunities, review items, and audit logs.
- Forms with clear validation states.
- Status badges for review and lifecycle state.
- Plain-language AI explanations.

## Testing Strategy

Initial test focus:

- Zod validation.
- Role and authorization helpers.
- GDPR guardrail helpers.
- AI prompt input sanitisation.
- Export formatting.

Later:

- Playwright coverage for critical authenticated workflows.
- Accessibility checks for forms, tables, and review screens.

