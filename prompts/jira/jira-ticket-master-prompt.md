# Jira Ticket Master Prompt

Turn the notes I provide into one clear, concise Jira ticket.

Use this prompt for either:
- Creating a new Jira ticket from rough notes
- Revising an existing Jira ticket using new notes, feedback, or added context
- Converting a finished ticket into Jira markup

If an existing ticket is provided, preserve the original intent and structure unless the notes clearly change the scope.

## Clarify First

Before writing the ticket, decide whether the notes are clear enough to draft.

If the scope, owner, ticket type, data source, delivery phase, acceptance criteria, or final output is unclear, ask 3–7 targeted questions before drafting.

Do not ask generic questions. Only ask questions that would materially change the ticket.

Clarify whether the ticket is one of:

- **Build:** requirements and data sources are mostly known
- **Spike:** the main work is investigation, feasibility, or data discovery
- **Hybrid:** delivery is expected, but requirements, data sources, stakeholder rules, or dependencies still need alignment

When drafting, preserve the intended ticket type and do not overstate certainty.

## Ticket Structure

Use this structure:

## Summary
One sentence describing the work.

## Background / Why
Briefly explain why this work matters and how it connects to the larger goal, feature, epic, or initiative.

## Goal
State the intended outcome.

## Scope
List what is included in this ticket.

## Technical Notes
Include relevant systems, data sources, dependencies, logic, constraints, or implementation details when useful.

## Acceptance Criteria
Provide a short checklist of what must be true for the ticket to be complete.

## Additional Notes
Add links, assumptions, open questions, or references only when needed.

## Output Options

Use the format I ask for. If I do not specify a format, default to **Tight**.

- **Draft:** full Jira ticket in clean markdown
- **Tight:** concise Jira ticket with only essential detail
- **Jira Markup:** Jira wiki markup using `h1`, `h2`, and bullet lists
- **Humanized:** natural internal product/analytics language, not generic AI wording
- **Revision:** tighten, clarify, or update an existing ticket without changing the intended scope

## Rules

- Treat each set of notes as one ticket unless I explicitly say the notes should become multiple tickets.
- Keep the ticket business-friendly, scannable, and not too long.
- Use plain language.
- Include technical detail only when it helps clarify the work.
- Do not invent details.
- Do not overstate certainty when requirements, data sources, mappings, or ownership are still being defined.
- If ownership is known, include it in the ticket.
- If the work depends on another team, call that out clearly.
- If the ticket rolls into an existing dashboard, model, table, epic, or scorecard, mention that in the Background, Goal, or Scope.
- If the ticket includes metrics, include the business definition and numerator / denominator where known.
- If a metric’s numerator, denominator, source, or rules are unknown, call that out as an open item.
- If revising an existing ticket, keep useful existing content and only tighten, clarify, or update what changed.
- Do not rewrite the ticket into a larger scope unless explicitly requested.
- Call out assumptions or open questions only when needed.
- Avoid robotic phrasing, filler, and over-explaining.
- Use concise bullets instead of long paragraphs where possible.
