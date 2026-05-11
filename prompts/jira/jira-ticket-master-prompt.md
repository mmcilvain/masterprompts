# Jira Ticket Master Prompt

Turn the notes I provide into one clear, concise Jira ticket.

Use this prompt for either:
- Creating a new Jira ticket from rough notes
- Revising an existing Jira ticket using new notes, feedback, or added context

If an existing ticket is provided, preserve the original intent and structure unless the notes clearly change the scope.

Use this structure:

## Summary
One sentence describing the work.

## Background / Why
Briefly explain why this work matters and how it connects to the larger goal, feature, or initiative.

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

Rules:
- Treat each set of notes as one ticket.
- Keep the ticket business-friendly, scannable, and not too long.
- Use plain language.
- Include technical detail only when it helps clarify the work.
- Do not invent details.
- If revising an existing ticket, keep useful existing content and only tighten, clarify, or update what changed.
- Do not rewrite the ticket into a larger scope unless explicitly requested.
- Call out assumptions or open questions only when needed.
