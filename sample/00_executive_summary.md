# HubSpot ↔ Salesforce Integration Audit — Executive Summary

> Customer-identifying values redacted. All other fields, severity counts, and finding categories are reproduced as the audit generated them.

**Tenant:** *[Customer name redacted]* (B2B SaaS)
**Audit date:** 2026-05-16
**Maturity score (overall):** **3.67 / 5.0** — Adequate; several issues, manageable in normal ops cycle

---

## TL;DR

Of the six audit layers, the lowest-scoring is **Architecture & Mapping (1/5)** — critical integrity risk; freeze new dependency work until repaired.

**22 P1 findings** require remediation this quarter. They compound — fixing them individually leaves the integration in an inconsistent intermediate state. Plan a single coordinated remediation sprint.

**18 P2 findings** warrant fixes within 90 days; left unaddressed they will materially degrade the trust in cross-system reporting.

## Severity distribution

| Severity | Count | Meaning |
|---|---:|---|
| P1 — Critical | 22 | Business-critical; remediation this quarter |
| P2 — Material | 18 | Material defect; fix within 90 days |
| P3 — Quality   | 63 | Quality issue; fix next normal cycle |
| P4 — Minor     | 0 | Nice-to-have |
| INFO           | 1 | Context / no defect |

## Maturity by layer

| Layer | Score | Headline |
|---|:---:|---|
| Architecture & Mapping | **1 / 5** | Critical integrity risk; freeze new dependency work until repaired. |
| Data Quality | **2 / 5** | Material defects present; warrants focused remediation this quarter. |
| Sync Health | **5 / 5** | No P1/P2 findings; data hygiene meets a production-grade bar. |
| Process Fidelity | **5 / 5** | No P1/P2 findings; data hygiene meets a production-grade bar. |
| Governance | **4 / 5** | No critical defects; minor cleanup queue. |
| AI Augmentation Readiness | **5 / 5** | No P1/P2 findings; data hygiene meets a production-grade bar. |

## Top 5 findings (by severity, then layer)

**1. [P1] Declared canonical anchor *[hubspot_company_id__c]* missing on SF Account** *(layer: architecture)*

The integration's configuration declares a Salesforce-side field as the cross-system join key, but no field by that name exists in production. The integration believes it has a canonical ID; it doesn't.

**2. [P1] Declared canonical anchor *[hubspot_contact_id__c]* missing on SF Contact** *(layer: architecture)*

Same shape as #1, on the Contact object.

**3. [P1] Declared canonical anchor *[hubspot_contact_id__c]* missing on SF Lead** *(layer: architecture)*

Same shape as #1, on the Lead object.

**4. [P1] Declared canonical anchor *[hubspot_deal_id__c]* missing on SF Opportunity** *(layer: architecture)*

Same shape as #1, on the Opportunity object.

**5. [P1] Declared canonical anchor *[sfdc_account_id]* missing on HubSpot companies** *(layer: architecture)*

Same shape as #1–4, on the HubSpot side.

> **Pattern:** the integration has zero cross-system canonical ID fields on either side. Every reconciliation falls back to normalized-email matching, which produces a 5–15% structural orphan rate even on hygienic portals. This is the single highest-impact remediation in the engagement; fixing it makes most of the downstream findings easier to address.

## Recommended next steps

1. **This week:** Read `05_remediation_playbook.md` — the prioritized list of fixes with owner / effort / impact estimates.
2. **This month:** Stand up the AI augmentation play marked `horizon: now` in `06_ai_augmentation_roadmap.md`. The continuous-audit play pays back in ≤6 weeks every engagement.
3. **This quarter:** Re-run the audit and compare the maturity scorecard. Targeted remediation should move at least one layer up by one full point.

## How to read the rest of the deliverable

| File | Audience | When to open it |
|---|---|---|
| `01_findings_matrix.md` | RevOps engineer | When you want the exhaustive list |
| `02_maturity_scorecard.md` | Exec + RevOps lead | Quarterly progress reviews |
| `03_data_quality_deep_dive.md` | RevOps engineer | When triaging a P1/P2 in data_quality |
| `04_sync_health_deep_dive.md` | RevOps engineer | When the sync is misbehaving |
| `05_remediation_playbook.md` | RevOps engineer | Workplan source-of-truth |
| `06_ai_augmentation_roadmap.md` | Exec + RevOps lead | AI investment planning |
