# AI Build Rules

## Purpose

This document defines how AI-supported features should be built in FutureFit Careers.

## Golden Rules

- Use anonymised group-level data only in the MVP.
- Do not send direct identifiers to AI services.
- Do not ask AI to make final decisions.
- Do not present AI output as objective truth.
- Require human review for client-impacting outputs.
- Log AI requests and review decisions.
- Keep prompts versioned.

## AI Feature Boundaries

Initial AI features:

- Match explanation between one client group and one opportunity.
- Client-ready email draft based on approved or reviewable match context.

Do not build:

- Individual risk scoring.
- Automated eligibility decisions.
- Fully automated outreach.
- Unreviewed recommendations.
- Personality, health, ethnicity, age, or other protected-characteristic inference.

## Prompt Design Requirements

Prompts should include:

- Task purpose.
- Explicit instruction to use only provided data.
- Structured anonymised group context.
- Structured opportunity context.
- Required output shape.
- Instruction to list assumptions and uncertainty.
- Instruction to avoid final decisions or guarantees.

## Output Shape

Prefer structured output with fields such as:

- `summary`
- `strengths`
- `gaps`
- `assumptions`
- `recommendedHumanChecks`
- `clientFriendlyVersion`

Validate output before saving or showing it as reviewable content.

## Language Rules

Use wording such as:

- "may be a fit"
- "could be relevant"
- "suggests a possible connection"
- "requires human review"
- "based on the provided anonymised group data"

Avoid wording such as:

- "is the best fit"
- "should be selected"
- "guaranteed"
- "eligible"
- "not suitable"
- "the candidate is"

## AI Metadata

For each generation, store:

- Feature name.
- Prompt version.
- Model name.
- Request timestamp.
- Requesting user.
- Related entity IDs.
- Review status.

Do not store unnecessary raw prompts if they contain sensitive operational context. If raw prompt retention is needed, review it separately.

## Failure Handling

When AI output is unavailable or invalid:

- Show a clear error to the specialist.
- Do not create a review item.
- Log the failure without storing sensitive content.
- Allow the specialist to retry.

## Evaluation

Before production use, test AI outputs against examples for:

- Hallucinated claims.
- Unsupported assumptions.
- Overconfident language.
- Privacy leakage.
- Bias risk.
- Clarity for specialists.

