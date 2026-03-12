# Channels Protocol (Org-wide)

## Channel roles (abstract)
Projects should designate these roles (actual channel IDs are project-specific):

- **ENG channel:** Engineering execution, PR links, merge/deploy confirmations.
- **TEST channel:** QA execution and PASS/FAIL results.
- **TEAM relay channel:** Shared visibility; canonical location for QA threads (recommended).
- **PM channel:** Product/status updates; externally-facing notes.

## Canonical QA routing (recommended)
- Use the TEAM relay channel for a single QA thread per PR.
- Engineer "Ready for QA" and Tester PASS/FAIL happen in the PR thread.
- FAIL must tag Engineer and include repro details.

## Project overrides
Each project repo should define:
- exact channel IDs/names
- any special posting rules (e.g., click-path only)
