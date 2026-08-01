# Function × Authority Org Chart (Kanban + Swim Lanes)

An alternative account org-chart lens for sales power mapping.

Traditional hierarchy answers *who reports to whom*. Title bands answer *how senior is this person*. This view answers a different question:

> **In each buying function, who can decide — and who only shapes, evaluates, or informs?**

## Axes

| Axis | Role in the board | Typical source fields |
|---|---|---|
| **Columns** | Category / function (Underwriting, Claims, IT, Procurement, Finance, Legal, Executive) | `Department`, buying-function tag, or a curated function taxonomy |
| **Swim lanes** | Authority / decision-making capacity | `Power`, seniority band, or an explicit Authority picklist |
| **Cards** | People (contacts) | Name, title, Power / Preference / Relationship / Access indicators |

### Authority lanes (top → bottom)

1. **Decide** — final yes/no; can commit budget or block the deal
2. **Shape** — sets criteria, owns the evaluation; strong influencer
3. **Evaluate** — runs diligence, pilots, security review; may recommend
4. **Inform** — adjacent stakeholder; needs updates, low decision weight

Lanes are ordered by decision capacity, not job grade. A Director of Procurement who can stop a contract sits in **Decide** even if a VP of Marketing sits in **Inform**.

### Function columns

Columns are the buying functions that matter for the motion (insurance / risk / enterprise SaaS by default). Empty cells are first-class: a blank **Decide × Procurement** cell is a coverage gap, not whitespace.

## Why this beats hierarchy alone

| View | Best at | Weak at |
|---|---|---|
| Hierarchy | Reporting lines, sponsor path | Multi-threaded buying committees |
| Title bands | Seniority distribution | Functional ownership of the deal |
| **Function × Authority** | Who can move which decision | Pure reporting structure |

Use it when the account has a buying committee, when deals stall on “unknown decision path,” or when reps need to see **coverage gaps by function** at a glance.

## Interaction model

- **Drag a card** across columns to re-tag function; across lanes to re-tag authority.
- **Click a card** to open the contact side panel (prototype: detail drawer).
- **Gap chips** call out empty Decide/Shape cells in critical functions.
- Existing Power / Preference / Relationship / Access chips stay on the card so this view stays compatible with the live Org Chart (CRM) tab.

## Prototype

Open [`index.html`](./index.html) in a browser. Sample account is an anonymized mid-market insurance buyer with intentional coverage holes.

## Mapping into the existing Salesforce tool

Suggested field contract (additive; does not replace `ReportsTo`):

| Concept | Suggested field | Notes |
|---|---|---|
| Function column | `Buying_Function__c` (picklist) | Or map from Department with a per-account override |
| Authority lane | `Decision_Capacity__c` (picklist: Decide / Shape / Evaluate / Inform) | Can default from Power + title ladder, editable by rep |
| Card indicators | existing Power / Preference / Relationship / Access | Unchanged |

View switcher on the Org Chart tab:

`Hierarchy · Title bands · Function × Authority`
