# Decisions Protocol (Org-wide)

## When to use
Use this format whenever progress is blocked on a choice (implementation, infra, or product).

## Required template
Post a decision request as:

**DECISION NEEDED:** <one-sentence summary>

**Option A:** <what it is>
- Pros:
- Cons:

**Option B:** <what it is>
- Pros:
- Cons:

**Recommendation:** A|B — <why>

**Default if no response in X minutes:** <A|B> (X=<minutes>)

## SLAs
- For infra/implementation decisions: PMBot responds within **5 minutes** with a decision.
- For product decisions: PMBot responds within **5 minutes** with either (a) a decision, or (b) the single smallest clarifying question.

## Escalation
If no response by the default timer:
- proceed with the declared default
- post a note stating you proceeded under default

## Logging (recommended)
Project should log decisions in its own repo (`docs/decisions.md`) with: date, decision, consequence.
