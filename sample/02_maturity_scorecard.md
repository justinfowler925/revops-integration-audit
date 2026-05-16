# Maturity Scorecard

> Customer-identifying values redacted. Counts and rubric scores reproduced as the audit generated them.

## Overall score: **3.67 / 5.0**

## Rubric

| Score | Meaning |
|:---:|---|
| 5 | Excellent — production-grade, no material defects |
| 4 | Strong — minor cleanup; no material risk |
| 3 | Adequate — several issues, manageable in normal ops cycle |
| 2 | At-risk — material defects; remediation effort warranted now |
| 1 | Critical — actively damaging the business; freeze new work until fixed |

## By layer

### Architecture & Mapping — **1 / 5** *(Critical — actively damaging the business; freeze new work until fixed)*

Critical integrity risk; freeze new dependency work until repaired.

| Severity | Count |
|---|---:|
| P1 | 12 |
| P2 | 12 |
| P3 | 59 |
| P4 | 0 |

**Top findings in this layer (redacted):**
- **[P1]** Declared canonical anchor missing on SF Account
- **[P1]** Declared canonical anchor missing on SF Contact
- **[P1]** Declared canonical anchor missing on SF Lead

---
### Data Quality — **2 / 5** *(At-risk — material defects; remediation effort warranted now)*

Material defects present; warrants focused remediation this quarter.

| Severity | Count |
|---|---:|
| P1 | 10 |
| P2 | 5 |
| P3 | 0 |
| P4 | 0 |

**Top findings in this layer (redacted):**
- **[P1]** Two fields share label *[redacted]* on Opportunity: *[standard field], [custom field]*
- **[P1]** Two fields share label *[redacted]* on Opportunity: *[standard field], [custom field]*
- **[P1]** Two fields share label *[vendor name redacted] Last Updated* on Account: *[legacy package field], [current package field]*

---
### Sync Health — **5 / 5** *(Excellent — production-grade, no material defects)*

No P1/P2 findings; data hygiene meets a production-grade bar.

| Severity | Count |
|---|---:|
| P1 | 0 |
| P2 | 0 |
| P3 | 1 |
| P4 | 0 |

---
### Process Fidelity — **5 / 5** *(Excellent — production-grade, no material defects)*

No P1/P2 findings; data hygiene meets a production-grade bar.

| Severity | Count |
|---|---:|
| P1 | 0 |
| P2 | 0 |
| P3 | 2 |
| P4 | 0 |

---
### Governance — **4 / 5** *(Strong — minor cleanup; no material risk)*

No critical defects; minor cleanup queue.

| Severity | Count |
|---|---:|
| P1 | 0 |
| P2 | 1 |
| P3 | 1 |
| P4 | 0 |

**Top findings in this layer:**
- **[P2]** No monitoring URL for the integration
- **[P3]** No documentation URL for the integration

---
### AI Augmentation Readiness — **5 / 5** *(Excellent — production-grade, no material defects)*

No P1/P2 findings; data hygiene meets a production-grade bar.

| Severity | Count |
|---|---:|
| P1 | 0 |
| P2 | 0 |
| P3 | 0 |
| P4 | 0 |

---

## How to improve a layer's score

A layer moves up by one point when:

- **1 → 2:** at most 3 P1s remain
- **2 → 3:** at most 1 P1 + 3 P2s remain
- **3 → 4:** zero P1s; ≤1 P2; ≤5 P3s
- **4 → 5:** zero P1/P2; ≤2 P3s

Use the remediation playbook (`05_remediation_playbook.md`) to plan a remediation sprint that targets the specific count-deltas above. Re-run the audit after each remediation batch to confirm the score moved.
