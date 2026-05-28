# Automation & Triggers — How the Watcher Actually Runs

How the Visual Second Brain reconciliation loop is triggered and executed on the Claude runtime,
using only documented Anthropic + Google capabilities. This replaces the hand-wavy
"ThinkPad bridge / it just watches" assumptions in earlier drafts with a verified, buildable design.

> **Framing reminder (`RES-COMMIT-001`, `RES-COMMIT-007`):** Claude is a **replaceable
> accelerator**, not a daemon. Claude does not "watch" anything on its own — it is *invoked*, does
> work, and stops. Something always-on must provide the **trigger** and the **runtime**. The
> substrate (Sheets) stays the source of truth regardless of which runtime fires.

---

## 0. The honest constraint

A fully "100% inside Claude, zero glue" watcher relies on two capabilities Anthropic's docs do
**not** currently confirm (see §4). So this design is built from **documented components only**,
adding a thin layer of free, Google-native glue. It needs **no Zapier** and **no Claude
Desktop/Cowork**.

---

## 1. The three jobs a watcher must do

1. **Detect** a change on any surface (Form submit, new Drive file, Sheet edit — incl. manual edits).
2. **Execute** the agent chain (Librarian → Historian → Creative Director → QA Auditor).
3. **Project** the result back to Sheets/Docs/Sites/Maps and log it.

Claude can do (2) and most of (3). It cannot do (1) by itself, and the Sites part of (3) needs an
authenticated browser. Those two are where the glue lives.

---

## 2. The documented-components architecture (recommended)

```
Google Form / Sheet / Drive folder
        │  (change happens — incl. a manual human edit)
        ▼
Google Apps Script trigger            ← free, Google-native, no Zapier
  • onFormSubmit / onChange (instant)
  • or time-driven poll (every 1–5 min) for Drive folder drops
        │  UrlFetchApp → webhook / HTTPS call
        ▼
Orchestrator (Claude Agent SDK, headless)   ← documented: query() in Python/TS
  • small serverless host (Cloud Run / Lambda / Functions) OR a Cloud Routine (§4)
  • runs the skill chain: librarian → historian → creative-director → qa-auditor
        │
        ├── Substrate read/write: Google Sheets/Drive/Docs API via a SERVICE ACCOUNT
        │     (documented, headless-safe — NOT the interactive consumer connector)
        │
        └── Sites projection: Computer Use against a PERSISTENT AUTHENTICATED browser
              (local machine or a hosted browser holding the Google session)
        ▼
SITE_SYNC_LOG row + ChatOps/digest confirmation to the human
```

Each write path is **idempotent, retryable, independently disable-able**. If the browser host is
down, Sheet/Drive/dossier writes still succeed and the Site degrades to "stale," never "lost."

---

## 3. Component verification (what the docs confirm)

| Component | Status | What it does / limit | Source |
|---|---|---|---|
| **Hooks** (`PreToolUse` can block) | ✅ confirmed | Our pre-publish QA gate: block publish unless `Verified` | code.claude.com/docs/en/hooks |
| **Agent SDK / headless `query()`** | ✅ confirmed | Run the Orchestrator + skill chain unattended (Py/TS) | platform.claude.com/docs/en/agent-sdk |
| **Computer Use** | ✅ confirmed | No-API Sites automation; screenshot→reason→click loop; needs authenticated browser | platform.claude.com/docs/.../computer-use-tool |
| **Skills (SKILL.md)** | ✅ confirmed | The 7 skills in `.claude/skills/`, portable across surfaces | code.claude.com/docs/en/skills |
| **MCP tool search / deferred loading** | ✅ confirmed | Cuts MCP token overhead (~85%) when many tools | platform.claude.com/docs/.../tool-search-tool |
| **Channels** (push events into a session) | ✅ confirmed | Optional: Telegram/Discord/iMessage → a session | code.claude.com/docs/en/channels |
| **Google Workspace connectors** | ✅ (interactive) | Read Drive/Gmail/Calendar in **chat**; headless use undocumented (§4) | support.claude.com/.../google-workspace-connectors |
| **`/schedule` (local)** | ✅ confirmed | Cadence tasks, but **machine must be awake + app open** | Claude Code docs |

---

## 4. The two unverified links (do not build on blindly)

1. **Cloud Routines with event triggers.** A cloud-side, machine-off **scheduled** routine appears
   to exist (third-party sources, not Anthropic's own docs), but the video's claim that routines
   trigger on **API call / GitHub event** is **not documented** — official routines look
   **schedule-only**. → *Verify in-app before relying on it. For event-driven triggering, use the
   Apps Script → webhook path and a serverless Agent SDK host, which are fully documented.*
2. **Consumer connectors in a headless run.** The Google Drive/Sheets **connector** is documented
   for **interactive** chat only; whether a routine or SDK run can use it **unattended is
   undocumented.** → *For the automated path, read/write the substrate with the Google
   **API via a service account**, not the consumer OAuth connector.*

---

## 5. Cost / surface ladder

| You want to automate… | Minimum (documented) | Cowork/Desktop? | Zapier? | Machine on? |
|---|---|---|---|---|
| Forms/Sheets → notes, dossiers, substrate | Apps Script trigger + Agent SDK + Sheets API (service account) | No | No | No (serverless) |
| Watch a Drive folder for dropped files | Apps Script time-trigger → Agent SDK | No | No | No (serverless) |
| Push updates to **Google Sites** | Agent SDK + Computer Use + authenticated browser host | No (Claude Code, not Cowork) | No | **Yes** (the browser host) |

---

## 6. Mapping to the Codex

- The Apps Script trigger band = the **Triggers** layer / the trigger-listener role (Blueprint
  S36–S38), replacing the old ThinkPad + Pub/Sub bridge.
- The Agent SDK orchestrator = **Orchestrator (R10)** running `orchestrator-reconcile`.
- The `PreToolUse` publish-gate hook = the QA Auditor's veto made enforceable.
- "Manual edits are first-class" (`RES-COMMIT-006`) is satisfied for free: Apps Script
  `onChange` catches a human editing a Sheet directly and reconciles it like any other trigger.
- Compliance systems (Neoserra) stay **manual** (`INT-010`); do not wire a trigger into them.

---

## 7. What to verify before deploying (honesty over completeness)

- Confirm Cloud Routines availability + trigger types on your plan, in-app.
- Confirm whether Computer Use can run in your chosen host against a persisted Google login.
- Start every autonomous routine on a **low-stakes, self-only** target (e.g., a daily digest to
  yourself) and watch it for weeks before pointing it at a client-facing Site. Trust is earned in
  reps, not installed.
