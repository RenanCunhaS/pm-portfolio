# Sprint KPI Dashboard Guide
**Author:** Renan Cunha dos Santos — Senior PM & Scrum Master (PSM I · PSPO I)

> Based on sprint reporting practices at The Wise Dreams (3 teams × 9 people) and TECA Digital (Power BI dashboard, 0 critical defects).

---

## Overview

A sprint KPI dashboard gives the Scrum Master, Product Owner, and stakeholders a real-time view of team health and delivery progress. This guide covers the four core metrics I track, how to calculate them, and how I set up reporting in Power BI + Jira.

---

## Core Metrics

### 1. Velocity

**What:** Story Points completed per sprint (meeting DoD). The primary measure of team throughput.

**How to calculate:**
```
Velocity = Sum of SP for all stories moved to "Done" within the sprint
           (only stories fully completed — partial credit not counted)
```

**How to use it:**
- Track rolling average over last 3 sprints for planning
- Do NOT compare velocity between teams (context always differs)
- Use to answer: "How much can we realistically commit next sprint?"
- Flag sudden drops (>20% below average) → investigate in retrospective

**What it looks like in Jira:**
- Board → Reports → Velocity Chart
- Or extract via Jira API: `/rest/agile/1.0/board/{boardId}/sprint/{sprintId}/issue`

**Sample data schema for Power BI:**
```
| sprint_name | sprint_id | story_id | story_points | status   | completed_date |
|-------------|-----------|----------|--------------|----------|----------------|
| Sprint 1    | SP-001    | US-14    | 8            | Done     | 2025-10-18     |
| Sprint 1    | SP-001    | US-15    | 3            | Done     | 2025-10-17     |
| Sprint 1    | SP-001    | US-19    | 3            | Not Done | —              |
```

---

### 2. Defect Rate

**What:** Number of bugs found in production vs. bugs found during sprint testing. Indicates code quality and QA effectiveness.

**How to calculate:**
```
Defect Escape Rate = (Bugs found in production) / (Total bugs found) × 100

Sprint Defect Rate = (Defects logged during sprint) / (Stories completed) 
```

**Severity classification I use:**

| Severity | Definition | SLA to fix |
|----------|-----------|------------|
| **Critical** | System crash, data loss, security breach | Same sprint |
| **High** | Feature broken, no workaround | Next sprint |
| **Medium** | Feature degraded, workaround exists | Backlog priority |
| **Low** | Minor UI/UX issue | Backlog |

**Target:** Critical defects in production = 0 (achieved at TECA Digital — 4 sprints, 0 critical defects)

---

### 3. Burndown Chart

**What:** Tracks remaining work (SP) against time within the sprint. Shows whether the team is on track to meet the sprint goal.

**How to read it:**
```
Y-axis: Remaining Story Points
X-axis: Sprint days (working days only)

Ideal burndown: straight diagonal line from total SP (Day 0) to 0 (last day)
Actual burndown: what really happened

Patterns to watch:
  - Flat line (no progress) → blocker or scope creep
  - Sudden drop → stories closed in batch (review daily updates habit)
  - Goes above ideal → stories added mid-sprint (protect the sprint!)
  - Ends above 0 → carryover → adjust next sprint commitment
```

**Jira setup:** Board → Active Sprint → Burndown Chart (built-in)

---

### 4. Sprint Closure Report Template

I produce this report at the end of every sprint. Sent to PO and key stakeholders.

```markdown
## Sprint [N] Closure Report
**Team:** [Team name]  
**Sprint dates:** [DD/MM] – [DD/MM/YYYY]  
**Sprint goal:** [Sprint goal statement]  
**Goal achieved:** Yes / No / Partial

---

### Metrics

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| Committed SP | X | Y | 🟢 / 🟡 / 🔴 |
| Completed SP (velocity) | X | Y | 🟢 / 🟡 / 🔴 |
| Completion rate | ≥ 80% | Z% | 🟢 / 🟡 / 🔴 |
| Critical defects (prod) | 0 | N | 🟢 / 🔴 |
| High defects | ≤ 2 | N | 🟢 / 🟡 / 🔴 |
| User feedback score | ≥ 4/5 | X/5 | 🟢 / 🟡 / 🔴 |

---

### Stories Delivered
[List all Done stories with SP]

### Stories Not Completed (carryover)
[List with reason and proposed action]

### Impediments Resolved
[List with resolution summary]

### Open Impediments
[List with owner and ETA]

### Key Decisions Made
[Decisions that affect next sprint or product direction]

### Next Sprint Preview
[Proposed sprint goal and top backlog items]
```

---

## Power BI Setup Notes

### Data sources
- **Jira:** Connect via Jira Power BI connector or export to CSV from Jira Reports
- **Manual tracking:** Use shared Excel/SharePoint list updated daily by SM

### Key visuals I use

| Visual type | Metric | Notes |
|------------|--------|-------|
| Line chart | Velocity trend (last 6 sprints) | Add average line |
| Clustered bar | Committed vs. completed SP per sprint | Highlights over/under commitment |
| Area chart | Burndown (actual vs. ideal) | Per-sprint view |
| KPI card | Defects in production | Red if > 0 critical |
| Donut chart | Story status breakdown | Done / In Progress / To Do / Blocked |
| Table | Impediment log | Filter by status: Open / Resolved |

### Refresh cadence
- During sprint: daily refresh (automated if Jira connector used)
- Sprint closure report: manual review + publish to stakeholders

---

## Team Health Indicators (Beyond the Numbers)

Numbers don't tell the full story. I also track these qualitative signals:

| Signal | Green | Yellow | Red |
|--------|-------|--------|-----|
| Daily stand-up attendance | >90% | 70–90% | <70% |
| Retrospective action completion | >80% | 50–80% | <50% |
| Unplanned work added mid-sprint | <10% of SP | 10–25% | >25% |
| Stories carried over repeatedly | 0 | 1–2 | 3+ |
| Team mood (self-reported) | Mostly positive | Mixed | Mostly negative |

---

*Template by Renan Cunha dos Santos · [linkedin.com/in/renan-cunha-santos](https://linkedin.com/in/renan-cunha-santos)*
