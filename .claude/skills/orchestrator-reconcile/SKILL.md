---
name: orchestrator-reconcile
description: >
  The Orchestrator's skill — the trigger-agnostic reconciliation engine. Given ANY change on ANY
  surface (a dropped file, a ChatOps command, a scheduled scan, or a manual edit), it resolves
  what changed and dispatches the agent chain to bring every other surface into sync. TRIGGER
  on: "reconcile", "run the pipeline", "sync the project", a watcher firing, or a scheduled scan.
---

# Orchestrator — The Reconciliation Engine

The traffic controller. Its defining principle: **any surface can be the input.** A manual edit to a
Sheet, Doc, or Site is a first-class trigger, equal to a dropped transcript or a ChatOps command.
One engine, many triggers.

## Triggers (all handled identically downstream)

1. **Drive folder drop** — new file in `01_Inbox`.
2. **Scheduled scan** — cadence check for changes since `last_scan` (zero new = zero cost).
3. **ChatOps** — a natural-language command reaches the local host.
4. **Manual edit anywhere** — a human changed a Sheet/Doc/Site; drift detected.

## Procedure

1. **Detect & scope.** Identify what changed and resolve the project via `MASTER_REGISTRY` /
   `Master_Index`. Pull its Drive folder, substrate tabs, and Site URLs.
2. **Resolve entities** referenced by the change against the registry (by ID, never name).
3. **Dispatch the chain in strict order** (no step starts before the prior finishes):
   - `librarian-content-scan` → organize, file, cross-link, mint/resolve IDs, register `VIS-`.
   - `historian-narrative-commit` → Event + dual-layer Commit + derived relations.
   - `creative-director-site-block` → staged blocks + visual spec to `SITE_CONTENT_BLOCKS`.
   - `qa-auditor` → verify at 375/1440, lint, pass/fail ticket.
4. **Gate publish with a hook.** Block the publish step unless `Visual_QA_Status = Verified`.
5. **Write the projections.** API where it exists (Sheets/Drive/Doc bodies); browser automation
   where it doesn't (Sites, Docs tabs), reconciling each Site to its `SITE_CONTENT_BLOCKS`
   intended state. Refresh backlink tabs in every referenced dossier.
6. **Log everything.** Append a `SITE_SYNC_LOG` row: triggered_by, scope, blocks attempted/
   succeeded/failed, manual_edits_detected + action, duration, status, failure_details.
7. **Confirm.** Report back to the human (ChatOps reply / digest): what synced, the link, and any
   `LINT_FINDINGS` raised.

## Error handling

- **Transient** (rate limit, timeout) → retry with exponential backoff.
- **Non-critical** (alt text fails on a non-image) → log and continue.
- **Critical** (can't reach a Sheet, can't open the Site editor) → halt and escalate to the human.
- **Repeated QA failure** (3x) → trigger `site-rollback` (S42): restore last published state, log
  `Manual Intervention Required`, notify.

## Hard rules

- **Never overwrite a human's manual edit** without detecting and preserving it — manual edits are
  first-class inputs to reconcile from, not errors to clobber.
- **Each write path is idempotent, retryable, independently disable-able.** If the browser path
  breaks, Sheet/Drive/dossier writes still succeed and the Site degrades to "stale," not "lost."
- **Sheets are truth.** Reconcile projections to the substrate, never the reverse.

## Honest limits

- The engine is only as good as entity resolution; when a change references an ambiguous entity,
  pause and ask rather than fan out a wrong update across surfaces.
