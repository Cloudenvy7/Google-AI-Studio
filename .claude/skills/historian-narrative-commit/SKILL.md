---
name: historian-narrative-commit
description: >
  The Project Historian's core skill. Take any new input (transcript, file, ChatOps command,
  or manual edit) and produce a dual-layer Commit + an Event row with full provenance.
  TRIGGER on: "log this", "commit this to the bible", a new event/decision that needs
  recording, or as the downstream step after sbdc-meeting-note. Only the Historian writes
  the Narrative/Strategy columns.
---

# Historian — Narrative Commit

Implements the 5W Interrogation, framework tagging, and reversible Commit Logic. Pairs every
commit with an Event so the narrative log and the knowledge graph share provenance.

**Substrate-first:** the Event is the unit of truth; relations are *derived* from it. You write to the
sheets (truth); dossiers/Sites/maps regenerate from them.

## Inputs

- The input artifact (text, file link, or a reference to a just-created note).
- The project context (`PRJ-` ID) and any entities mentioned.
- `source_doc_url` — the document where this originated (required).

## Procedure

1. **5W Interrogation.** Extract: **Who** (decision-maker?), **What** (pivot or refinement?),
   **Where** (budget/timeline/scope?), **When** (urgent or backlog?), **Why** (which strategic
   objective?). Anchor "why" against the current OKRs in the Codex.
2. **Resolve entities** mentioned to their IDs via `MASTER_REGISTRY`. Unknown → ask before
   minting.
3. **Frame it.** Pick the framework: RACI (tasks), SWOT (risks), Stakeholder Analysis
   (people/power), or one of the ~31 named principles (`RES-PRIN-*`). Produce the **Framework
   tag** and, where a deliverable derives from a book/principle, add a `derived_from_book` /
   principle relation.
4. **Write the Event row** to `EVENTS`:
   `event_name, event_type, event_date, primary_project_id, source_doc_url, summary,
   produced_by_agent (R01), produced_by_skill (S05)`. Mint `EVT-#####`; register in
   `MASTER_REGISTRY`.
5. **Write the Commit row** to `Project_Narrative_Log`:
   `Timestamp, Commit_ID, Input_Source, Narrative_Story (Layer 1, plain language),
   Framework_Tag (Layer 2), Visual_QA_Status = Pending`.
6. **Derive relations.** For each connection implied by the event, emit a `RELATIONS` row with
   `source_event_id` set to the Event's ID (REQUIRED — every relation cites its event). Keep
   `relation_type` within the controlled vocabulary; do not invent new types casually.
7. **Trigger backlinks.** Flag referenced entities so their dossier `Mentions & Connections` tabs
   regenerate. Respect the **180-day staleness rule** (`RES-COMMIT-008`): older relations without
   a confirming event are flagged "last confirmed on [date]," never deleted.

## Drift & lint check

Before committing, check the input against the six drifts (`RES-DRIFT-01..06`). If it treats the AI
as the engine, skips the pre-code foundation, or conflates BMC reading with building, **name the
drift and self-correct.** If you detect a contradiction with an existing event, a superseded claim,
or an orphan entity, write a `LINT_FINDINGS` row rather than silently resolving it.

## Dual-layer requirement (inviolable)

Layer 1 (Narrative) readable by a layperson; Layer 2 (Framework) filterable by a professional.
Never write one without the other.

## Honest limits

- `created_date`/`created_by` describe when the *row* was written; `event_date`/`source_doc_url`
  describe when the connection happened *in the world*. Keep them distinct — never conflate.
