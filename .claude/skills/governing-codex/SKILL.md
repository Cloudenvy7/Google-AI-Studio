---
name: governing-codex
description: >
  The style-and-doctrine reference every agent consults before producing client-facing content.
  Carries voice rules, the brand style guide, the Visual Vocabulary, the proof-pairing law, the
  principle/drift library, and the inviolable commitments. TRIGGER on: writing or reviewing any
  client-facing copy or visual, "what's our voice/brand", "check this against the codex", or as a
  pre-write step inside the Creative Director and Historian skills.
---

# Governing Codex — Voice, Brand & Doctrine

The longer doctrine behind `CLAUDE.md`. Consult this before any agent writes client-facing
content. When this skill and `CLAUDE.md` conflict, `CLAUDE.md` wins (it is the constitution).

## Voice

- **Client-facing:** first person where the consultant acts ("I recommended…", "We discussed…").
  Plain language, low fog index, ~Grade 8 reading level. **Name specifics** — real tools, people,
  events — never generic abstractions.
- **SME / internal (Framework layer only):** graduate-level framework language is allowed in the
  Layer-2 tag (RACI / SWOT / Stakeholder / a named principle), never in client-facing prose.
- **Dual-layer always:** every commit pairs a plain Narrative (Layer 1) with a Framework tag
  (Layer 2).

## Brand style guide

> **TBD — fill these in with the real values; do not invent them.** Until populated, agents must
> ask for the brand value rather than guessing a hex code or font.

- Primary palette (hex): `TODO`
- Secondary / accent (hex): `TODO`
- Heading font + sizes (e.g., H1/H2/H3): `TODO`
- Body font + minimum size: `TODO` (min body size is also the lever the QA feedback loop tunes)
- Logo usage, draft-banner text, footer contact line: `TODO`

## The Visual Vocabulary (consolidation, not abstraction)

Text is the method of last resort. Map data to the right artifact:

| If the data is… | Use | Tool |
|---|---|---|
| dates / sequences | timeline / Gantt | Google Charts · Mermaid |
| coordinates / addresses | map | Google My Maps |
| financial / KPIs | chart / dashboard | Looker Studio · Sheets |
| process / hierarchy | flowchart / node graph | Mermaid |
| a core concept / milestone | summary card + image | NotebookLM · Imagen |
| a vendor / partner | embedded website | Sites embed-by-URL |
| files / assets | Drive folder grid | Sites Insert > Drive |

A good visual **concentrates** detail (consolidation); it never **hides** it (abstraction). Visuals are
first-class data — register them as `VIS-` artifacts, not throwaway output.

## Proof-pairing law

Every narrative claim placed on a Site must sit beside an embedded proof object (Drive file,
Sheet, folder grid, or website embed). A claim with no adjacent proof is invalid.

## The principle / drift library (queryable lineage)

- **Five canonical books** (`RES-BOOK-001..005`) and their ~31 principles (`RES-PRIN-*`) live in
  `RESOURCES`. Tag any deliverable to the principle it derives from so the lineage is queryable.
- **Six drifts** (`RES-DRIFT-01..06`) are recurring distortions. Before publishing, check the work
  against them; if it treats the AI as the engine, skips the pre-code foundation, or conflates BMC
  reading with building, **name the drift and self-correct** (a `corrects_drift` relation / a
  `LINT_FINDINGS` row).

## Inviolable commitments to honor in copy

- **AI assists, does not ghostwrite** (`RES-COMMIT-010`): structure/critique/visualize the client's
  own work; never author what must be theirs.
- **180-day staleness** (`RES-COMMIT-008`): flag, don't pretend old facts are fresh.
- **Sheets are truth** (`RES-COMMIT-005`): copy on a Site is a projection of the substrate.

## How agents use this skill

The Creative Director loads it before copywriting and visual selection; the Historian loads it to
pick the right Framework tag and to anchor "why" against current OKRs; the QA Auditor uses the
brand values and proof-pairing law as pass/fail criteria. The Feedback Learner edits this skill
when a QA failure pattern warrants a parameter change.
