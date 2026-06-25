# Roadmap

## Phase 0: Foundation

- Create project structure and documentation.
- Scaffold Next.js App Router with TypeScript and Tailwind.
- Add shadcn/ui.
- Configure linting, formatting, testing, and environment validation.
- Set up PostgreSQL and Prisma.

## Phase 1: Secure Internal Shell

- Implement Auth.js.
- Add role model and protected routes.
- Build internal dashboard layout and navigation.
- Add basic audit logging for authentication and admin actions.

## Phase 2: Core Records

- Build anonymised client groups CRUD.
- Build opportunities CRUD.
- Add archive flows instead of destructive deletion.
- Add validation and unit tests for core schemas.

## Phase 3: AI-Assisted Matching

- Build AI service boundary.
- Add prompt versioning.
- Generate structured match explanations.
- Store AI metadata.
- Route generated explanations into review queue.

## Phase 4: Human Review

- Build review queue views.
- Support approve, reject, and request changes.
- Store reviewer notes.
- Add audit logs for review decisions.

## Phase 5: Communication And Reporting

- Generate client-ready email drafts.
- Require review before use.
- Add CSV tracking table export.
- Log export activity.

## Phase 6: Transparency And Hardening

- Publish GDPR/AI transparency page.
- Add admin audit log view.
- Review security checklist.
- Add selected integration and end-to-end tests.
- Prepare production deployment checklist.

## Later Enhancements

- Playwright coverage for critical workflows.
- Opportunity import workflow.
- Advanced labour-market analytics.
- Configurable prompt templates.
- Multi-organization support.
- Client-facing transparency materials.
- Named client support only after separate privacy and architecture review.

