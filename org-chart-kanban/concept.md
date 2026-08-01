# Concept diagram — Function × Authority board

```mermaid
flowchart TB
  subgraph axes [Board axes]
    COL[Columns = buying functions<br/>Executive · UW · Claims · IT · Procurement · Finance · Legal]
    ROW[Swim lanes = decision capacity<br/>Decide → Shape → Evaluate → Inform]
  end

  subgraph card [Contact card]
    P[Person + title]
    S[Power · Preference · Relationship · Access]
    P --> S
  end

  COL --> CELL[Cell = function ∩ authority]
  ROW --> CELL
  card --> CELL

  CELL --> GAP[Empty Decide/Shape on critical function<br/>= coverage gap]
  CELL --> MOVE[Drag across column = re-tag function<br/>Drag across lane = re-tag authority]
```

## Compared to existing Org Chart (CRM) views

```mermaid
flowchart LR
  H[Hierarchy view<br/>ReportsTo tree] -->|who reports to whom| Q1[Sponsor path]
  B[Title bands view<br/>seniority ladder] -->|how senior| Q2[Power distribution]
  K[Function × Authority<br/>kanban + swim lanes] -->|who can decide in which function| Q3[Buying committee coverage]
```

## Suggested Salesforce view switcher

```text
Account → Org Chart (CRM)
  [ Hierarchy ]  [ Title bands ]  [ Function × Authority ]
```
