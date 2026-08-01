# Handoff · fowler-brain SSOT × Brutus dashboard

Resume artifact for the next Cursor thread. Written 2026-08-01 from cloud agent run [Fowler-brain expansion](https://cursor.com/agents/bc-6162eecd-095d-4bbb-a67e-8a8bf4b78b4e).

## Goal

Make **fowler-brain the SSOT** for everything Justin is working on, and surface it as a **new tab in Brutus** (local mission-control / agent UI on the laptop) so it can be seen and operated from one dashboard.

## Desired lanes

From the stated ask plus observed work patterns (ClearSpeed Slack cadence, `/now` planks, portfolio, Atlas4 lanes):

| Lane | Scope |
|---|---|
| **Personal projects** | PurpleChipmonk, MonchMonch, Matchbox7, justinfowler.com / IP, consulting primitives |
| **ClearSpeed RevOps** | Linear `REV-*`, Deal Support Requests, HubSpot↔Salesforce, Org Chart / Rep Cockpit, weekly activity reports |
| **Lessons learned** | capture → review → promote → archive (existing fowler-brain loop; Phase 5 promotion still deferred) |
| **Todos / inbox** | Single capture surface; lane-tagged; Saturday-reviewable |
| **Audience / writing plank** | LinkedIn cadence, newsletter, talks (Plank 03) |
| **Consulting / money** | Six-layer audit productization, CCA-F / paid IP, open-source Atlas/OpenClaw derivatives |
| **Agent ops** | Atlas/Brutus lane health, MCP preflight, never-silent-delegation style prevention rules |

## Known architecture

Private repos were **not** accessible to the cloud agent that wrote this. Details below are from public case studies only.

### fowler-brain (private)

- Two layers in one git repo:
  - **Brain:** `global/`, `contexts/`, `workflows/`, `templates/`, `vocabulary/`, `lessons/`
  - **Strategy:** `strategy/plans/`, `strategy/weekly/`, `strategy/tracking/`, `strategy/reviews/`
- Compile via `rebuild.sh` → 8 tool adapters (Claude Code, Cursor `.mdc`, Atlas, OpenClaw, Claude.ai, Ollama, etc.)
- Operating loop: capture → review → promote → distribute → execute
- Cadence: Saturday 8a CT coaching review
- Phases 1–4 shipped; Phase 5 (lesson-promotion algorithm, dormant asset detection, rule conflict resolution) and Phase 6 (quarterly architecture review) are trigger-deferred
- Case study: https://justinfowler.com/case-studies/fowler-brain.html

### Atlas4 (private, Mac Studio)

- Manager UI at `127.0.0.1:8766`
- Lanes: `pcm · sfdc · atlas-d · research`
- Intake: Linear webhook → `state/inbox/<lane>/*.txt`
- Case study: https://justinfowler.com/case-studies/atlas4.html

### Brutus

- Personal bot / mission-control UI that **lives on the laptop**
- Named in Slack (2026-07-31) as the sibling/successor joke to Atlas (“atlas and now brutus”)
- Not in any public GitHub repo under `justinfowler925`
- This is the UI that should get the new **Brain / SSOT** tab

## Hard blocker (this cloud run)

- Cursor Cloud agents run in a **remote Docker VM**, not on the laptop.
- This workspace was only [`justinfowler925/revops-integration-audit`](https://github.com/justinfowler925/revops-integration-audit) (public case study + unmerged org-chart kanban branch `cursor/org-chart-kanban-swimlanes-a840`).
- **No Brutus, Atlas, or fowler-brain code was on the filesystem.** Private repo names (`brutus`, `atlas4`, `fowler-brain`) 404 for the cloud token.
- A Brutus “new tab” **cannot** be implemented from a cloud run against this audit repo until Brutus is opened locally or granted to the agent.

## Resume instructions for next thread

1. Open the **Brutus project folder in Cursor locally** (Agent mode, not Cloud), **or** grant the agent the private Brutus + fowler-brain repos.
2. Inspect Brutus tab shell / nav and add a **Brain / SSOT** tab.
3. Dashboard should show the lanes above: projects, ClearSpeed RevOps, lessons, todos/inbox, audience, consulting/money, agent ops — wired to fowler-brain markdown/SSOT as source of truth (read lane boards + capture hooks; compile/distribute stays in fowler-brain scripts).
4. Prefer matching Brutus’s existing UI patterns over inventing a new design system; if Brutus is Atlas4-derived, mirror the mission-control tab model.

## Related public artifacts

- Org-chart Function × Authority kanban prototype (draft PR): https://github.com/justinfowler925/revops-integration-audit/pull/1
- Six-Layer Integration Audit case study: this repo’s `README.md`
- `/now` planks: https://justinfowler.com/now.html

## Out of scope for this handoff commit

- No Brutus UI implementation (code not present in the cloud workspace).
- No changes to the audit case-study narrative beyond adding this file.
