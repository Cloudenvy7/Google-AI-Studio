# The Visual Second Brain
### A Technical and Architectural Narrative

*Black Fox Studios — relational data infrastructure for community-based organizations*

---

## Purpose of this document

This narrative explains what the system is, how it works, and why it is built the way it is — written for a technical or partner reader who wants enough of the architecture to evaluate it, build on it, or collaborate around it. It covers the whole system: the relational substrate, the visual layer that sits above it, and the community theory of change the whole thing exists to serve. It is not a pitch. Where the design makes a tradeoff, the tradeoff is named. Where the system has load-bearing assumptions, those assumptions are stated so they can be tested rather than discovered later.

The short version: most "AI for community organizations" work fails because it treats the AI as the system. Here, the AI is not the system. The data substrate is the system, and the AI is one accelerator that reads and maintains it. That single inversion explains nearly every design choice that follows.

---

## 1. The problem this is built against

The communities this serves — immigrant and refugee organizations, BIPOC small business owners, formerly incarcerated workers, nonprofit staff serving those populations — are locked out of the current AI wave for a reason that is rarely named precisely. It is not that they lack intelligence, data, or need. It is that every dominant AI tool assumes a specific cognitive posture: an individual, working alone, in text, through a prompt, who has already organized their own thinking well enough to ask the tool a good question. Obsidian looks like a developer tool. A chatbot looks like a blank box demanding expertise the user came to acquire. Notion looks like enterprise software with too many switches. The tools that would teach someone to think like a knowledge worker are gatekept behind the very literacy they would teach.

There is exactly one sufficiently powerful relational system these communities already trust and operate daily without fear: Google Workspace. It does not look technical. It looks like email, documents, spreadsheets, forms, and calendars — the surfaces people already use at work, at church, at the community center. The relational power is hidden under familiar surfaces. A volunteer who has never heard the word "database" can fill out a Google Form; that submission becomes a row in a Sheet, which becomes a reference in a Doc, which becomes a section on a Site. They did data entry. The system did the relational work.

That is the wedge. The design goal is not "easier AI." It is **AI-grade data infrastructure operated by people who do not know they are operating AI-grade data infrastructure** — and who never have to interact with the AI directly until they choose to.

---

## 2. The central inversion: the substrate is the system

Most AI deployments put the model at the center and treat data as something the model consumes. This system does the opposite. The relational substrate — a set of Google Sheets holding entities, events, and relations — is the durable, authoritative core. The AI is a maintenance and synthesis layer that reads from the substrate and writes back to it. Swap the model (Claude, Gemini, a local open-weights model on a NAS) and the substrate is untouched. The schema, the rules, the visual conventions, and the accumulated data all survive a model switch, because they were never inside the model in the first place.

This is why the substrate had to be designed first and carefully, before any automation. Everything downstream is a projection of it. If the substrate is sound, projections can be regenerated freely. If the substrate is muddled, no amount of model quality fixes it.

The practical consequence for a partner: **the system's value compounds in the data, not in the model.** That is the opposite of most AI products, where value evaporates when the vendor changes terms. Here, the organization owns the substrate (their own Workspace), and the intelligence layer is replaceable infrastructure.

---

## 3. The substrate, layer by layer

The substrate is a normalized relational schema implemented in plain Google Sheets. It follows standard database discipline (third normal form), but it is operable by non-technical people because the surface is just spreadsheet tabs.

### 3.1 The spine: a master registry of typed IDs

Every entity that exists anywhere in the system — a person, an organization, a place, a project, a resource, an event, a visual artifact — gets exactly one row in a `MASTER_REGISTRY` sheet and one immutable, typed ID: `PER-00001`, `ORG-00001`, `PLA-00001`, `PRJ-00001`, `RES-00001`, `EVT-00001`, `VIS-00001`.

Two design rules carry the weight here:

- **IDs are stable; names are not.** A person's name can change, an organization can rebrand, a place can be renamed — the ID never moves. Every cross-reference everywhere in the system points at the ID, not the name. This is what makes the system survivable over years.
- **The registry is a phone book, not a profile.** It holds only the ID, the type, a display name, status, creation provenance, and a link to that entity's dossier document. All substantive detail lives in the type-specific sheets. Keeping the spine thin keeps it fast and unambiguous.

### 3.2 Type sheets: one per entity kind

`PEOPLE`, `ORGANIZATIONS`, `PLACES`, `PROJECTS`, `RESOURCES`, plus `EVENTS` and `VISUAL_ARTIFACTS`. Each row carries a foreign key back to the registry and only the fields relevant to that type — people have emails and roles; places have latitude and longitude; projects have status and timelines. This is deliberate: a unified mega-table would force every row to carry columns it doesn't need. Typed sheets stay readable for the humans operating them.

### 3.3 Events: the keystone

This is the non-obvious move that makes the whole graph cohere. Most relational designs would create a relation every time two entities interact, and lose the context of *why* and *when*. Instead, an **Event** is a first-class entity: a bounded occurrence — a meeting, an introduction, a workshop, a phone call, a submission — with participants, a date, a project context, and a pointer to the source document that recorded it.

"I introduced Jerry to the two Northeastern interns to discuss continuing the hackathon project" is not three relations. It is **one event** that *implies* relations between the participants. The event is the unit of truth; relations are derived from it. Every relation therefore inherits a provenance chain: relation → source event → source document → the moment in the world it actually happened.

### 3.4 Relations: connective tissue with mandatory provenance

The `RELATIONS` sheet is where the graph lives. Each row is one relation between two entity IDs, with a relation type drawn from a controlled vocabulary. The hard rule — enforced as a required field — is that **every relation must cite a `source_event_id`.** No orphan facts. No "Maria works at FCS" floating free of when and how that was established. This is the property that lets the system answer not just "what is connected" but "on what basis, as of when, and where can I read the original." It is a bibliography baked into the data model.

A controlled vocabulary governs relation types (`Employed by`, `Located at`, `Involved in`, `Introduced to`, `corrects_drift`, `derived_from_book`, `external_validates`, and a deliberately small set of others). Vocabulary discipline matters here more than anywhere: the fastest way to kill a relational system is to invent a new relation type every time something feels slightly different. The list is meant to stay short and to grow only on purpose.

### 3.5 The operational sheets: lint, integrations, and per-project site state

Three additional sheets keep the system honest and operable:

- **`LINT_FINDINGS`** is where the system logs its own integrity problems for human review: contradictions between events, claims that newer sources have superseded, entities with no inbound relations, places where a deliverable risks reinforcing a known conceptual drift. It starts empty and fills as the system runs. The point is that the system surfaces its own decay rather than hiding it.
- **`INTEGRATIONS`** is a single inventory of every external dependency, with each one's failure mode and fallback stated explicitly. This doubles as the technical-architecture appendix for any funder or partner who asks "what is this actually built on, and what happens when a piece breaks."
- **Per-project site sheets** (`SITE_PAGES`, `SITE_CONTENT_BLOCKS`, `SITE_SYNC_LOG`) describe the intended state of a project's public Google Site. They are covered in detail in Section 5.

---

## 4. Dossiers and backlinks: where the graph becomes navigable

Every entity has a dossier — a single Google Doc, organized into tabs, that is the human-readable home for everything about that entity. The sheets are queryable; the dossier is readable. They are two views of the same truth.

Tabs split cleanly into two kinds, and the split is a hard rule: **human-written tabs and system-generated tabs never mix.** A person's dossier has a `Meetings & Conversations` tab (what you wrote) and a separate `Mentions & Connections` tab (what the system found). The second is auto-generated from the relations and events — every place this entity appears across the system, in date order, each linking back to its source. Visiting Maria's dossier surfaces every event she was part of, every project she touches, every visual artifact that references her — without that content being duplicated into her dossier. The information lives in one place; discoverability happens through backlinks.

This is the difference between a filing cabinet and a knowledge graph. In a filing cabinet, finding everything about Maria means remembering everywhere you filed her. Here, the backlinks assemble themselves, and they carry their provenance with them.

Auto-generated tabs are visibly marked as such, and the system never silently overwrites human edits — if it finds a manual note in an auto tab, it preserves and flags it rather than destroying it. Trust in an automated system is built or lost on exactly this kind of detail.

### The staleness discipline

A backlink from two years ago and one from last week look identical on a tab, and a reader assumes both are current. To prevent confident-looking stale facts, the system carries a **staleness threshold** (currently 180 days, stored as a single editable commitment in the substrate). When it regenerates an auto tab, any relation without a confirming event inside that window gets visually flagged as possibly outdated — never deleted, just marked "last confirmed on this date." The system is allowed to remember; it is not allowed to pretend old facts are fresh.

---

## 5. Google Sites and the API gap: why browser automation is correct, not a hack

Several Google products that this system depends on have no public write API. You can read the structure of Google Docs tabs but not create them programmatically. Google Sites has no meaningful write API at all. This is not a bug to engineer around quietly; it is a structural fact that shapes the architecture, and a partner should understand it clearly.

The design response is the cleanest available: **the Sheet is the intended state of the Site; automation reconciles the Site to match the Sheet.** A project's `SITE_CONTENT_BLOCKS` sheet describes, row by row, every content block that should appear on the project Site — heading, paragraph, image, embed — in order, on which page, sourced from which event and which entities. To publish, the system walks that sheet and makes the Site match.

For the surfaces with no API, that reconciliation happens through **browser automation** (Stagehand / Playwright / Puppeteer) — software that drives the Site editor the way a person would. This is the same pattern enterprise teams use for legacy systems without APIs: when the front door is locked but the lobby is open, you walk through the lobby. It is the architecturally correct answer to an API gap, not a workaround.

The honest tradeoffs, stated plainly:

- **Browser automation is more fragile than an API.** When Google changes the Sites editor — and they do — the automation can drift or break, sometimes silently. The mitigation is that the Sheet always holds the truth, so a broken Site sync degrades to "the Site is stale" rather than "the data is lost." The `SITE_SYNC_LOG` records every run so failures are visible, not silent.
- **Each write path is independently disable-able.** If Site automation breaks, the dossier, registry, and map updates still work, and Site editing falls back to manual for a week without taking the system down. This is a deliberate property: no single fragile component can halt the whole system.
- **Compliance systems stay manual.** Where a write path touches a regulated system (for example, a state CRM with no import function and real compliance exposure), the design choice is to keep it manual indefinitely. Automating into a compliance system you can be audited on is a liability, not a convenience, and the architecture says so explicitly rather than chasing full automation for its own sake.

There is a second, sharper compliance boundary that the system must encode, drawn from real contract terms: **the AI assists, structures, reviews, and visualizes — it does not author the work that must be the client's own.** The EDI contract states the rule plainly: provide coaching, review, and feedback; do not ghostwrite applications. An AI that drafts an applicant's grant narrative crosses that line; an AI that helps the applicant structure, critique, and visualize their own narrative stays on the right side of it. This is not a minor caveat — it governs what the synthesis layer is permitted to produce whenever the system touches funded technical-assistance work, and it is stored as an architectural commitment so the constraint travels with the system rather than living only in a contract someone has to remember.

---

## 6. The visual layer: the equity layer

This is the part that is easy to mistake for decoration and is in fact load-bearing.

The claim "a picture is worth a thousand words" is treated here as a literal statement about cognitive bandwidth, not a cliché. A reader processing a thousand words sequentially takes minutes; a viewer absorbing a well-constructed image that encodes the same information takes seconds. For a fluent, time-rich knowledge worker, that gap is a convenience. For a community organization volunteer with fifteen minutes between client meetings, it is the difference between "this is usable" and "this is not for me."

The precise framing matters: a good visual is **consolidation, not abstraction.** An abstraction hides detail; a consolidation concentrates it. A community asset map does not throw away the underlying records — it concentrates the whole dataset into a single glance, with the full substrate preserved underneath. The visual is a higher-bandwidth interface to the same truth, not a lossy summary of it.

This reframes who gets to participate. The dominant AI paradigm privileges a cognitive style — alone, textual, sequential, prompt-driven — that is over-represented among software engineers and under-represented in nearly every community organization in the country. The communities served here are not technically illiterate; they are visually and collaboratively fluent in ways the current paradigm does not reward. The system rewards that fluency by treating the dashboard, the map, the timeline, and the infographic as **first-class data artifacts the AI reads from**, not as outputs the AI produces to satisfy an accessibility checklist.

Architecturally, this is why `VISUAL_ARTIFACTS` is a full entity type with its own registry, not a throwaway output. Each infographic, dashboard, map view, slide deck, or audio/video overview is a row that records what it consolidates, what question it answers, how it was generated, its cognitive format, and required alt text. Visuals persist, version with the data they represent, and regenerate when the underlying data changes. They appear as thumbnails in the backlink tabs of every entity they reference, so an entity's dossier is a multimodal index, not just a text list.

The generation engine at the pre-code level is **Google NotebookLM**, chosen deliberately: it is free, it lives inside Workspace, it is source-driven rather than prompt-driven (the user uploads material and the tool makes it navigable, rather than demanding a good prompt), and its Studio outputs map almost exactly onto the visual taxonomy the methodology already uses. It is the Google-native operationalization of two of the foundational methodologies at once. When the time comes for sensitive data to stay local, the same role is filled by an on-premise equivalent — the architecture is identical; only the runtime moves.

---

## 7. Why the methodology holds: the intellectual lineage

The "Visual Second Brain" is not an invented design pattern. It is a synthesis of five established business and knowledge-management methodologies, each solving one specific problem in the stack. Naming the lineage is what makes the system teachable as canonical material rather than proprietary technique, and it is what lets a skeptical reader check the method against its sources.

- **Osterwalder, *Business Model Generation*** — the nine-block Canvas, used here as a *reading* tool for structured analysis of any external entity. Contributes the canonical structure for an entity's dossier.
- **Forte, *Building a Second Brain*** — CODE (Capture/Organize/Distill/Express) and PARA. Contributes the discipline of externalizing thinking into a structured, retrievable substrate that outlives any individual's memory.
- **Roam, *The Back of the Napkin*** — the six-picture visual taxonomy and the empirical case for visual cognition. Contributes the foundation and the canonical vocabulary for the visual layer.
- **Gerber, *The E-Myth Revisited*** — the Technician/Manager/Entrepreneur role decomposition and the franchise-prototype discipline. Contributes the move that turns individual work into systematized, portable operations.
- **Ries, *The Lean Startup*** — Build-Measure-Learn and innovation accounting. Contributes the iteration discipline that turns a static system into a self-correcting one.

The through-line across all five is **portability**: each book takes a capacity that normally requires an exceptional individual and turns it into a teachable method. The community member does not need to be a designer, a strategist, an operations expert, a knowledge manager, or a lean practitioner — the methods carry those capacities. That is what makes the work scalable, and it is why the substrate stores these books and their roughly thirty named principles as first-class resources: any deliverable can be tagged to the principle it derives from, making the intellectual lineage queryable rather than merely cited.

The same relational discipline guards the system against its own conceptual decay. Six named "drifts" — recurring ways the concept gets distorted in conversation (treating AI as the engine rather than the accelerator; forgetting the pre-code foundation; conflating the methodology with one of its tools) — are stored as entities, and a `corrects_drift` relation type lets any artifact be checked against them. The system is built to notice when its own description has wandered from its intent.

---

## 8. The deployment arc: cloud now, local-first later

The architecture is portable across runtimes by design, and it deploys in stages so that value is produced before complexity is added.

- **Today — pre-code, cloud.** Organizations operate Google Workspace directly. NotebookLM generates visual consolidations. Everything is free and accessible to anyone with a Google account. No AI orchestration is required for the work to produce value — and this is a proven claim, not an aspiration. The EDI Technical Assistance Playbook is a paid, compliant City of Seattle contract that runs almost entirely on pre-code Workspace: a scheduling portal, a welcome email, an intake Form, Session Sheets, a Meeting Log (Form → Sheet), an Evaluation & Public Benefit Report, and an invoice. No registry, no relations table, no AI in the critical path — and it delivers compliant client work repeatably. The precise claim is worth stating carefully, because overclaiming here is itself a known failure mode: **the Playbook proves that pre-code Google Workspace delivers compliant paid client work; the relational substrate described in this document is the structured evolution of that same Form-to-Sheet-to-Doc flow, not something the Playbook already implements.** The 2023 personal case study makes the complementary point quantitatively — the same pre-code discipline, applied to one person's job search, moved interview conversion from 2.86% (35 applications, 1 interview, traditional method) to 35.29% (17 applications, 6 interviews, structured method), a clean baseline-intervention-measurement experiment. Together: the case study proves the method works at personal scale; the Playbook proves it works as paid, compliant, other-as-client work. The substrate is what those proven surfaces become when the registry and relations are layered on top.
- **Near future — local-first reasoning.** Sensitive client data is reasoned over on an on-premise device (a NAS) running open-weights models. The collaborative surfaces stay in Workspace where multiple people edit together; the reasoning and knowledge-graph synthesis happen locally, on hardware the organization physically owns, can inspect, and can unplug. For organizations serving vulnerable populations, this is a data-sovereignty requirement, not a preference — and it lines up with where AI regulation is heading, making it the compliant default rather than only the ethical one.
- **Later — physical interfaces.** Projected surfaces and gesture/ambient capture extend the visual layer into the physical world, so that the act of working and the act of recording the work converge. This is downstream of a stable substrate, not a prerequisite for it.

At every stage the nonprofit's people stay on the visual surfaces they already use. Everything below that is invisible to them. Manual edits remain first-class inputs at every layer — a person editing a sheet directly is treated exactly like an automated update, which is what lets volunteers and clients participate without learning the machinery.

---

## 9. Where the system is strong, and where it is exposed

A partner should hear both sides.

**Strengths.** The substrate is durable and model-agnostic — value compounds in data the organization owns. The provenance discipline (every relation cites an event; every event cites a document) makes the graph auditable in a way most knowledge bases are not. The human-written / system-generated separation and the never-silently-overwrite rule make it trustworthy to operate. The visual layer is a genuine accessibility-as-default design, not an afterthought. The whole thing runs at pre-code on tools the communities already trust, which is the difference between adoption and abandonment.

**Exposures, stated honestly.** Browser automation against APIs that don't exist is the fragile seam; it is mitigated by keeping the Sheet authoritative and every write path independently disable-able, but it carries an ongoing maintenance cost whenever Google changes a UI. Local-first AI is slower and weaker than frontier cloud models, so the heaviest reasoning may still need occasional cloud calls, with the sovereignty boundary made explicit per data class. And a system this interconnected has a real operational-ownership question: someone must maintain it as Google's surfaces change, and that responsibility should be designed in from the start — funded, contracted, or staffed — rather than discovered as an unplanned part-time job later. The architecture's answer is graceful degradation: no single fragile component can take the whole system down, and the substrate of truth survives any individual projection breaking.

---

## 10. The one-line version

A relational data substrate the community owns and operates through tools it already trusts; a visual layer that makes that substrate readable at human bandwidth; and a replaceable AI layer that reads and maintains it without ever being the thing the community has to learn. The AI is not the system. The substrate is the system. Everything else is a projection of it — and that is precisely why it holds.
