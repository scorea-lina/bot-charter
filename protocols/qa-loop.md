# QA Loop Protocol (Org-wide)

## Goal
- Tester runs QA immediately once a PR is testable.
- FAIL reaches Engineer immediately with full context.
- PASS triggers immediate merge/deploy + next-task assignment.

## Canonical structure
### One shared QA relay channel
Use one shared channel where PMBot, EngineerBot, and TesterBot all participate.

### One thread per PR
Create a single thread per PR in the shared QA relay channel.
All comms for that PR happen in that thread.

## Required message formats
### EngineerBot: Ready for QA
In the PR QA thread, EngineerBot posts:
1) PR link
2) QA URL(s) (alias + direct deploy)
3) 3-step checklist
4) Expected visible change
5) Explicit ask to TesterBot to test now and reply PASS/FAIL in-thread

### TesterBot: Result
In the PR QA thread, TesterBot posts one of:
- `PR #__ QA: PASS ✅`
- `PR #__ QA: FAIL ❌`

If FAIL, include:
- failing step number(s)
- expected vs actual
- links to failing page/endpoint
- screenshot/logs if relevant

## SLAs
- TesterBot: respond within 5 minutes of Ready-for-QA (PASS/FAIL or BLOCKED+ETA)
- EngineerBot: acknowledge FAIL within 2 minutes with plan+ETA

## Fail loop (redundant relay)
- TesterBot MUST tag EngineerBot in FAIL.
- PMBot backstops: if no Engineer ack within 2 minutes, PMBot pings EngineerBot in eng channel with link + 1–2 bullets.

## Pass loop (seamless move-on)
On PASS:
1) PMBot triggers merge+prod deploy request immediately.
2) PMBot posts required PM update (project-defined).
3) PMBot assigns next task immediately with deliverable + ACK+ETA.
