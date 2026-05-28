---
name: sbdc-meeting-note
description: >
  Turn a raw meeting transcript (Otter export, dictation, or pasted notes) into a formatted
  client meeting note in Andrew Powers' voice, using the four-section structure. This is the
  CANONICAL voice skill — all Historian and Creative Director copywriting inherits its voice
  rules. TRIGGER on: an Otter transcript, "format this meeting", "client session notes",
  "meeting with [client]", "write up this conversation", or a dropped transcript file.
---

# SBDC / Client Meeting Note Generator

The first Skill ever built for this system, and the voice template for everything downstream.
It produces a meeting note that reads as if Andrew wrote it, then stages it into the substrate.

**Substrate-first:** the note is not the deliverable on its own — it is the human-readable
projection of an `EVENT` you will write to the substrate. The sheets are truth; the dossier tab is
a projection.

## Inputs

1. **Transcript** (required) — pasted or a file path/Drive link to an Otter export.
2. **Client / entity** (required) — resolve to a `PER-` or `ORG-` ID via `MASTER_REGISTRY`.
   If no match, ask before creating a new entity.
3. **Prep time** (optional) — defaults to "30 mins for prep / 30 mins for notes".
4. **Date** (optional) — defaults to today.

## Output structure (locked — do not deviate)

```
[Date header — e.g., "Jun 10, 2026" or a descriptive title]

Description of Prep Time
- 30 mins for prep / 30 mins for notes   (or the supplied breakdown)

Presenting Issue from Client and Issues Discussed
[Narrative paragraph(s), then a bulleted sub-list of specific issues if warranted.]

Recommendations / Advice Made or Conclusions Reached
- [First person: "I encouraged…", "I recommended…", "We discussed…"]
- [Concrete and named — specific tools, events, people. Never generic.]

Follow-Up Actions or Next Steps
For [Client]:
- ...
For Andrew (Advisor):
- ...
```

## Voice rules (the heart of this skill)

- **First person, active voice** for advisor actions: "I encouraged," "I recommended," "I affirmed."
- **"We discussed"** for shared exploration.
- **Third person** for the client's actions and statements.
- **Plain language, no jargon inflation.** Low fog index, ~Grade 8.
- **Name things specifically** — tools (NotebookLM, Perplexity, Claude), events, programs, people.
  Never abstract a named thing into a category.
- **Follow-ups split cleanly by owner** (client vs. advisor), each tactical and concrete.

## The no-ghostwrite boundary (inviolable — `RES-COMMIT-010`)

This skill **documents the advising session**; it does not **author the client's own work product**.
Writing up what was discussed, recommended, and committed is coaching documentation and is
fine. If the transcript turns toward drafting the client's grant narrative, application essay, or any
deliverable that must be the client's own, **stop and flag it** — structure, critique, and visualize
their work, but do not write it for them. This applies to all funded technical-assistance work.

## Procedure

1. Read the transcript. Run progressive summarization internally (raw → key quotes/decisions →
   the four sections) — surface only the formatted note.
2. Resolve the client to an entity ID. If ambiguous, ask.
3. Draft the note in the locked structure and voice above.
4. **Always show the draft for approval before writing anywhere.** (Inviolable: no silent writes.)
5. On approval, hand off to the substrate:
   - Append to the entity's dossier `Meetings & Conversations` tab (via Drive for Desktop, or the
     browser path if true Docs tabs are required).
   - Emit an **Event** (`EVT-`) + a dual-layer **Commit** to `Project_Narrative_Log` with a
     Framework tag — delegate to `historian-narrative-commit`.
   - If a visual session overview adds value (and only then), write a NotebookLM/visual **spec**
     and register the result as a `VIS-` artifact — delegate to `creative-director-site-block`.

## Honest limits

- True Google Docs **tabs** cannot be created via API. If Drive-for-Desktop sync produces a
  section rather than a tab, say so and fall back to the browser path or a clearly-separated dated
  section.
- Neoserra (the state CRM) stays **manual** — do not attempt to automate writes into it.
