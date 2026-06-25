# Security Checklist

## Authentication

- Use Auth.js with secure session settings.
- Require authentication for all dashboard routes.
- Disable inactive users.
- Protect admin-only pages.
- Use strong provider configuration and secret management.

## Authorization

- Define roles explicitly.
- Check authorization server-side.
- Avoid relying only on hidden UI.
- Add tests for role helper functions.
- Log denied sensitive actions where appropriate.

## Data Protection

- Use anonymised group-level data for MVP.
- Prevent direct identifiers in client group records.
- Validate all inputs with Zod.
- Limit free-text fields.
- Avoid storing unnecessary AI prompts or raw vendor responses.

## Database

- Use Prisma for database access.
- Apply migrations through controlled process.
- Use least-privilege database credentials.
- Back up production data.
- Avoid destructive deletes for business records.

## Secrets

- Store secrets in environment variables.
- Never commit `.env` files.
- Rotate secrets if exposed.
- Keep AI provider keys server-side only.

## AI Security

- Keep AI calls server-side.
- Use prompt templates with versioning.
- Strip or reject direct identifiers before AI calls.
- Validate structured AI responses.
- Log generation metadata.
- Require review for client-impacting outputs.

## Exports

- Export anonymised data only.
- Log export requests.
- Include requesting user, timestamp, filters, and row count.
- Avoid exporting hidden internal notes unless explicitly selected and authorized.

## Audit Logs

- Log create, update, archive, AI generation, review decision, and export events.
- Keep audit logs append-only.
- Restrict audit log access to admins.
- Define retention period before production.

## Web Security

- Use secure headers.
- Protect against CSRF where relevant.
- Sanitize rendered user-generated text.
- Avoid exposing stack traces in production.
- Rate-limit sensitive endpoints if exposed beyond the internal network.

## Production Readiness

- Complete security review.
- Complete privacy review.
- Configure monitoring and error reporting.
- Document incident response.
- Run dependency audit.
- Run accessibility checks for core screens.

