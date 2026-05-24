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

## Inputs

- The input artifact (text, file link, or a reference to a just-created note).
- The project context (`PRJ-` ID) and any entities mentioned.
- `source_doc_url` — the document where this originated (required).

## Procedure

1. **5W Interrogation.** Extract: **Who** (and are they a decision-maker?), **What** (pivot or
   refinement?), **Where** (budget/timeline/scope?), **When** (urgent or backlog?), **Why**
   (which strategic objective?). Anchor "why" against the current OKRs in the Codex.
2. **Resolve entities** mentioned to their IDs via `MASTER_REGISTRY`. Unknown → ask before
   minting.
3. **Frame it.** Pick the right framework: RACI (task assignments), SWOT (risks), Stakeholder
   Analysis (people/power). Produce the **Framework tag**.
4. **Write the Event row** to `EVENTS`:
   `event_name, event_type, event_date, primary_project_id, source_doc_url, summary`.
   Mint an `EVT-#####` ID and register it in `MASTER_REGISTRY`.
5. **Write the Commit row** to `Project_Narrative_Log`:
   `Timestamp, Commit_ID, Input_Source, Narrative_Story (Layer 1, plain language),
   Framework_Tag (Layer 2), Visual_QA_Status = Pending`.
6. **Derive relations.** For each connection implied by the event, emit a `RELATIONS` row with
   `source_event_id` set to the Event's ID (required — every relation cites its event).
7. **Trigger backlinks.** Flag the referenced entities so their dossier `Mentions & Connections`
   tabs regenerate (delegate to the backlink-refresh step).

## Dual-layer requirement (inviolable)

Layer 1 (Narrative) must be readable by a layperson. Layer 2 (Framework) must be filterable by a
professional. Never write one without the other.

## Reversible history

Each Commit_ID / EVT-ID is a rollback handle. Record enough that, given the ID, you can trace
every downstream asset, Site block, and relation it produced.

## Honest limits

- `created_date`/`created_by` describe when the *row* was written; `event_date`/`source_doc_url`
  describe when the connection happened *in the world*. Keep them distinct — never conflate.
