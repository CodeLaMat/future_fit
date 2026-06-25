# Database Model

## Modelling Principles

- Store anonymised group-level data in the MVP.
- Avoid direct identifiers such as names, personal email addresses, phone numbers, addresses, social security numbers, or free-text personal histories.
- Prefer controlled fields, arrays, and short structured notes over unrestricted free text.
- Track lifecycle state instead of deleting business records immediately.
- Keep audit logs append-only.

## Proposed Core Entities

### User

Internal platform user.

Fields:

- `id`
- `name`
- `email`
- `role`
- `status`
- `createdAt`
- `updatedAt`

### ClientGroup

An anonymised group of clients with shared labour-market transition needs.

Fields:

- `id`
- `title`
- `summary`
- `educationLevels`
- `fieldsOfStudy`
- `skills`
- `languages`
- `experienceAreas`
- `preferredSectors`
- `preferredLocations`
- `workModes`
- `constraints`
- `groupSizeRange`
- `status`
- `createdById`
- `createdAt`
- `updatedAt`
- `archivedAt`

### Opportunity

A role, training path, programme, employer need, or other labour-market opportunity.

Fields:

- `id`
- `title`
- `description`
- `organization`
- `sector`
- `location`
- `workMode`
- `requiredSkills`
- `beneficialSkills`
- `educationRequirements`
- `languageRequirements`
- `sourceUrl`
- `sourceName`
- `freshnessDate`
- `deadline`
- `status`
- `createdById`
- `createdAt`
- `updatedAt`
- `archivedAt`

### MatchExplanation

AI-supported group-to-opportunity explanation.

Fields:

- `id`
- `clientGroupId`
- `opportunityId`
- `summary`
- `strengths`
- `gaps`
- `assumptions`
- `recommendedHumanChecks`
- `aiModel`
- `promptVersion`
- `status`
- `createdById`
- `createdAt`
- `updatedAt`

### ReviewItem

Human review workflow item.

Fields:

- `id`
- `type`
- `status`
- `matchExplanationId`
- `emailDraftId`
- `assignedToId`
- `reviewedById`
- `reviewerNotes`
- `decision`
- `createdAt`
- `updatedAt`
- `reviewedAt`

### EmailDraft

Client-ready email draft for specialist review and copy-out.

Fields:

- `id`
- `clientGroupId`
- `opportunityId`
- `matchExplanationId`
- `subject`
- `body`
- `tone`
- `status`
- `createdById`
- `createdAt`
- `updatedAt`

### ExportJob

Record of tracking table exports.

Fields:

- `id`
- `requestedById`
- `filters`
- `rowCount`
- `format`
- `createdAt`

### AuditLog

Append-only record of important activity.

Fields:

- `id`
- `actorUserId`
- `action`
- `entityType`
- `entityId`
- `metadata`
- `ipAddress`
- `userAgent`
- `createdAt`

## Suggested Enums

```text
UserRole: ADMIN, SPECIALIST, REVIEWER
UserStatus: ACTIVE, DISABLED
RecordStatus: ACTIVE, ARCHIVED
ReviewStatus: PENDING, APPROVED, REJECTED, CHANGES_REQUESTED
ReviewItemType: MATCH_EXPLANATION, EMAIL_DRAFT
WorkMode: ONSITE, HYBRID, REMOTE, FLEXIBLE
EmailDraftStatus: DRAFT, IN_REVIEW, APPROVED, REJECTED, USED_OUTSIDE_PLATFORM
MatchExplanationStatus: DRAFT, IN_REVIEW, APPROVED, REJECTED
ExportFormat: CSV
```

## Relationship Summary

- A `User` creates many `ClientGroup` records.
- A `User` creates many `Opportunity` records.
- A `ClientGroup` has many `MatchExplanation` records.
- An `Opportunity` has many `MatchExplanation` records.
- A `MatchExplanation` may have one or more `ReviewItem` records.
- A `MatchExplanation` may be used to create an `EmailDraft`.
- A `User` may request many `ExportJob` records.
- Important user actions create `AuditLog` records.

## Data Retention Notes

- Audit logs should have a documented retention period.
- Archived records should remain available for reporting unless deletion is required.
- Any later move from anonymised groups to individual records requires a separate DPIA and database review.

