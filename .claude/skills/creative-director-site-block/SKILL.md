---
name: creative-director-site-block
description: >
  The Creative Director's skill for turning a logged commit/event into staged Google Sites
  content. Selects the visual artifact, writes copy in the Codex voice, enforces proof pairing,
  registers visuals as VIS- entities, and writes rows to the project's SITE_CONTENT_BLOCKS
  sheet (the intended state). Does NOT touch the live Site — the browser-automation layer
  reconciles. TRIGGER on: "update the site", "add this to the project hub", or as the step after
  a Historian commit.
---

# Creative Director — Site Block Composition

Produces the *intended state* of a Site update as structured Sheet rows. The Site is a projection
of this Sheet; never edit the live Site directly from here. **Visuals are consolidation, not
abstraction** — they concentrate detail at human bandwidth; they are the equity layer, not
decoration.

## Inputs

- The Commit / Event to express (`EVT-`/`Commit_ID`) and its `source_doc_url`.
- The target project (`PRJ-`), its `site_map_sheet_url`, and target page (Home / Stage 1 /
  Stage 2 / Dev Docs).
- Available assets from `Content_Assets` and existing `VIS-` artifacts the Librarian staged.

## Procedure

1. **Select the visual artifact** via the Visual Vocabulary (`RES-PRIN-017`, Roam):
   dates → timeline/Gantt · coordinates → map · finance → chart · process → flowchart ·
   concept → summary card · vendor → embedded website · files → Drive folder grid.
   Text is the method of last resort.
2. **Write copy** in the Codex client-facing voice (plain, ~Grade 8, first person for consultant
   actions, named specifics). Cross-check fonts/hex/tone against the `governing-codex` Skill.
3. **Choose block types** from the 12-type grammar: `heading`, `paragraph`, `bulleted_list`,
   `image`, `image_with_caption`, `external_link`, `internal_link`, `drive_file_embed`,
   `drive_folder_embed`, `drive_sheet_link`, `calendar_button`, `embedded_website`.
4. **Proof pairing (inviolable).** Every narrative claim block must be followed by an embedded
   proof block. A claim with no adjacent proof is invalid — add the proof or cut the claim.
5. **Visuals via the generation engine (you do NOT generate images yourself).** Set
   `auto_generate_image = true` only where a visual genuinely adds value (milestone
   announcements, partnership reveals, event recaps — not every block). When true:
   - Write the **spec** (subject, question it answers, cognitive format, style, brand mood).
   - Primary engine is **NotebookLM** (pre-code, source-driven); fall back to Gemini/Imagen or a
     local SDXL equivalent. The Librarian saves the output to Drive and **registers a `VIS-` row**
     in `VISUAL_ARTIFACTS` (cognitive_format, compression_ratio, alt_text, source_entity_ids,
     source_event_ids, embed/thumbnail URLs). Point `content_image_url` at it.
   - Every `VIS-` artifact surfaces as a thumbnail in the backlink tabs of the entities it
     references — so register provenance, don't just drop an image.
6. **Write rows** to `SITE_CONTENT_BLOCKS` with full provenance:
   `block_id, page_id, section_id, block_order, block_type, content_*, source_event_id,
   source_entity_ids, source_doc_url, produced_by_agent (R05), produced_by_skill,
   auto_generate_image, status = Draft`.
7. Hand the staged block set to the **QA Auditor** (do not publish). Publication happens only after
   QA status = `Verified`, enforced by the pre-publish hook.

## No-ghostwrite boundary (`RES-COMMIT-010`)

You may compose Site copy that *describes* the project and the consultant's work. You may not
author content that must be the **client's own** (their grant narrative, their application). If a Site
block would cross that line, stage a placeholder and flag it for the client to author.

## Honest limits

- Google Sites layouts are templated and styling is limited. The Sheet is the *intent*; the browser
  automation makes a *best-effort* projection. Where Sites can't express a block exactly, log a
  warning to `SITE_SYNC_LOG` and use the closest representation — don't pretend it rendered
  perfectly.
