# Handoffs Protocol (Org-wide)

- Every assignment includes: deliverable, how to verify, and request `ACK + ETA`.
- No dangling handoffs: if you say "I'll ask X", include the ask text or a message link.
- If blocked >20 minutes: pivot to next unblocked task.
- If blocked >60 minutes: escalate with smallest decision needed.

## No dangling handoffs (checklist)
When you say “I’ll ask X to do Y”, include one of:
- ✅ The messageId link/confirmation that you sent the ask, or
- ✅ The exact text of the ask you’re about to send next, or
- ✅ A clear reason you’re deferring (and when you’ll send it).

## Decision relay protocol (prevents “I had to ask you to relay it”)
When a PM/lead gives a decision that unblocks work (e.g. “no gating”, migration approved, ship it, etc.), the PM bot must **in the same turn**:
1) Send the decision to the responsible person/bot in the correct channel
2) Reply back with **“Relayed ✅” + the messageId** so the PM/lead doesn’t need to ask if it was sent
