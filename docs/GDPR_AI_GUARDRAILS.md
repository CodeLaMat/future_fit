# GDPR And AI Guardrails

## Core Position

FutureFit Careers is an AI-supported internal decision-support tool. It must not make automated decisions about individuals. Employment specialists remain responsible for all client-facing decisions and communications.

## MVP Data Policy

The MVP should use anonymised or aggregated client-group data only.

Do not store:

- Client names.
- Personal email addresses.
- Phone numbers.
- Home addresses.
- National identification numbers.
- Exact birth dates.
- Free-text biographical histories that could identify a person.
- Sensitive personal data unless explicitly approved through a separate process.

## Lawful Basis And Purpose

Before production use, confirm and document:

- Lawful basis for processing.
- Processing purpose.
- Data categories.
- Data subjects.
- Recipients or processors.
- Retention periods.
- Data subject rights process.
- AI vendor and subprocessors.

## AI Use Rules

AI may be used to:

- Summarise anonymised group-level employability context.
- Explain potential fit between a client group and an opportunity.
- Identify skills gaps and assumptions.
- Draft email text for specialist review.

AI must not be used to:

- Decide eligibility for services.
- Rank named individuals.
- Reject clients.
- Infer protected characteristics.
- Generate sensitive personal conclusions.
- Send messages automatically.
- Produce final client-facing recommendations without human review.

## Human Review Requirements

Human review is required before:

- A match explanation is used in client-facing work.
- An email draft is copied into external communication.
- Any AI-generated text is included in official reporting.

Reviewers should check:

- Accuracy.
- Fairness.
- Missing context.
- Unsupported assumptions.
- Tone and clarity.
- Whether the output could be interpreted as a final automated decision.

## Transparency Requirements

The platform should clearly explain:

- What data is used.
- Why AI is used.
- What the AI output means.
- What the AI output does not mean.
- That a human specialist reviews outputs.
- That the platform supports decisions but does not replace professional judgement.

## Prompt And Output Safety

Prompts should:

- Use structured anonymised input.
- Exclude direct identifiers.
- Ask for uncertainty and assumptions.
- Ask for plain language.
- Avoid deterministic ranking language.

Outputs should:

- Include caveats and human checks.
- Avoid claims of certainty.
- Avoid sensitive inferences.
- Avoid fabricated sources.
- Be stored with model and prompt version metadata.

## Auditability

Log:

- AI generation requests.
- Review decisions.
- Export activity.
- Record creation, updates, and archiving.
- Authentication events where appropriate.

Audit metadata should help reconstruct what happened without storing unnecessary personal data.

## Production Readiness Gate

Before handling real operational data, complete:

- Data Protection Impact Assessment, if required.
- Processor and subprocessor review.
- Retention policy.
- Access control review.
- Incident response process.
- AI transparency notice.
- Security testing.

