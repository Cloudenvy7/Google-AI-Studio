---
name: creative-director-site-block
description: >
  The Creative Director's skill for turning a logged commit/event into staged Google Sites
  content. Selects the visual artifact, writes copy in the Codex voice, enforces proof pairing,
  and writes rows to the project's SITE_CONTENT_BLOCKS sheet (the intended state). Does NOT
  touch the live Site — the browser-automation layer reconciles. TRIGGER on: "update the site",
  "add this to the project hub", or as the step after a Historian commit.
---

# Creative Director — Site Block Composition

Produces the *intended state* of a Site update as structured Sheet rows. The Site is a projection
of this Sheet; never edit the live Site directly from here.

## Inputs

- The Commit / Event to express (`EVT-`/`Commit_ID`) and its `source_doc_url`.
- The target project (`PRJ-`), its `site_map_sheet_url`, and target page (Home / Stage 1 /
  Stage 2 / Dev Docs).
- Available assets from `Content_Assets` (files, images the Librarian already staged).

## Procedure

1. **Select the visual artifact** via the Visual Vocabulary (Codex §7.2):
   dates → timeline/Gantt · coordinates → map · finance → chart · process → flowchart ·
   concept → summary card · vendor → embedded website · files → Drive folder grid.
   Text is the method of last resort.
2. **Write copy** in the Codex client-facing voice (plain, ~Grade 8, first person for consultant
   actions, named specifics). Cross-check fonts/hex/tone against the `governing-codex` Skill.
3. **Choose block types** from the 12-type grammar (Appendix C): `heading`, `paragraph`,
   `bulleted_list`, `image`, `image_with_caption`, `external_link`, `internal_link`,
   `drive_file_embed`, `drive_folder_embed`, `drive_sheet_link`, `calendar_button`,
   `embedded_website`.
4. **Proof pairing (inviolable).** Every narrative claim block must be followed by an embedded
   proof block. If you write a claim with no adjacent proof, the block set is invalid — add the
   proof or cut the claim.
5. **Image decision.** Set `auto_generate_image = true` only where a visual genuinely adds value
   (milestone announcements, partnership reveals, event recaps — not every block). When true,
   write the image **prompt** (subject, style, composition, lighting, brand mood) and hand off to the
   image model via MCP; the Librarian saves the asset to Drive and returns a `content_image_url`.
   *You do not generate images yourself.*
6. **Write rows** to `SITE_CONTENT_BLOCKS` with full provenance:
   `block_id, page_id, section_id, block_order, block_type, content_*, source_event_id,
   source_entity_ids, source_doc_url, auto_generate_image, status = Draft`.
7. Hand the staged block set to the **QA Auditor** (do not publish). Publication happens only
   after QA status = `Verified`, enforced by the pre-publish hook.

## Honest limits

- Google Sites layouts are templated and styling is limited. The Sheet is the *intent*; the browser
  automation makes a *best-effort* projection. Where Sites can't express a block exactly, log a
  warning to `SITE_SYNC_LOG` and use the closest available representation — don't pretend it
  rendered perfectly.
