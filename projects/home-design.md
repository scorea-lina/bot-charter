# HomeDesign Project Addendum

This document contains HomeDesign-specific operating rules that are *stricter* than the org-wide defaults.

## 0) Concrete Discord channels (canonical)
- #hd-pm: <#1477066552439341137>
- EngineerBot (engineering / PRs / deploys): <#1478814881598799872>
- DesignerBot (design / UX decisions): <#1478814583732043946>
- TesterBot (end-to-end testing reports): <#1479584904382779512>
- Cross-functional collab: <#1478801538314145893>

**Channel discipline:** never ask a bot for work outside its channel; relay context across channels explicitly.


## 1) Ping cadence (strict)

### ACK SLA
- Any assigned ask must receive an **ACK within 2 minutes**.
  - ACK must include **owner + next artifact + ETA**.

### Artifact SLA
- The promised artifact should arrive by the stated **ETA**.
- If **ETA + 2 minutes** passes with no artifact: ping once for status + revised ETA.

### Silence rule
- If there\x27s an in-flight task and the owner is silent for **>10 minutes**, post a quick ping requesting:
  - current status
  - blocker (if any)
  - next checkpoint time

### Escalation
- If still no artifact after a second ping, escalate in the team-visible channel with:
  - what\x27s blocked
  - what was tried
  - smallest unblock needed
  - recommended default

## 2) Concept of time (HomeDesign tone)
- Prefer **Small/Medium/Large** over wide ranges.
- Always include *when you\x27ll ping for QA* or *when you\x27ll post the next update*.

## 3) Flow of work (canonical)
1) **Design** posts the spec/decision (or "DECISION NEEDED")
2) **Engineering** implements and posts PR link + clear QA request
3) **QA** runs checklist and posts PASS/FAIL
4) If **FAIL**: Engineering ACKs immediately, posts fix plan + ETA, then re-requests QA
5) If **PASS**: Engineering merges + deploys to prod, then posts prod URL + confirmation
6) PM/ops updates #hd-pm with the minimal user-visible summary + links

## 4) Manual work rule (HomeDesign phrasing)
- Do not ask the human to do manual execution steps. Only ask for:
  - credentials/access you cannot obtain
  - high-risk approvals
  - explicit product decisions

## 5) Release rule (HomeDesign)
- Default unless explicitly overridden per PR: **QA PASS → merge PR → deploy to prod → post prod URL + confirmation in #hd-pm**.
- If “prod” is ambiguous (no canonical prod URL/domain), ask in #hd-pm before deploying.

## 6) Deployment autonomy (HomeDesign)
- If a change is:
  - already merged to `main`, and
  - additive/low-risk (ops/cron/status endpoints, bugfixes), and
  - has no pending QA gate,
  then **deploy to prod** without asking.
- After deploying, post in #hd-pm:
  - what shipped (PR/commit)
  - prod URL / underlying deploy
  - any follow-up verification step
- Ask before deploying when:
  - schema migration is involved
  - user-facing behavior changes materially
  - required secrets/permissions are missing
  - rollback risk is unclear
