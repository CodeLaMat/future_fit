# MVP Scope

## MVP Goal

Build an internal web application for employment specialists that supports anonymised client-group analysis, opportunity management, AI-assisted match explanations, human review, client-ready drafting, reporting export, transparency, and auditability.

## Included Features

### 1. Authentication And Roles

- Sign in for internal users.
- Role-based access for admin, specialist, and reviewer roles.
- Session handling through Auth.js.
- Protected dashboard routes.

### 2. Dashboard

- Overview of anonymised client groups.
- Opportunity counts and review queue status.
- Recent audit activity summary.
- Clear entry points into core workflows.

### 3. Anonymised Client Groups

- Create, view, edit, and archive anonymised groups.
- Store aggregated education, skill, experience, language, sector, and preference data.
- Prevent storage of direct identifiers in MVP group records.

### 4. Opportunities Database

- Create, view, edit, and archive opportunities.
- Support roles, training programmes, employers, sectors, required skills, locations, work modes, and deadlines.
- Track source and freshness date.

### 5. AI Match Explanation

- Generate a plain-language explanation of why an opportunity may fit a client group.
- Show strengths, gaps, assumptions, and suggested human checks.
- Avoid final scores that imply automated decision-making.

### 6. Human Review Queue

- Queue AI-generated explanations and email drafts for review.
- Allow approve, reject, request changes, and mark as sent outside platform.
- Store reviewer notes and timestamps.

### 7. Client-Ready Email Generator

- Draft email text for specialists to copy into their own email client.
- Use approved group-level context only.
- Require human review before use.

### 8. Tracking Table Export

- Export selected tracking data as CSV.
- Include group, opportunity, review status, dates, and specialist metadata.
- Exclude personal identifiers.

### 9. GDPR/AI Transparency Page

- Explain what data is used.
- Explain what AI does and does not do.
- Explain human review and limitations.
- Provide internal guidance for specialists.

### 10. Audit Logs

- Log authentication events, create/update/archive actions, AI generation requests, review decisions, and exports.
- Make logs visible to admins.

## Out Of Scope For MVP

- Client accounts or self-service features.
- Individual named client records.
- Automated emails.
- Automated eligibility decisions.
- Payments, billing, or marketplace functions.
- Live job-board ingestion.
- Advanced analytics dashboards.
- Multi-tenant customer administration.
- Mobile-native app.

## MVP Quality Bar

- TypeScript strictness should be enabled.
- All server inputs should be validated with Zod.
- Database access should go through Prisma.
- Protected pages should enforce authorization server-side.
- AI output should be reviewable, explainable, and logged.
- Core business rules should have Vitest coverage before production use.

## First Release Assumption

The MVP is deployed for a small internal team using anonymised data. This does not remove the need for GDPR controls, but it narrows the first implementation surface.

