# Sprint Planning Template
**Author:** Renan Cunha dos Santos — Senior PM & Scrum Master (PSM I · PSPO I)

> Based on real sprint planning practices from The Wise Dreams (AI/VR) and TECA Digital projects.

---

## Pre-Planning Checklist

Before the session starts, confirm:

- [ ] Product backlog is refined (user stories estimated and groomed)
- [ ] Previous sprint review completed, feedback captured
- [ ] Team capacity calculated (subtract PTO, meetings, support duties)
- [ ] Sprint goal drafted by PO (can be refined during session)
- [ ] Jira board cleaned: Done items archived, carryover items reviewed

---

## Step 1 — Calculate Team Capacity

```
Sprint duration: __ working days
Team size: __ developers / __ QA / __ others

Per person available hours = (Sprint days × hours/day) − PTO − meetings − overhead

Example (2-week sprint, 5 people, 6h/day productive):
  Gross hours = 10 days × 5 people × 6h = 300h
  Minus PTO (1 person, 2 days) = −12h
  Minus recurring meetings (~1.5h/day/person) = −75h
  Net capacity ≈ 213h → convert to Story Points (team's avg SP/h)
```

**Reference velocity:** Use last 3 sprint average. Don't inflate. Don't overcommit.

---

## Step 2 — Backlog Prioritization (MoSCoW)

Apply MoSCoW to every item before committing to the sprint:

| Priority | Label | Commit to sprint? | Description |
|----------|-------|-------------------|-------------|
| **Must Have** | `M` | Always | Sprint fails without this. Non-negotiable. |
| **Should Have** | `S` | If capacity allows | High value, but workaround exists. Strong preference. |
| **Could Have** | `C` | Only if capacity is surplus | Nice-to-have. First to drop if team is over capacity. |
| **Won't Have** | `W` | No | Agreed out of scope. Log in backlog for future sprints. |

**Rule of thumb:** Must + Should items should not exceed 80% of total capacity. Keep buffer for bugs, rework, and unplanned work.

---

## Step 3 — Story Point Estimation (Planning Poker)

Use Fibonacci sequence: **1 · 2 · 3 · 5 · 8 · 13 · 21 · ∞ · ?**

### Reference scale (calibrate per team)

| Points | Complexity | Example |
|--------|-----------|---------|
| 1 | Trivial | Change a label or copy string |
| 2 | Simple | Add a field to a form |
| 3 | Small | New API endpoint with validation |
| 5 | Medium | New feature with DB changes and unit tests |
| 8 | Large | New module with external integration |
| 13 | Very large | Consider splitting into smaller stories |
| 21+ | Epic | Must be broken down before committing |

### Facilitation tips
- Everyone reveals simultaneously (no anchoring)
- If spread is wide (e.g., 2 vs 13): ask high and low estimators to explain → re-estimate
- ∞ = too large to estimate → split the story
- ? = not enough info → add to refinement backlog

---

## Step 4 — Sprint Goal

The sprint goal should:
- Be a single sentence stating the business value delivered this sprint
- Be achievable with Must + Should items
- Be measurable (how will you know it's done?)

**Template:**
```
This sprint, we will [deliver X] so that [stakeholder Y] can [achieve Z].
Measured by: [metric or condition].
```

**Example (AI Tourism Platform):**
> "This sprint, we will deliver the natural language occupancy forecast query so that hotel managers at Barceló can get instant forecasts without manual reporting. Measured by: response time ≤ 3s and accuracy ≥ 85% on test dataset."

---

## Step 5 — Sprint Backlog Table

Copy and fill this table in your sprint planning notes (Jira, Confluence, or Markdown):

```markdown
| ID | User Story | MoSCoW | SP | Assignee | Acceptance Criteria (key) |
|----|-----------|--------|----|----------|--------------------------|
|    |           |        |    |          |                          |
```

**Total committed SP:** ___  
**Capacity SP:** ___  
**Buffer remaining:** ___

---

## Sprint Planning Meeting Agenda (2-week sprint)

```
Duration: 2–3 hours (scale to sprint length: ~1h per sprint week)

[0:00] Opening — Review sprint goal proposal (PO, 10 min)
[0:10] Capacity check — Confirm availability per person (SM, 10 min)
[0:20] Backlog walkthrough — PO presents top items, team asks questions (40 min)
[1:00] Estimation round — Planning Poker for unestimated items (30 min)
[1:30] Commitment — Team selects items up to capacity, MoSCoW applied (20 min)
[1:50] Sprint goal finalized — Team agrees on wording (10 min)
[2:00] Task breakdown — Optional: break stories into sub-tasks in Jira (30 min)
[2:30] Close — Confirm DoD, open impediments, sprint start confirmed
```

---

## Impediment Log (open at start of each sprint)

| # | Impediment | Raised by | Date | Owner | Status | Resolution |
|---|-----------|-----------|------|-------|--------|------------|
|   |           |           |      |       |        |            |

---

*Template by Renan Cunha dos Santos · [linkedin.com/in/renan-cunha-santos](https://linkedin.com/in/renan-cunha-santos)*
