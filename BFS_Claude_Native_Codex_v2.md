# BLACK FOX STUDIOS

## The Visual Second Brain — Operating Codex (Claude Runtime Edition)

**Relational data infrastructure for community-based organizations, with Claude as one replaceable accelerator over a model-agnostic substrate**

Prepared by Andrew Powers — Founder, Black Fox Studios | SBDC Advisor, Highline College — andrew@blackfoxstudios.org

**Version 2.1 — realigned to the Visual Second Brain Architecture Narrative + Substrate** | CONFIDENTIAL — Internal & Partner Use Only

> **What this edition is.** v1.0 (the Antigravity CMS Codex/Blueprint) described the organism on
> the Gemini/Antigravity stack. v2.0 re-platformed it onto Claude. **v2.1 corrects the framing
> itself:** the system is not Claude, Gemini, or any model — **the system is the relational
> substrate**, and the AI is a replaceable accelerator that reads and maintains it. This edition
> realigns to the two governing documents — `Visual_Second_Brain_Architecture_Narrative.md`
> and the Substrate workbook — and folds in everything they carry that earlier editions missed:
> `VISUAL_ARTIFACTS` as a 7th entity type, the lint/integrations/vocabulary sheets, the five-book
> intellectual lineage, the six drifts, NotebookLM as the pre-code visual engine, the staleness
> discipline, the no-ghostwrite compliance boundary, and the cloud→local-first deployment arc.
> Claude is documented here as **one runtime**, not the center.

---

## Table of Contents

**Part I — The Central Inversion & Strategic Foundation**
- 1.0 The substrate is the system; the AI is not
- 1.1 The problem this is built against
- 1.2 The Clarity Gap and the equity wedge
- 1.3 The Organism Metaphor (substrate-first)
- 1.4 Claude as one replaceable runtime

**Part II — Governance Model**
- 2.0 Constitutional AI: the Governing Codex
- 2.1 Dual-Layer Communication
- 2.2 Visual QA as Law
- 2.3 The no-ghostwrite compliance boundary

**Part III — The Organizational Structure (model-agnostic roles)**
- 3.0 Agents as subagents + Skills
- 3.1–3.5 Historian, Librarian, Creative Director, QA Auditor, Orchestrator

**Part IV — The Substrate: The Relational Knowledge Graph**
- 4.0 Master Registry & typed IDs
- 4.1 Seven entity types
- 4.2 Events & Relations (mandatory provenance)
- 4.3 Visual Artifacts as first-class data
- 4.4 Dossiers, backlinks & the staleness discipline
- 4.5 Lint, Integrations & Vocabularies
- 4.6 The Community Asset Map

**Part V — The Visual Layer & the Site Template**
- 5.0 The visual layer is the equity layer
- 5.1 The JBL reference implementation
- 5.2 Template grammar
- 5.3 The Site-Map Sheet as intended state

**Part VI — The Technical Architecture (Claude runtime)**
- 6.0 The stack
- 6.1 Execution hosts
- 6.2 MCP servers
- 6.3 Browser automation & the API gap
- 6.4 The local bridge
- 6.5 Triggers
- 6.6 The visual-generation engine (NotebookLM first)

**Part VII — Operational Mechanics**
- 7.0 Commit logic & reversible history
- 7.1 CODE framework
- 7.2 Visual Vocabulary
- 7.3 The reconciliation engine
- 7.4 The full lifecycle

**Part VIII — Intellectual Lineage, Drift Control, Scale & Deployment**
- 8.0 The five canonical books
- 8.1 The six drifts & lint discipline
- 8.1b Feedback loop & quarterly audits
- 8.2 Fractal growth
- 8.3 The deployment arc (cloud → local-first → physical)
- 8.4 The workshop funnel & proof artifacts

**Appendices** — A. Bootstrap · B. Variables · C. Block types · D. Integrations inventory · E. Skills

---

# Part I — The Central Inversion & Strategic Foundation

## 1.0 The substrate is the system; the AI is not

Most AI deployments put the model at the center and treat data as something the model
consumes. This system does the opposite. The **relational substrate** — Google Sheets holding
entities, events, and relations — is the durable, authoritative core. The AI is a maintenance and
synthesis layer that reads from the substrate and writes back to it. Swap the model (Claude,
Gemini, a local open-weights model on a NAS) and the substrate is untouched: schema, rules,
visual conventions, and accumulated data all survive, because they were never inside the model.

The practical consequence for a partner: **value compounds in the data the organization owns,
not in the model.** That is the opposite of most AI products, where value evaporates when the
vendor changes terms. The substrate had to be designed first and carefully, before any
automation; everything downstream is a projection of it. If the substrate is sound, projections
regenerate freely. If it is muddled, no model quality fixes it.

This is also why the system is **pre-code first** (`RES-COMMIT-001`): the Workspace substrate
produces value before any AI is added. AI accelerates; it does not enable. Forgetting this is
`DRIFT-05`, and the architecture is built to refuse it.

## 1.1 The problem this is built against

The communities served — immigrant/refugee organizations, BIPOC small business owners,
formerly incarcerated workers, the nonprofit staff serving them — are locked out of the AI wave
for a reason rarely named precisely: every dominant tool assumes a specific cognitive posture
(an individual, alone, in text, through a prompt, who has *already* organized their thinking well
enough to ask a good question). Obsidian looks like a developer tool; a chatbot is a blank box
demanding the literacy it claims to teach. The one sufficiently powerful relational system these
communities already trust and operate daily is **Google Workspace** — email, Docs, Sheets,
Forms, Calendar. The relational power is hidden under familiar surfaces.

## 1.2 The Clarity Gap and the equity wedge

The Clarity Gap — intent degrading as a project moves founder → manager → designer →
developer — is closed by using AI as the translator. The deeper wedge: **AI-grade data
infrastructure operated by people who don't know they're operating it.** A volunteer fills out a
Form; that becomes a row in a Sheet, a reference in a Doc, a section on a Site. They did data
entry; the system did the relational work — and they never had to touch the AI.

## 1.3 The Organism Metaphor (substrate-first)

| Organ | Role | Implementation (substrate-first) |
|---|---|---|
| **Brain / spine** | structured truth | Google Sheets substrate — **the system itself** |
| **Memory** | raw assets | Google Drive |
| **Body** | presentation (a projection) | Google Sites |
| **Map** | spatial projection | Google My Maps |
| **Nervous System** | the accelerator | **AI (Claude / Gemini / local) — replaceable** |
| **Hands** | UI interaction where no API exists | Claude in Chrome / computer use; Stagehand/Playwright fallback |
| **Connective tissue** | tool access | MCP servers |

The substrate does not move when the model changes. That is the whole point.

## 1.4 Claude as one replaceable runtime

This edition documents the **Claude runtime** because it is what we operate today, and because
Claude's strengths fit the work: Skills are first-class and portable (the SBDC meeting-note skill
was the first); MCP closes Google's API gaps; the Agent SDK gives real orchestration; and
Claude's training rewards flagging unverified work, which matches the QA discipline. **But none
of this is load-bearing for the architecture.** `RES-COMMIT-007` (model-agnostic) means Gemini
or a local model could fill the same roles. Claude is the current accelerator, not the system.

---

# Part II — The Governance Model

## 2.0 Constitutional AI: the Governing Codex

The Codex (strategic priorities, voice, boundaries, brand) is implemented as a layered system
prompt + `CLAUDE.md` (auto-loaded by Claude Code/Cowork each session) + a `governing-codex`
Skill carrying the longer doctrine (style guide, visual vocabulary, the principle/drift library).
Before any action, an agent filters it through the constitution and self-corrects or refuses on
conflict — enforced by instruction-following plus hooks that can hard-block a tool call.

## 2.1 Dual-Layer Communication: Narrative + Framework

Every action generates two records: **Layer 1 — Narrative** (low-fog, plain language) and **Layer
2 — Framework** (the SME tag: RACI / SWOT / Stakeholder Analysis, or one of the ~31 named
principles in `RESOURCES`). This is the surviving DNA of the original SBDC meeting-note skill,
now written by Claude and logged to `Project_Narrative_Log`. Never write one layer without the
other.

## 2.2 The Check Your Work Ethic: Visual QA as Law

A task is not done when the code is valid; it is done when the UX is verified. The QA Auditor
launches a browser, sets 375px and 1440px viewports, captures screenshots, and reads them
with vision; on contrast/overlap failure it rejects its own work and loops; three strikes trigger
rollback. Failures it cannot resolve are logged to `LINT_FINDINGS`, not hidden.

## 2.3 The no-ghostwrite compliance boundary

`RES-COMMIT-010` (the EDI contract rule): **the AI assists, structures, reviews, and visualizes —
it does not author the work that must be the client's own.** Helping an applicant structure,
critique, and visualize *their own* grant narrative is allowed; drafting the narrative for them is
not. This governs everything the synthesis layer produces whenever it touches funded
technical-assistance work, and it is stored as an architectural commitment so the constraint
travels with the system rather than living only in a contract someone must remember.

---

# Part III — The Organizational Structure (model-agnostic roles)

## 3.0 Agents as subagents + Skills

Each agent is a subagent (own context, system prompt, allowed tools) carrying Skills that encode
its SOPs. The Orchestrator enforces the chain. The roles are the R01–R10 roles from the
Blueprint; the table below shows the **Claude runtime** binding — another runtime would map the
same roles to its own models.

| Agent | Role | Writes to | Claude model |
|---|---|---|---|
| Historian | PM | `Project_Narrative_Log`, `EVENTS` | Opus 4.7 |
| Librarian | Info Architect | type sheets, `RELATIONS`, `VISUAL_ARTIFACTS` | Sonnet 4.6 |
| Creative Director | UX/UI | `SITE_CONTENT_BLOCKS`, `VISUAL_ARTIFACTS` | Opus 4.7 |
| QA Auditor | QA | QA status, `LINT_FINDINGS` | Sonnet 4.6 |
| Orchestrator | DevOps | sync logs, dispatch | Sonnet 4.6 |

Haiku 4.5 handles cheap classification.

## 3.1 The Project Historian
Guardian of context; only writer of Narrative/Strategy. Runs the 5W Interrogation, applies
frameworks, performs Progressive Summarization (raw → key quotes → 3-bullet executive), and
writes a **Commit** paired with an **Event** row (every commit is, in graph terms, an event with
participants and provenance).

## 3.2 The Librarian
Fights entropy. Content-scans new files (vision), canonical-renames, files the master, and creates
one-to-many references. In this edition the Librarian also mints `VIS-` rows for visual artifacts
and maintains relations — a new file about a person updates that person's dossier and
`RELATIONS`, not just `Content_Assets`. Reaches Drive via the Drive MCP or Drive for Desktop.

## 3.3 The Creative Director
Turns data into visible experience: copy in the Codex voice, Visual Vocabulary selection, brand
enforcement, layout, block insertion, proof pairing. Emits structured block instructions; does not
click the editor. **Visual generation is delegated** (Part VI.6) — it writes the spec, an engine
produces the asset, the result is registered as a `VIS-` artifact.

## 3.4 The QA Auditor
The only agent with veto. Viewport sim, screenshot, WCAG contrast, layout-regression, pass/fail
ticketing, and **lint**: it writes contradictions, stale claims, orphans, and drift-correction-needed
items to `LINT_FINDINGS` for human review.

## 3.5 The Orchestrator
Agent SDK root agent. Resolves the project via `MASTER_REGISTRY`, dispatches **Librarian →
Historian → Creative Director → QA Auditor**, enforces sequencing, handles errors (retry/skip/
escalate), and triggers rollback on repeated QA failure. Hooks give hard control points (e.g.,
pre-publish blocks unless QA status = `Verified`).

---

# Part IV — The Substrate: The Relational Knowledge Graph

The substrate is a normalized (3NF) schema in plain Google Sheets — standard database
discipline, operable by non-technical people because the surface is just spreadsheet tabs.

## 4.0 The Master Registry and typed IDs

One **`MASTER_REGISTRY`** sheet is the spine — *a phone book, not a profile*. Columns:
`entity_id` (`TYPE-#####`), `entity_type`, `display_name`, `created_date`, `created_by`, `status`,
`dossier_doc_url`, `notes`. **IDs are stable; names are not** — every cross-reference points at
the ID. Prefixes: `PER- ORG- PLA- PRJ- RES- EVT- VIS-`.

## 4.1 The seven entity types

Each is its own sheet keyed back to the registry: **PEOPLE, ORGANIZATIONS, PLACES,
PROJECTS, RESOURCES, EVENTS, VISUAL_ARTIFACTS.** (v2.0 had six; `VISUAL_ARTIFACTS` is
the seventh — see 4.3.) Each carries only the fields relevant to its type; a unified mega-table is
explicitly rejected.

## 4.2 Events & Relations (mandatory provenance)

**`EVENTS`** is the keystone: a bounded occurrence (meeting, introduction, workshop, submission)
with participants, date, project context, and `source_doc_url`. *"I introduced Jerry to the two
Northeastern interns"* is **one event** that implies relations — not three free-floating relations.
Events also carry `produced_by_agent` / `produced_by_skill` (Codex R-/S- IDs).

**`RELATIONS`** is the connective tissue: each row one connection between two IDs, with a
controlled-vocabulary `relation_type`. The hard rule: **every relation cites a `source_event_id`**
(required field). The chain is relation → event → document → the moment in the world. It is a
bibliography baked into the data model. Vocabulary stays small and grows only on purpose
(`Employed by`, `Located at`, `Involved in`, `Introduced to`, `corrects_drift`, `derived_from_book`,
`external_validates`, `Connected to` used sparingly, etc.).

## 4.3 Visual Artifacts as first-class data

`VISUAL_ARTIFACTS` (`VIS-`) makes the visual layer queryable. Each infographic, dashboard, map
view, slide deck, or audio/video overview is a row recording what it consolidates
(`source_entity_ids`, `source_event_ids`, `source_query`), how it was generated (`generated_by`,
`generation_method`), its `cognitive_format`, `compression_ratio`, `accessibility_alt_text`, and
embed/thumbnail URLs. Visuals persist, version with their data, regenerate when the data
changes, and appear as thumbnails in the backlink tabs of every entity they reference — so a
dossier is a **multimodal** index, not a text list.

## 4.4 Dossiers, backlinks & the staleness discipline

Every entity has a **dossier Google Doc** (canonical home; URL in the registry) with flat
canonical tabs. **Human-written and system-generated tabs never mix** (hard rule). Universal
tabs: `Profile`, `Mentions & Connections` (auto backlinks), `Resources & Files`, `Notes & Scratch`
(human-only). Type-specific tabs per the entity kind. Auto tabs are marked and **never silently
overwrite** a human edit — they preserve and flag it.

**Backlinks** (Notion/Roam pattern): content lives in one place; `Mentions & Connections`
auto-populates from `RELATIONS`/`EVENTS` with date, summary, source link, project tags, and
`VIS-` thumbnails. Write once; discoverability propagates.

**Staleness discipline (`RES-COMMIT-008`):** a 180-day threshold (a single editable commitment
in the substrate). On regeneration, any relation without a confirming event inside the window is
flagged "last confirmed on [date]" — **never deleted**. The system may remember; it may not
pretend old facts are fresh.

*Claude-runtime note:* Google's Docs API cannot create tabs programmatically. Dossier-tab
writes go through Drive for Desktop (local edit, synced back) or the browser path — the same
mechanism as Sites. Validate whether a locally-edited `.docx` syncs as a true tab or a section.

## 4.5 Lint, Integrations & Vocabularies

- **`LINT_FINDINGS`** — the system logs its own integrity problems (contradictions, superseded
  claims, orphan entities, drift-correction-needed) with severity and status, for human review. It
  starts empty and fills as the system runs. *The system surfaces its own decay rather than hiding
  it.*
- **`INTEGRATIONS`** — one inventory of every external dependency, each with auth status, cost
  model, **failure mode, and fallback** (Appendix D). Doubles as the technical-architecture
  appendix for funders.
- **`VOCABULARIES`** — canonical value lists for every enum column. Keep tight; **vocabulary
  explosion kills a relational system.**

## 4.6 The Community Asset Map

`PLACES` with `lat`/`lng` project onto **Google My Maps**, linked by the same IDs. Limited write
API → treated as lightly-synced / often-manual.

---

# Part V — The Visual Layer & the Site Template

## 5.0 The visual layer is the equity layer

"A picture is worth a thousand words" is treated literally, as a statement about cognitive
bandwidth. For a time-rich knowledge worker the text/visual gap is a convenience; for a volunteer
with fifteen minutes between client meetings it is the difference between "usable" and "not for
me." A good visual is **consolidation, not abstraction** (`RES-COMMIT-004`): it concentrates the
whole dataset into a glance with the full substrate preserved underneath. This rewards the visual
and collaborative fluency these communities have and the prompt-driven paradigm ignores.

## 5.1 The JBL reference implementation

The Joe Brazil Legacy site (`jbl.blackfoxstudios.org`, funded 4Culture — `RES-PROOF-003`) is the
gold standard and established the site grammar. Persistent elements + four pages: **Home**
(overview), **Stage 1** (show your work), **Stage 2** (receipts), **Development Docs** (breadcrumb).

## 5.2 Template grammar

~12 block types (heading, paragraph, bulleted_list, image, image_with_caption, external_link,
internal_link, drive_file_embed, drive_folder_embed, drive_sheet_link, calendar_button,
embedded_website) and ~20 per-client variables (Appendix B). **Proof pairing is law:** every
claim sits beside an embedded proof object.

## 5.3 The Site-Map Sheet as intended state

Each project's `SITE_PAGES` + `SITE_CONTENT_BLOCKS` sheets are the *intended state*; the Site
is the *projection*; automation reconciles the Site to match. Idempotent, recoverable, editable by
anyone who can edit a Sheet. Every block carries `source_event_id` + `source_entity_ids`, so
publishing also updates the backlink tabs of referenced entities. `SITE_SYNC_LOG` records every
run, flags manual-edit drift, and makes failures visible.

---

# Part VI — The Technical Architecture (Claude runtime)

## 6.0 The stack

| Layer | Tool | Role |
|---|---|---|
| Operator surface | Claude Desktop (Cowork) | non-dev mission control (Mac; Max tier) |
| Developer surface | Claude Code (CLI) | scripted mission control; cross-platform |
| Intelligence | Claude Opus 4.7 / Sonnet 4.6 / Haiku 4.5 | the accelerator (replaceable) |
| Agent framework | Claude Agent SDK | orchestration, subagents, hooks |
| Capability unit | Claude Skills | SOPs, voice, templates |
| Tool access | MCP servers | Drive, custom write, browser, image |
| Hands | Claude in Chrome / computer use | UI automation (Stagehand/Playwright fallback) |
| Local bridge | Drive for Desktop | sync shared drives as local files |
| Visual engine | **NotebookLM** (pre-code) | Studio visual consolidations; Imagen/local SDXL fallback |
| Substrate | Sheets / Docs / Drive / Sites / My Maps | the system + its projections |

## 6.1 Execution hosts
Build and schedule on **Claude Code** (cross-platform, holds Skills/`CLAUDE.md`/the SDK
orchestrator); expose daily flows to the human via **Cowork** (Mac/Max) or a ChatOps trigger on
any platform.

## 6.2 MCP servers
The answer to "Google didn't ship an API": **Drive/Docs/Sheets MCP** (cloud ops; no tab create),
a **custom write MCP** (privileged writes when stock is read-only — the same pattern that pushes
this repo), a **browser MCP** (Sites + Docs tabs via the front end), and an **image MCP**
(NotebookLM/Imagen/local). Each independently disable-able.

## 6.3 Browser automation & the API gap
Several Google products have no public write API (Docs tabs are read-only via API; Sites has no
meaningful write API). This is a structural fact, not a bug to hide. The correct pattern: the Sheet
is the intended state; automation reconciles the Site to match, driven primarily by **Claude in
Chrome / computer use** (resilient to UI change) with Stagehand/Playwright as the scripted
fallback. A broken Site sync degrades to "the Site is stale," never "the data is lost," because the
Sheet holds truth.

## 6.4 The local bridge
**Drive for Desktop** syncs the shared drive to local files; Claude edits local files and Google
syncs them back, sidestepping API fights for Doc bodies and many Drive ops. (Honest limit: true
Docs *tabs* may sync as sections — validate per use; fall back to the browser path if true tabs are
required.)

## 6.5 Triggers
Trigger-agnostic engine: **Drive folder drop**, **scheduled scan** (zero new content = zero cost),
**ChatOps** (replaces v1.0's ThinkPad+Pub/Sub with a Claude-hosted listener; Google Chat
optional front-end), and **manual edit anywhere** (drift detected → reconcile).

## 6.6 The visual-generation engine (NotebookLM first)

**No AI model here generates images itself — it orchestrates a generator.** The primary,
pre-code engine is **Google NotebookLM** (`RES-TOOL-001`): free, in-Workspace, **source-driven**
(upload material; it makes it navigable — no good-prompt literacy required), and its Studio
outputs map almost exactly onto the Roam six-picture taxonomy and the Forte "Express" step. For
raster image generation specifically, **Gemini/Imagen** (`INT-007`) or a **local Stable Diffusion
XL** equivalent fill the role. The Creative Director writes the spec and sets `auto_generate_image
= true` only where a visual genuinely adds value; the Librarian saves the output and registers a
`VIS-` artifact. When sensitive data must stay local, the same role runs on-prem — the
architecture is identical; only the runtime moves.

---

# Part VII — Operational Mechanics

## 7.0 Commit logic & reversible history
No change to a projection without a Commit (timestamp, `Commit_ID`, source, narrative,
framework tag, QA status), paired with an Event so the log and the graph share provenance. The
ID is a rollback handle.

## 7.1 The CODE framework
Capture → Organize → Distill → Express (`RES-PRIN-008`, Forte). Text is the method of last resort.

## 7.2 The Visual Vocabulary
Deterministic data→design (Roam, `RES-PRIN-017`): dates→timeline/Gantt · coordinates→map ·
finance→chart · process→flowchart · concept→summary card · vendor→embedded site ·
files→Drive grid. Rendering via Google Charts/Looker/Mermaid; imagery via the 6.6 engine.

## 7.3 The reconciliation engine
**Any surface can be the input.** Manual edits are first-class (`RES-COMMIT-006`), not exceptions.
One engine, many triggers: read the change → resolve entities → determine affected surfaces →
generate updates → write via API where possible, queue browser automation where not → log to
`SITE_SYNC_LOG`. Every path idempotent, retryable, independently disable-able, failures visible.

## 7.4 The full lifecycle
Capture → Organize (Librarian: files + relations + event + any `VIS-`) → Distill (Historian:
commit + event + framework tag) → Express (Creative Director: blocks + visual spec) → Audit (QA:
375/1440 + lint) → Publish & Confirm (status `Verified`; backlinks refreshed in every referenced
dossier). Target ~4 minutes, ~15 seconds of human effort.

---

# Part VIII — Intellectual Lineage, Drift Control, Scale & Deployment

## 8.0 The five canonical books

The Visual Second Brain is a synthesis of five established methodologies, stored as
`canonical_book` resources with their ~31 principles (`RES-PRIN-*`) so any deliverable can be
tagged to the principle it derives from — making the lineage *queryable*, not merely cited:

- **Osterwalder, *Business Model Generation*** (`RES-BOOK-001`) — the BMC used as a **reading**
  tool for any external entity; gives the dossier its structure.
- **Forte, *Building a Second Brain*** (`RES-BOOK-002`) — CODE + PARA; externalize thinking into
  a retrievable substrate that outlives memory.
- **Roam, *The Back of the Napkin*** (`RES-BOOK-003`) — the six-picture visual taxonomy and the
  empirical case for visual cognition; foundation of the visual layer.
- **Gerber, *The E-Myth Revisited*** (`RES-BOOK-004`) — Technician/Manager/Entrepreneur
  decomposition and the franchise-prototype discipline; turns individual work into portable
  operations.
- **Ries, *The Lean Startup*** (`RES-BOOK-005`) — Build-Measure-Learn and innovation
  accounting; the iteration discipline.

The through-line is **portability**: each book turns a capacity that normally requires an
exceptional individual into a teachable method, so the community member need not be a designer,
strategist, ops expert, knowledge manager, or lean practitioner — the methods carry those
capacities.

## 8.1 The six drifts & lint discipline

Six named **drifts** (`RES-DRIFT-01..06`) are recurring ways the concept gets distorted — AI as
the engine not the accelerator (`01`); axis conflation (`02`); treating the EDI Playbook as separate
from the workshop (`03`); losing the "getting a job is a job" frame (`04`); forgetting the pre-code
foundation (`05`); conflating BMC building with BMC reading (`06`). They are stored as entities; a
`corrects_drift` relation lets any artifact be checked against them, and `LINT_FINDINGS` surfaces
drift-correction-needed items. If a request or output starts treating the AI as the system or
skipping pre-code, **name the drift and self-correct.**

## 8.1b Feedback loop & quarterly audits
QA rejections are tagged by failure type; recurring patterns trigger a Codex parameter update
(e.g., raise min body font) that the next run reads — muscle memory, implemented as a Skill that
edits the `governing-codex` Skill. Quarterly, a human reads the Narrative Log as a story, looks for
Strategic Dissonance, and updates the Codex via a Strategic Commit.

## 8.2 Fractal growth
A project is a cell: one registry entry + one Drive folder + one Site + its site-map sheets. New
client = clone the cell. Defensibility is **the trained, networked community as distribution
channel** (`RES-COMMIT-002`), not a technical moat.

## 8.3 The deployment arc (cloud → local-first → physical)
- **Today — pre-code, cloud.** Workspace + NotebookLM, free. Proven: the EDI Playbook
  (`RES-PROOF-002`) is a paid, compliant City of Seattle contract running almost entirely on
  pre-code Workspace; the 2023 case study (`RES-PROOF-001`) moved interview conversion
  2.86% → 35.29% as a clean Lean experiment. *Precise claim:* the substrate is the structured
  **evolution** of that Form→Sheet→Doc flow, not something those proofs already implement.
- **Near future — local-first.** Sensitive client data reasoned over on an on-prem **NAS** with
  open-weights models (`RES-COMMIT-003`); collaborative surfaces stay in Workspace. Data
  sovereignty as a survival requirement, aligned with where regulation is heading.
- **Later — physical interfaces.** Projected surfaces and ambient capture; downstream of a stable
  substrate, not a prerequisite.

## 8.4 The workshop funnel & proof artifacts
"Google and AI for Business" teaches the *manual* version of everything the system automates,
establishing the Clarity Gap; the automated system is the upsell. Proof artifacts are first-class
resources (`RES-PROOF-001..006`), including the Codex and Blueprint themselves.

---

# Appendices

## Appendix A — Bootstrap Protocol (Claude runtime)
1. Confirm `CLAUDE.md` is loaded; MCP servers connected (Drive, custom write, browser, image);
   Drive for Desktop syncing; the four subagents + Skills registered.
2. Verify the root Drive folder; build the substrate workbook: `MASTER_REGISTRY`, the seven type
   sheets, `RELATIONS`, `EVENTS`, `VISUAL_ARTIFACTS`, `LINT_FINDINGS`, `INTEGRATIONS`,
   `VOCABULARIES`, `Project_Narrative_Log`, `Content_Assets`. Seed `RESOURCES` with the five
   books, principles, drifts, commitments, proofs.
3. Per project: `SITE_PAGES`, `SITE_CONTENT_BLOCKS`, `SITE_SYNC_LOG`.
4. Librarian crawl: register entities, mint typed IDs, write metadata + alt text, build dossiers from
   per-type templates. Establish triggers (drop, scan, ChatOps, manual-edit drift).

## Appendix B — Template Variable Reference
`{{client_name}}`, `{{client_short}}`, `{{consultant_name}}`, `{{partner_orgs}}`, `{{site_url}}`,
`{{project_strategy_pdf}}`, `{{hero_image_main}}`, `{{narrative_paragraph}}`,
`{{strategic_pillars}}`, `{{stage_1_name}}`, `{{stage_1_slides}}`, `{{vendor_partner_url}}`,
`{{stage_2_name}}`, `{{stage_2_drive_folder_id}}`, `{{stage_2_sheet_id}}`,
`{{development_docs}}`, `{{calendar_booking_url}}`, `{{consultant_contact}}`.

## Appendix C — Block Type Vocabulary
`heading`, `paragraph`, `bulleted_list`, `image`, `image_with_caption`, `external_link`,
`internal_link`, `drive_file_embed`, `drive_folder_embed`, `drive_sheet_link`, `calendar_button`,
`embedded_website`. Proof-pairing mandatory.

## Appendix D — Integrations Inventory (`INTEGRATIONS` sheet)

| ID | Service | Purpose | Failure mode | Fallback |
|---|---|---|---|---|
| INT-001 | Google Sheets API | the substrate | writes fail | manual edit |
| INT-002 | Google Drive API | files, dossiers, triggers | ops fail | manual Drive ops |
| INT-003 | Google Docs API | dossier bodies (no tab write) | tab write unsupported | append section / browser |
| INT-004 | Google Sites (no API) | public hubs | no programmatic write | browser automation |
| INT-005 | Google My Maps | asset map | limited write | manual pins |
| INT-006 | NotebookLM | pre-code visual engine | generation fails | manual Slides / Imagen / local |
| INT-007 | Gemini / Imagen | image generation | gen fails | local SDXL / hand-drawn |
| INT-008 | Stagehand | Sites/Docs-tab browser writes | breaks on UI change | Playwright/Puppeteer |
| INT-009 | Otter.ai | transcription | unavailable | manual notes |
| INT-010 | Neoserra (WA SBDC) | compliance CRM | no import | **manual indefinitely** |

## Appendix E — Skill Inventory (Claude Skills ↔ Blueprint S01–S42)
Historian: `transcript-synthesis`(S01), `5w-interrogation`(S02), `okr-alignment`(S03),
`raci-tagging`(S04), `narrative-commit`(S05), `quarterly-review`(S06), `codex-version`(S07),
`strategic-commit`(S08). Librarian: `content-scan`(S09), `taxonomy-routing`(S10),
`canonical-rename`(S11), `cross-link`(S12), `content-assets-entry`(S13), `image-alt-text`(S14),
`schema-design`(S15), `project-tab-gen`(S16), `validation-formatting`(S17). Creative Director:
`section-copywriting`(S18), `visual-vocabulary`(S19), `visual-spec`(S20 — spec only; engine
generates), `brand-enforcement`(S21), `layout-composition`(S22), `block-insertion`(S23),
`proof-pairing`(S24). Site Builder: `template-clone`(S25), `multi-page`(S26), `browser-drive`
(S27), `playwright-fallback`(S28). QA Auditor: `viewport-sim`(S29), `screenshot`(S30),
`wcag-contrast`(S31), `layout-regression`(S32), `passfail-ticket`(S33), `rejection-pattern`(S34),
`param-self-tune`(S35), plus `lint-scan` (contradictions/stale/orphans → `LINT_FINDINGS`).
Infra/Orchestrator: `trigger-listen`(S36–S38), `job-dispatch`(S39), `agent-sequencing`(S40),
`error-handling`(S41), `site-rollback`(S42).

The SBDC meeting-note generator — the first Skill built — is the canonical voice template all
Historian/Creative Director copy inherits from.

— End of Document —
