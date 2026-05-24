# BLACK FOX STUDIOS

## The Antigravity CMS Operating Codex — Claude-Native Edition

**A Comprehensive Blueprint for Autonomous, Agentic Google Sites Project Management & Client Consulting, Executed on Claude**

Prepared by Andrew Powers — Founder, Black Fox Studios | SBDC Advisor, Highline College — andrew@blackfoxstudios.org

**Version 2.0 — Claude-Native Rewrite** | CONFIDENTIAL — Internal & Partner Use Only

> **What changed from v1.0.** The original Codex and Organizational Blueprint described the
> same organism running on the Google Antigravity IDE with Gemini as the brain. This edition
> keeps every philosophy, every agent role, and the full Visual Second Brain methodology
> intact, but re-platforms the execution layer onto **Claude** — Claude Code, Claude Desktop
> (Cowork), Claude Skills, the Claude Agent SDK, and MCP servers — and folds back in the
> **relational knowledge-graph layer** (entities, relations, events, dossiers, backlinks, My Maps)
> that was designed in the founding conversation but left out of v1.0. Where Claude cannot do
> something natively (image generation), this document says so plainly and routes around it.

---

## Table of Contents

**Part I — Philosophy & Strategic Foundation**
- 1.0 The Manifesto: Documentation Is Production
- 1.1 The Clarity Gap and How We Close It
- 1.2 The Organism Metaphor (re-mapped to Claude)
- 1.3 Why Claude Is the Right Brain for This Organism

**Part II — Governance Model**
- 2.0 Constitutional AI: The Governing Codex as a Claude System Prompt
- 2.1 Dual-Layer Communication: Narrative + Framework
- 2.2 The Check Your Work Ethic: Visual QA as Law

**Part III — The AI Organizational Structure on Claude**
- 3.0 Agents as Claude Subagents + Skills
- 3.1 The Project Historian
- 3.2 The Librarian
- 3.3 The Creative Director
- 3.4 The QA Auditor
- 3.5 The Orchestrator

**Part IV — The Data Model: The Relational Knowledge Graph**
- 4.0 The Master Registry and Typed IDs
- 4.1 The Six Entity Types
- 4.2 Relations and Events (provenance + the "bibliography" property)
- 4.3 Dossier Docs and Auto-Backlinks
- 4.4 The Community Asset Map (Google My Maps)

**Part V — The Consulting Process & Site Template**
- 5.0 The Visual Second Brain
- 5.1 The JBL Reference Implementation
- 5.2 Template Grammar: Pages, Blocks, Variables
- 5.3 The Site-Map Sheet as Intended State

**Part VI — The Claude Technical Architecture**
- 6.0 The Claude-Native Stack
- 6.1 Execution Hosts: Claude Code vs. Cowork
- 6.2 MCP Servers: The Connective Tissue
- 6.3 Browser Automation the Claude Way
- 6.4 The Local Bridge: Drive for Desktop
- 6.5 Triggers: How Work Starts
- 6.6 The Image-Generation Honesty Section

**Part VII — Operational Mechanics**
- 7.0 Commit Logic and Reversible History
- 7.1 The CODE Framework
- 7.2 The Visual Vocabulary
- 7.3 The Reconciliation Engine: Any Surface as Input
- 7.4 The Full Lifecycle: From Voice to View

**Part VIII — Iteration, Scale & Change Management**
- 8.0 The Feedback Loop
- 8.1 Quarterly System Audits
- 8.2 The Fractal Growth Model
- 8.3 The Workshop Integration

**Appendices**
- A. Bootstrap Protocol (Claude-native initialization)
- B. Template Variable Reference
- C. Block Type Vocabulary
- D. MCP Server Inventory
- E. Skill Inventory (Claude Skills mapped to v1.0 skills S01–S42)

---

# Part I — Philosophy & Strategic Foundation

## 1.0 The Manifesto: Documentation Is Production

Nothing in the founding philosophy changes because the model changed. Production is not a
phase that happens after thinking; the act of documenting a decision is the mechanism that
triggers the work. If a decision is made but not logged, it did not happen. If a change is
deployed but not visually verified, it is reckless. The documentation **is** the production.

What Claude adds is a more honest relationship with that axiom. Claude is trained to refuse to
mark work complete on the basis of "the code ran." It is comfortable saying "I did X but could
not verify Y," which is exactly the posture the Check Your Work Ethic demands. The model's
disposition matches the doctrine.

## 1.1 The Clarity Gap and How We Close It

The Clarity Gap — the degradation of intent as a project moves from founder to manager to
designer to developer — is unchanged. We still serve small businesses and nonprofits in South
King County, many burned by consultants who could not translate between what the client knows
and what a system needs. AI is still the translator; the consultant still manages the AI, not the
client.

The Claude-native difference: the translator now runs in environments a non-developer can
actually operate. v1.0 leaned on the Antigravity IDE, which — as was correctly observed in the
founding conversation — is "designed as if someone's very skilled and knows how to use IDEs."
Claude Desktop's Cowork mode is explicitly built for the opposite user: point it at folders,
describe an outcome, approve consequential steps. That design choice is itself a closing of the
Clarity Gap at the tooling layer, not just the content layer.

## 1.2 The Organism Metaphor (re-mapped to Claude)

| Organ | v1.0 (Gemini/Antigravity) | v2.0 (Claude-Native) |
|---|---|---|
| **Brain** (structured truth) | Google Sheets | Google Sheets — unchanged (substrate is still Google) |
| **Memory** (raw assets) | Google Drive | Google Drive — unchanged |
| **Body** (presentation) | Google Sites | Google Sites — unchanged |
| **Nervous System** (the agents) | Gemini agents in Antigravity | **Claude** (Opus/Sonnet/Haiku) as subagents + Skills, hosted in Claude Code / Cowork |
| **Mission Control** (the host) | Antigravity IDE | **Claude Code** (developer surface) **+ Claude Desktop / Cowork** (operator surface) |
| **Hands** (UI interaction) | Stagehand / Puppeteer | **Claude in Chrome / computer use**, with Playwright-via-MCP as the scripted fallback |
| **Connective tissue** (tool access) | direct API calls | **MCP servers** (Google Drive MCP, custom write MCP, browser MCP) |

The substrate — Sheets, Drive, Sites, My Maps — does not move. Google still provides free
hosting, collaboration, and a stack the client already trusts. What changes is the nervous system
and the hands.

## 1.3 Why Claude Is the Right Brain for This Organism

1. **Skills are first-class and portable.** A Claude Skill (a `SKILL.md` plus reference files) is
   exactly the unit this system is built from — the SBDC meeting-note generator was the first one.
   Skills are model-invoked, version-controllable, and run identically in Claude chat, Claude
   Code, and Cowork.
2. **MCP is the answer to Google's API gaps.** Where v1.0 hit walls (Docs tabs, Sites), MCP lets
   us bolt on exactly the capability we need — a custom write server, a browser server — without
   waiting for a vendor API.
3. **The Agent SDK gives us real orchestration.** Subagents, hooks, and context management
   replace the Antigravity "Agent Manager" with something programmable and testable.
4. **Honest verification.** Claude's training rewards flagging unverified work, which is the
   keystone of the QA discipline.

The one thing Claude does **not** do is generate images. Part VI.6 handles this directly.

---

# Part II — The Governance Model

## 2.0 Constitutional AI: The Governing Codex as a Claude System Prompt

The Governing Codex — strategic priorities, tonal voice, operational boundaries, brand
standards — is implemented as a **layered Claude system prompt + a `CLAUDE.md` file +
project Skills**:

- **`CLAUDE.md`** at the repo/project root holds the durable constitution. Claude Code and
  Cowork both read it automatically on every session, so the constitution is always in context.
- **A `governing-codex` Skill** carries the longer doctrine (voice rules, style guide, visual
  vocabulary) and is invoked when an agent is about to write client-facing content.
- **The system prompt** (set via the Agent SDK for the orchestrator) carries the inviolable rules
  that must never be overridden.

Before any action, an agent filters the proposed action through this constitution. If a proposed
update conflicts with the Codex, the agent self-corrects or refuses — the same behavior as
v1.0, now enforced by Claude's instruction-following plus explicit hooks that can block a tool call.

## 2.1 Dual-Layer Communication: Narrative + Framework

Unchanged in intent. Every action generates two records:

- **Layer 1 — Narrative (Human Story):** low-fog, plain language. *"The client was worried about
  the timeline, so we updated the Schedule section to show a Q3 completion date."*
- **Layer 2 — Framework (SME Metadata):** *"Framework Applied: Stakeholder Analysis (High
  Power / High Interest); Risk Mitigation (Schedule Slip)."*

This is the surviving DNA of the original SBDC meeting-note skill, which produced exactly this
kind of voice-faithful, structured output. In v2.0 it is generated by Claude (better voice fidelity
than the Gemini summarization step the founding conversation explicitly distrusted) and written
to the `Project_Narrative_Log`.

## 2.2 The Check Your Work Ethic: Visual QA as Law

A task is not done when the code is valid; it is done when the user experience is verified. The
QA Auditor still physically launches a browser, sets the viewport to 375px (mobile) and 1440px
(desktop), captures screenshots, and reads them with vision. The difference: the browser is
driven by **Claude in Chrome / computer use** (or Playwright via MCP), and the screenshots
are analyzed by **Claude's own vision** rather than Gemini Vision. If text overlaps an image or
contrast fails WCAG 4.5:1, the Auditor rejects its own work and loops. Three consecutive
failures trigger a rollback.

---

# Part III — The AI Organizational Structure on Claude

## 3.0 Agents as Claude Subagents + Skills

In v1.0 the four agents were Gemini personas inside Antigravity. In v2.0 each agent is a
**Claude subagent** (its own context window, its own system prompt, its own allowed tool set)
defined through the Agent SDK or as a Claude Code subagent, and each carries one or more
**Skills** that encode its standard operating procedures. The Orchestrator dispatches them in
sequence and enforces the dependency chain.

| Agent | Industry role | Claude implementation | Model |
|---|---|---|---|
| Project Historian | Product Manager | subagent + `historian` skills | Opus 4.7 (judgment-heavy) |
| Librarian | Info Architect | subagent + Drive MCP + `librarian` skills | Sonnet 4.6 (volume) |
| Creative Director | UX/UI Designer | subagent + `creative-director` skills + image MCP | Opus 4.7 (composition) |
| QA Auditor | QA Engineer | subagent + browser MCP + vision | Sonnet 4.6 (vision) |
| Orchestrator | DevOps Lead | Agent SDK root loop + hooks | Sonnet 4.6 |

Model selection is a cost/quality lever: Haiku 4.5 handles cheap classification (is this file an
image? which project does this belong to?), Sonnet handles volume and vision, Opus handles
the judgment-heavy synthesis and composition.

## 3.1 The Project Historian

Guardian of context; the only entity allowed to write the Strategy and Narrative columns of the
Project Bible. Runs the **5W Interrogation** (Who/What/Where/When/Why), applies business
frameworks (RACI, SWOT, Stakeholder Analysis), performs **Progressive Summarization**
(Level 1 raw → Level 2 key quotes → Level 3 three-bullet executive summary), and writes a
**Commit** to `Project_Narrative_Log`. In v2.0 the Historian also writes **Event** rows (Part IV)
because every commit is, in knowledge-graph terms, an event with participants and provenance.

## 3.2 The Librarian

Fights entropy. Content-scans every new file (Claude vision reads PDFs, images, sheets),
applies taxonomy routing from the Codex, renames to canonical `YYYY-MM-DD_Type_Name_vNN.ext`,
files the master copy, and creates **one-to-many** references across the database. In v2.0 the
Librarian's reach extends to the full entity model: a new file about a person updates that
person's dossier and the relations table, not just `Content_Assets`. It reaches Drive through the
**Google Drive MCP** for cloud operations and through **Drive for Desktop** for local file edits.

## 3.3 The Creative Director

Turns data into visible experience. Copywriting in the Codex voice, **Visual Vocabulary**
selection (timelines→Gantt, locations→maps, finance→charts, concepts→cards), brand
enforcement against the Style Guide, layout composition against the JBL template, block
insertion, and **proof pairing**. It does not click the editor itself — it emits structured block-
insertion instructions that the browser-automation layer executes. **Image generation is
delegated** to an external model (Part VI.6); Claude writes the prompt and orchestrates, an
image API produces the asset.

## 3.4 The QA Auditor

The only agent with veto power. Viewport simulation (375/1440), screenshot capture, WCAG
contrast analysis, layout-regression detection, and pass/fail ticketing to the Narrative Log. Built
on the **browser MCP / Claude in Chrome** plus Claude vision. On pass → publish + status
`Verified`; on fail → defect ticket back to the Creative Director; three strikes → Orchestrator
rollback.

## 3.5 The Orchestrator

The traffic controller, implemented as the **Agent SDK root agent**. Receives the trigger,
resolves the project via `Master_Index`, and dispatches the chain: **Librarian → Historian →
Creative Director → QA Auditor**. Enforces sequencing with the dependency rule (no building
before organizing and logging are done), handles errors (retry transient, skip non-critical,
escalate critical), and triggers rollback on repeated QA failure. **Hooks** give it hard control
points — e.g., a pre-publish hook that blocks if QA status is not `Verified`.

---

# Part IV — The Data Model: The Relational Knowledge Graph

> This is the layer the founding conversation designed in depth and v1.0 omitted. It is restored
> here because it is what makes the system a knowledge graph rather than a fancy CRM.

## 4.0 The Master Registry and Typed IDs

One **`MASTER_REGISTRY`** sheet is the spine. Every entity that exists anywhere gets a stable,
immutable, typed ID. Names change; IDs never do.

`MASTER_REGISTRY` columns: `entity_id` (`TYPE-#####`), `entity_type`, `display_name`,
`created_date`, `created_by`, `status`, `dossier_doc_url`, `notes`.

ID prefixes: `PER-` people, `ORG-` organizations, `PLA-` places, `PRJ-` projects, `RES-`
resources, `EVT-` events. Five-digit zero-padded for correct text sort.

The v1.0 `Master_Index` becomes a **view** of `MASTER_REGISTRY` filtered to `entity_type =
Project` — so the project-hub product and the knowledge graph share one spine.

## 4.1 The Six Entity Types

Each type has its own sheet keyed back to the registry by `entity_id` (a foreign key):

- **PEOPLE** — first/last/preferred name, email, phone, role, `primary_org_id`, location,
  relationship type/strength, `last_interaction_date`.
- **ORGANIZATIONS** — official name, short name, type, `primary_location_id`, website,
  relationship type.
- **PLACES** — name, type, address, `lat`, `lng`, `my_maps_pin_url`.
- **PROJECTS** — name, short name, status, dates, `lead_person_id`, `project_site_url`,
  `site_map_sheet_url`, summary.
- **RESOURCES** — name, type (grant/tool/doc/opportunity/event), url, relevant dates.
- **EVENTS** — see 4.2; the keystone.

## 4.2 Relations and Events (provenance + the "bibliography" property)

**`EVENTS`** records bounded occurrences (meeting, introduction, workshop, email, site visit).
Columns: `entity_id` (`EVT-#####`), `event_name`, `event_type`, `event_date`,
`primary_project_id`, `source_doc_url`, `summary`, `notes`. The event's `source_doc_url` is the
actual meeting note / transcript / email where it was recorded.

**`RELATIONS`** is the connective tissue. Every row is one connection and **every relation
traces back to a source event** (`source_event_id` is required — locked decision). Columns:
`relation_id`, `entity_id_a`, `entity_id_b`, `relation_type`, `source_event_id`, `source_doc_url`,
`start_date`, `end_date`, `strength`, `relevant_project_ids`, `created_date`, `created_by`.

Controlled vocabulary for `relation_type` (start small, resist explosion): *Employed by, Located
at, Involved in, Hosted at, Funded by, Uses, Partners with, Introduced to, Connected to.*

This is the "bibliography" property: any fact in the system is one click from the event and the
document that produced it. When you write "I introduced JR to Shreya and Langley about the
hackathon pipeline," that is **one event** producing **several relations**, each citing the event.

## 4.3 Dossier Docs and Auto-Backlinks

Every entity has a **dossier Google Doc** (its canonical home, URL stored in the registry) built
from a per-type template with **flat canonical tabs**:

- **Universal tabs (all dossiers):** `Profile`, `Mentions & Connections` (auto), `Resources &
  Files`, `Notes & Scratch` (human-only).
- **Type-specific tabs:** People → `Meetings & Conversations`, `Context & Background`; Orgs →
  `History & Engagement`, `Key People` (auto); Places → `Events & Activity`, `Geographic
  Context`; Projects → `Timeline & Milestones`, `Participants` (auto), `Site Map Reference`,
  `Deliverables & Documents`; Resources → `Details & Specs`, `Usage & References` (auto);
  Events → `Profile`, `Full Record`, `Outcomes`.

**Hard rule: human-written and system-generated content never mix in the same tab.** Auto
tabs carry a header — *"This tab is auto-generated. Manual edits will be overwritten on next
sync. Use Notes & Scratch for freeform."*

**Backlinks** are the Notion/Roam pattern: content lives in one place; the `Mentions &
Connections` tab in every referenced entity's dossier auto-populates from `RELATIONS`/`EVENTS`
with date, one-line summary, source link, and project tags. You write once; the system
propagates discoverability.

**Claude's role here:** the Docs-tabs API still cannot create tabs programmatically. So dossier
tab writes go through the **same browser-automation path as Sites**, or — preferably — through
**Drive for Desktop**, where Claude edits the local file and Google syncs it back. The system
treats "create/refresh a dossier tab" as just another reconcile target.

## 4.4 The Community Asset Map (Google My Maps)

`PLACES` entities with `lat`/`lng` project onto a **Google My Maps** community asset map,
linked by the same ID system. The map shows entities in spatial relationship; projects link to it
when geography matters. My Maps has only a limited API, so it is treated as a **lightly-synced /
often-manual** surface — written when easy, otherwise updated by hand and reconciled.

---

# Part V — The Consulting Process & Site Template

## 5.0 The Visual Second Brain

Every engagement produces a Google Sites project hub — an internal, visual single-source-of-
truth, not a public marketing site. Four reader needs, four entry points: executive overview,
show-your-work, the receipts, and the breadcrumb trail.

## 5.1 The JBL Reference Implementation

The Joe Brazil Legacy site (`jbl.blackfoxstudios.org`) is the gold standard. Site-level persistent
elements (logo, title `BFS X [CLIENT]`, nav, draft banner, footer contact, calendar CTA) plus the
four pages:

- **Home** — H1 block, hosting statement, hero image, embedded strategy PDF, narrative, four
  sub-sections (Project / Goal / Development / Deliverables), calendar booking button.
- **Stage 1 (Show Your Work)** — stage hero + date, embedded vendor/partner site, repeating
  milestone slides (image + heading + body).
- **Stage 2 (Receipts)** — intro, date, embedded Drive folder grid, embedded Sheet.
- **Development Docs (Breadcrumb)** — H1, intro, hero + date, repeating dated document index.

## 5.2 Template Grammar: Pages, Blocks, Variables

~12 reusable block types (heading, paragraph, bulleted_list, image, image_with_caption,
external_link, internal_link, drive_file_embed, drive_folder_embed, drive_sheet_link,
calendar_button, embedded_website) and ~20 per-client variables (`{{client_name}}`,
`{{stage_1_slides}}`, `{{stage_2_drive_folder_id}}`, etc. — full list in Appendix B).

**Design law — Proof Pairing:** every narrative claim sits next to an embedded proof object the
reader can see, click, and verify without leaving the page.

## 5.3 The Site-Map Sheet as Intended State

Each project has a **site-map Sheet** that is the *intended state* of its Site. The Site is a
*projection*; browser automation only makes the Site match the Sheet. This makes Site updates
idempotent and recoverable, editable by anyone who can edit a Sheet, and writable
programmatically. Two sheets per project:

- **`SITE_PAGES`** — `page_id`, `page_title`, `page_slug`, `parent_page_id`, `page_order`,
  `page_status`, `page_purpose`, `last_published_date`.
- **`SITE_CONTENT_BLOCKS`** — `block_id`, `page_id`, `section_id`, `block_order`,
  `block_type`, `content_text`, `content_image_url`, `content_embed_url`,
  `content_button_url/label`, `source_event_id`, `source_entity_ids`, `source_doc_url`,
  `auto_generate_image` (bool), `created_date`, `last_updated_date`, `status`.

Plus **`SITE_SYNC_LOG`** (`sync_id`, `sync_date`, `triggered_by`, `result`, `drift_detected`,
`notes`) for operational health — every reconcile run is logged, and manual Site edits that don't
match the Sheet are flagged as drift.

Because each block carries `source_event_id` and `source_entity_ids`, publishing to the Site
also updates the backlink tabs of every referenced entity's dossier — the Site becomes another
node in the reconciliation graph.

---

# Part VI — The Claude Technical Architecture

## 6.0 The Claude-Native Stack

| Layer | Tool | Role | Notes |
|---|---|---|---|
| Operator surface | Claude Desktop (Cowork) | non-dev mission control | Mac now, Windows later; Max tier |
| Developer surface | Claude Code (CLI) | scripted mission control | cross-platform; subagents, hooks, skills |
| Intelligence | Claude (Opus 4.7 / Sonnet 4.6 / Haiku 4.5) | the brain | model-per-task cost lever |
| Agent framework | Claude Agent SDK | orchestration, subagents | replaces Antigravity Agent Manager |
| Capability unit | Claude Skills (`SKILL.md`) | SOPs, voice, templates | portable across chat/Code/Cowork |
| Tool access | MCP servers | Drive, write, browser | the connective tissue |
| Hands | Claude in Chrome / computer use | UI automation | Playwright-via-MCP fallback |
| Local bridge | Drive for Desktop | sync shared drives as local files | sidesteps Docs/Sites API gaps |
| Substrate | Sheets / Docs / Drive / Sites / My Maps | Brain/Memory/Body/Map | unchanged from v1.0 |

## 6.1 Execution Hosts: Claude Code vs. Cowork

- **Claude Code** is the build-and-run-it surface: it has the filesystem, runs the Agent SDK
  orchestrator, holds the Skills and `CLAUDE.md`, and is where the system is developed and
  scheduled. Cross-platform (works on Windows, unlike Cowork today).
- **Cowork (Claude Desktop)** is the operator surface for the non-developer day-to-day: point it
  at the project folder, say "format this transcript and update the right client's hub," approve the
  consequential steps. Mac-only research preview today; requires Max.

**Recommendation:** build and schedule on Claude Code; expose the daily-driver flows to the
human through Cowork once on Mac/Max, or through a ChatOps trigger (6.5) on any platform.

## 6.2 MCP Servers: The Connective Tissue

MCP is the v2.0 answer to "Google didn't ship an API." The system uses:

1. **Google Drive/Docs/Sheets MCP** — cloud reads/writes for Drive files, Sheet rows, Doc
   bodies. (Tab *creation* still unsupported by Google's API — see 4.3 / 6.3.)
2. **A custom write MCP** — the lesson already learned in practice: when the stock integration is
   read-only or missing operations, a purpose-built MCP server with the right credentials does the
   writes. (This is the same pattern that pushed this very repo when the default GitHub path was
   read-only.)
3. **A browser MCP** (Playwright/computer-use server) — drives Google Sites and Docs tabs
   from the front end.

Each MCP is independently disable-able, satisfying the graceful-degradation rule: if the browser
MCP breaks, Sheet/Drive writes still work and Site updates fall back to manual.

## 6.3 Browser Automation the Claude Way

Google Sites and Docs-tab creation have no write API. v1.0 used Stagehand/Puppeteer. v2.0
uses **Claude in Chrome / computer use** as the primary path — Claude reasons about the page
visually and clicks like a human, which is more resilient to Google's constant UI changes than
brittle selectors — with **Playwright via MCP** as the scripted fallback for precise, repeatable
actions. Either way the target is the **site-map Sheet's intended state** (5.3), so automation is
idempotent: re-run any time, it just makes the Site match the Sheet.

The same mechanism handles dossier-tab creation (4.3) when Drive for Desktop isn't the
chosen path.

## 6.4 The Local Bridge: Drive for Desktop

The cleanest route around Google's API gaps: install **Drive for Desktop**, which syncs the
shared drive (including the project folders) to local files. Claude Code / Cowork then edit the
**local files**, and Google syncs the changes back to the cloud. No API fight for Doc bodies and
many Drive operations. (Note the honest limit from the founding conversation: Google Docs
*tabs* are a Google-native organizational layer; a locally edited `.docx` may sync as sections
rather than true tabs — so true-tab creation may still need the browser path. Validate per use.)

## 6.5 Triggers: How Work Starts

The reconciliation engine (7.3) is trigger-agnostic. Supported triggers:

1. **Drive folder drop** — a transcript/PDF lands in `01_Inbox`; a folder watcher (Apps Script
   change feed or Drive-for-Desktop file event) fires the Orchestrator.
2. **Scheduled scan** — Claude Code runs on a cadence (cron / scheduled Cowork task),
   checking Sheets and Drive for changes since the last `last_scan` timestamp. Zero new content
   = zero cost.
3. **ChatOps** — a message ("update Project Alpha with the new budget PDF") reaches the local
   host. This replaces v1.0's ThinkPad + Pub/Sub + Google Chat with a simpler Claude-hosted
   listener; Google Chat can still be the front-end if desired.
4. **Manual edit anywhere** — a human edits a Sheet/Doc/Site directly; the watcher detects drift
   and the engine reconciles (the "any surface as input" principle, 7.3).

## 6.6 The Image-Generation Honesty Section

**Claude cannot generate images.** This is the one capability the original Gemini-based design
had natively (Imagen) that the Claude brain does not. The design handles this explicitly:

- Claude (Creative Director) **writes the image prompt** — subject, style, composition, lighting,
  brand mood — and decides *which* blocks warrant a visual (the `auto_generate_image` flag;
  do **not** auto-visualize everything).
- An **external image model produces the asset** via API/MCP — Gemini Imagen remains a
  perfectly good choice and is already in the Google stack, or any image API can be wired as an
  MCP tool.
- The Librarian saves the asset to Drive and the Creative Director points `content_image_url` at
  it.

So image generation is **orchestrated by Claude, executed by an image model**. This is a
genuine architectural seam, stated plainly rather than hand-waved.

---

# Part VII — Operational Mechanics

## 7.0 Commit Logic and Reversible History

No change to product or strategy without a **Commit** (timestamp, `Commit_ID`, input source,
narrative, framework tag, QA status). In v2.0 a commit is paired with an **Event** row, so the
commit log and the knowledge graph share provenance. Reversible history works as before: find
the Commit/Event ID, trace downstream assets and Site blocks, roll back.

## 7.1 The CODE Framework

**C**apture (zero-friction intake) → **O**rganize (Librarian routes by actionability) → **D**istill
(Historian's progressive summarization) → **E**xpress (Creative Director visualizes; text is the
method of last resort). Unchanged.

## 7.2 The Visual Vocabulary

Deterministic data-to-design rules: dates→Gantt/timeline, coordinates→map, finance→chart,
process→flowchart, concept→summary card, vendor→embedded site, files→Drive grid. Charts
that need rendering use Google Charts/Looker/Mermaid; imagery uses the external image model
(6.6).

## 7.3 The Reconciliation Engine: Any Surface as Input

The architectural heart, restored from the founding conversation. The system is **not** a one-way
fan-out from a single trigger. **Any surface can be the input**; the engine's job is to detect a
change anywhere and reconcile the rest. Manual edits are first-class, not exceptions. One engine,
many triggers (6.5). The engine: reads the changed surface → resolves entities against the
registry → determines affected surfaces via the relational schema → generates each downstream
update → writes via API where possible, queues browser automation where not → logs the
reconciliation. Each write path is idempotent, retryable, independently disable-able, and surfaces
failures visibly (status Sheet / digest).

## 7.4 The Full Lifecycle: From Voice to View

1. **Capture** — "Update the homepage with the safety milestone; use the PDF I just dropped."
2. **Organize** — Librarian files the PDF, writes `Content_Assets` + relations + event.
3. **Distill** — Historian commits the narrative + framework tag + Event row.
4. **Express** — Creative Director composes the block, prompts the image model, emits insertion
   instructions.
5. **Audit** — QA Auditor drives the browser, screenshots 375/1440, checks contrast/layout.
6. **Publish & Confirm** — on pass, publish; status → `Verified`; backlinks updated in every
   referenced dossier; confirmation sent to the human. Target: ~4 minutes, ~15 seconds of
   human effort.

---

# Part VIII — Iteration, Scale & Change Management

## 8.0 The Feedback Loop

QA rejections are logged with a failure-type tag. Before a new task, the Creative Director queries
recent failures; recurring patterns (e.g., mobile font too small) trigger a Codex parameter update
(raise minimum body font), and the next run reads the updated Codex. The system builds muscle
memory. In v2.0 this is a Skill that edits the `governing-codex` Skill / `CLAUDE.md`.

## 8.1 Quarterly System Audits

A human reads the Narrative Log as a story, looking for Strategic Dissonance, and updates the
Governing Codex. The update is a Strategic Commit; every agent aligns on next activation.

## 8.2 The Fractal Growth Model

A project is a cell: one registry entry + one Drive folder + one Site + its site-map Sheets. New
client = clone the cell, not rebuild the system. One Orchestrator iterates the `Master_Index`. A
single consultant runs a portfolio of dozens.

## 8.3 The Workshop Integration

"Google and AI for Business" is the top of the funnel — a 15-minute workshop teaching the
*manual* version of everything the system automates. The workshop establishes the Clarity Gap;
the Antigravity CMS is the upsell. Each manual step maps to an automated agent. The pitch: *"What
if all of this happened automatically every time you added a file to your Google Drive?"*

---

# Appendices

## Appendix A — Bootstrap Protocol (Claude-Native Initialization)

Directive to the Claude orchestrator (run in Claude Code at the project root):

**Phase 1 — Constitution & host**
1. Confirm `CLAUDE.md` (the Governing Codex) is present and loaded.
2. Confirm MCP servers are connected: Drive/Docs/Sheets MCP, custom write MCP, browser
   MCP. Confirm Drive for Desktop is syncing the project shared drive.
3. Confirm the four subagents and their Skills are registered with the Agent SDK.

**Phase 2 — Substrate**
4. Verify the root Drive folder ("Antigravity Projects — 2026"); create if missing.
5. Construct `DB_Master_Projects`; create `MASTER_REGISTRY`, the six type sheets,
   `RELATIONS`, `EVENTS`, `Project_Narrative_Log`, `Content_Assets`.
6. For each project, create `SITE_PAGES`, `SITE_CONTENT_BLOCKS`, `SITE_SYNC_LOG`.

**Phase 3 — Librarian crawl**
7. Recursively scan the root; register entities, mint typed IDs, write metadata, generate alt text
   (Claude vision), create dossiers from per-type templates.
8. Establish watch triggers (folder drop, scheduled scan, ChatOps, manual-edit drift).

## Appendix B — Template Variable Reference

`{{client_name}}`, `{{client_short}}`, `{{consultant_name}}`, `{{partner_orgs}}`, `{{site_url}}`,
`{{project_strategy_pdf}}`, `{{hero_image_main}}`, `{{narrative_paragraph}}`,
`{{strategic_pillars}}`, `{{stage_1_name}}`, `{{stage_1_slides}}`, `{{vendor_partner_url}}`,
`{{stage_2_name}}`, `{{stage_2_drive_folder_id}}`, `{{stage_2_sheet_id}}`,
`{{development_docs}}`, `{{calendar_booking_url}}`, `{{consultant_contact}}`.

## Appendix C — Block Type Vocabulary

`heading`, `paragraph`, `bulleted_list`, `image`, `image_with_caption`, `external_link`,
`internal_link`, `drive_file_embed`, `drive_folder_embed`, `drive_sheet_link`, `calendar_button`,
`embedded_website`. Each maps to a Google Sites insertion action executed by the browser-
automation layer. Proof-pairing is mandatory: every narrative section gets ≥1 embedded proof.

## Appendix D — MCP Server Inventory

| MCP server | Purpose | Write? | Fallback |
|---|---|---|---|
| Drive/Docs/Sheets MCP | cloud file/sheet/doc ops | yes (no tab create) | Drive for Desktop |
| Custom write MCP | privileged writes when stock is read-only | yes | n/a |
| Browser MCP (Playwright/computer-use) | Sites + Docs tabs via front end | yes | manual |
| Image MCP (Gemini Imagen or other) | asset generation | yes | manual upload |

## Appendix E — Skill Inventory (Claude Skills ↔ v1.0 S01–S42)

The 42 skills from the Organizational Blueprint port directly to Claude Skills, grouped by agent:

- **Historian:** `transcript-synthesis` (S01), `5w-interrogation` (S02), `okr-alignment` (S03),
  `raci-tagging` (S04), `narrative-commit` (S05), `quarterly-review` (S06), `codex-version`
  (S07), `strategic-commit` (S08).
- **Librarian:** `content-scan` (S09), `taxonomy-routing` (S10), `canonical-rename` (S11),
  `cross-link` (S12), `content-assets-entry` (S13), `image-alt-text` (S14), `schema-design`
  (S15), `project-tab-gen` (S16), `validation-formatting` (S17).
- **Creative Director:** `section-copywriting` (S18), `visual-vocabulary` (S19), `image-prompt`
  (S20 — prompt only; generation external), `brand-enforcement` (S21), `layout-composition`
  (S22), `block-insertion` (S23), `proof-pairing` (S24).
- **Site Builder (browser):** `template-clone` (S25), `multi-page` (S26), `browser-drive`
  (S27 — Claude in Chrome / computer use), `playwright-fallback` (S28).
- **QA Auditor:** `viewport-sim` (S29), `screenshot` (S30), `wcag-contrast` (S31),
  `layout-regression` (S32), `passfail-ticket` (S33), `rejection-pattern` (S34), `param-self-tune`
  (S35).
- **Infra/Orchestrator:** `trigger-listen` (S36–S38), `job-dispatch` (S39), `agent-sequencing`
  (S40), `error-handling` (S41), `site-rollback` (S42).

The SBDC meeting-note generator — the first Skill ever built for this system — is the canonical
template all Historian/Creative Director skills inherit their voice rules from.

— End of Document —
