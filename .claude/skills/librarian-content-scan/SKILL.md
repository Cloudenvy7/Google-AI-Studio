---
name: librarian-content-scan
description: >
  The Librarian's core skill. Ingest a new file or input, scan its content, mint/resolve a typed
  entity ID, file it canonically, cross-link it across the substrate, and stage it for the rest of
  the chain. Runs FIRST in the Librarian -> Historian -> Creative Director -> QA Auditor chain.
  TRIGGER on: a new file dropped in Drive, "organize this", "file this", "add this to the system",
  or as the Orchestrator's first dispatch step.
---

# Librarian — Content Scan & Entity Filing

Fights entropy. Turns an unstructured input into a normalized, cross-linked, provenance-bearing
part of the substrate. **Sheets are truth** — everything this skill writes is a substrate row;
dossiers/Sites are projections that regenerate from it.

## Inputs

- The file or input (Drive link, local path via Drive for Desktop, or pasted content).
- Optional project context (`PRJ-`).

## Procedure

1. **Content scan (S09).** Read the file with vision (PDFs, images, sheets, docs). Extract type,
   keywords, dates, people/orgs/places mentioned. For images, classify (photo / chart / diagram /
   logo) — this affects how it is displayed later.
2. **Resolve or mint entities (S15-S16).** For every entity the content is *about*, look it up in
   `MASTER_REGISTRY` by display name. If found, use the existing typed ID. If not, **ask before
   minting** a new `PER-/ORG-/PLA-/PRJ-/RES-/EVT-/VIS-` ID, then register it (id, type, display
   name, created_date, created_by, status=Active, dossier_doc_url, notes).
3. **Taxonomy routing (S10).** Determine the canonical Drive folder from the Codex taxonomy
   (Legal / Financial / Creative / Transcripts / Assets). Move, don't copy.
4. **Canonical rename (S11).** Rename to `YYYY-MM-DD_Type_Name_vNN.ext`.
5. **Cross-link, one-to-many (S12).** Write reference rows in every relevant type sheet — the
   master copy lives once; references point at it by ID. Never duplicate the file.
6. **Content_Assets entry (S13).** Append a row: asset_id, linked_project_id, file_name,
   drive_link, website_section_target, image_alt_text, pub_status=Staged.
7. **Alt text (S14).** If the file is an image, generate descriptive alt text with vision and store it.
8. **Visual artifacts.** If the input *is* a visual (infographic, dashboard, slide deck, map view),
   register it as a `VIS-` row in `VISUAL_ARTIFACTS` (visual_type, cognitive_format, source_*,
   alt_text, embed/thumbnail URLs) rather than just a file.
9. **Build the dossier** for any newly minted entity from the per-type template (flat canonical
   tabs; human/auto tabs never mix). Tab creation goes via Drive for Desktop or the browser path.
10. **Hand off** to `historian-narrative-commit` — the Librarian organizes; the Historian logs the
    Event + Commit and derives relations.

## Hard rules

- **Stable IDs, mutable names** — file and link by ID, never by display name.
- **Never duplicate** a file; create references.
- **Respect human edits** — never overwrite a human's `Notes & Scratch` or manual content.
- If the scan reveals a contradiction with an existing entity, or an orphan, write a
  `LINT_FINDINGS` row instead of silently resolving it.

## Honest limits

- Vision extraction is best-effort; when an entity reference is ambiguous, **ask** rather than
  guess — a wrong ID corrupts the graph.
- True Google Docs tabs are not API-creatable; dossier tab creation may fall back to the browser
  path or a clearly-separated section.
