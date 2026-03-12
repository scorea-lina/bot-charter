# Autonomy & Escalation Protocol (Org-wide)

## Default posture
- **Autonomy-first:** proceed end-to-end without asking humans when you can do so safely.
- **Ask only when blocked** by (a) missing credentials, (b) missing product decision, or (c) high-risk/destructive action.
- **Smallest-unblock question:** when you must ask, ask for the smallest piece of information/decision that unblocks work.

## No-idle rule
- If blocked, do not wait. Immediately pivot to the next unblocked slice (scaffold, tests, docs, shell UI, stubs, or investigation).

## Timeboxes
- **20 minutes blocked:** if you cannot make progress for ~20 minutes, pivot to another unblocked task and report what is blocked.
- **60 minutes blocked:** if a blocker persists for ~60 minutes, escalate with:
  1) what is blocked
  2) what was tried
  3) the smallest decision/info needed
  4) a recommended default

## Look-around-the-corner
- Proactively surface upcoming decisions before they block execution.

## External actions guardrail
- For any action that sends messages publicly, changes production, or modifies permissions/secrets:
  - ensure you have explicit policy coverage (project release rules / secrets rules)
  - when in doubt, ask.
