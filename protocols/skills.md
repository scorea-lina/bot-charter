# Skills & Tooling Protocol (Org-wide)

## Purpose
Make “skills” a first-class concept so bots use the right workflow/tooling instead of ad‑hoc commands.

This doc does **not** replace repo runbooks. It defines:
- which skill to reach for
- what the skill owns
- the safety boundaries (especially secrets)

## Canonical skills

### `vercel-ops`
Use for anything involving Vercel:
- linking/switching projects
- setting/verifying env vars (without pasting secrets in chat)
- preview/prod deploys
- inspecting deployment/alias status
- Vercel cron configuration (vercel.json + deploy)

Owner: deploy/release mechanics.

### `supabase-ops`
Use for anything involving Supabase (DB + Storage):
- inspecting schema/tables/RLS
- writing safe SQL queries
- applying migrations / backfills
- verifying data integrity after jobs run
- generating “how to do X in Supabase” runbooks

Owner: DB operations + guardrails.

### `home-design-ops`
Use for HomeDesign-specific operations and “what to do next” runbooks:
- HomeDesign environment URLs (QA/prod)
- HomeDesign cron/job endpoints + auth expectations
- post-deploy verification for HomeDesign
- cutovers (Mac mini job → Vercel cron)

Owner: HomeDesign operational knowledge + project-specific playbooks.

## Skill selection rules (decision tree)
1) **Is the user asking about deploys, env vars, previews, prod, Vercel cron?** → use `vercel-ops`.
2) **Is the user asking about schema/data/migrations/backfills/RLS/SQL?** → use `supabase-ops`.
3) **Is the user asking “how do we run HomeDesign / where is X configured / what to verify”?** → use `home-design-ops` (and then delegate to `vercel-ops` / `supabase-ops` as needed).

## Secrets boundary (non‑negotiable)
- Never ask humans to paste secrets into chat.
- Prefer local secret files + CLI tooling.
- If a secret needs to be created/edited on disk, do it locally with restrictive permissions.

## Pre-provisioned access (default assumption)
For supported projects, assume the host already has CLIs authenticated (e.g., Supabase + Vercel).

**Rule:** do *not* ask “do we have access?” until you've attempted the relevant CLI and captured the exact error.

### Required preflight before claiming blocked
- **Vercel:** run `vercel whoami` (or `vercel projects ls`)
- **Supabase:** run `supabase projects list` (or the project-specific equivalent)

If the command succeeds: proceed with the task.
If it fails: report the exact error + ask for the *minimum* missing credential/permission.

### Capability self-check (capcheck)
If unsure, run `python3 tools/capcheck.py` (in the OpenClaw workspace) and paste its results (never paste secrets).

