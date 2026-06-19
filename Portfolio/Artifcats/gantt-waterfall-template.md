# Gantt Template — Waterfall / PMI / PMBOK
**Author:** Renan Cunha dos Santos — Senior PM & Scrum Master (PSM I · PSPO I)

> Based on the Sales Campaign Automation Portal delivered at Intelcia/MEO (Faro, Portugal).
> Tools used: MS Project · SharePoint on Azure Cloud · PMBOK framework.

---

## Project Lifecycle Overview (PMBOK)

```
INITIATING → PLANNING → EXECUTING → MONITORING & CONTROLLING → CLOSING
    │             │           │                 │                   │
 Charter       Scope      Team work        Status reports      Formal sign-off
 Stakeholders  WBS        Deliverables     Change control      Lessons learned
 Kick-off      Gantt      Procurement      Risk management     Archive
```

---

## Phase 1 — Initiating

### Deliverables
- **Project Charter** — signed by sponsor
- **Stakeholder Register** — all parties identified with influence/interest matrix
- **Kick-off Meeting** — agenda, minutes, decisions logged

### Kick-off Meeting Agenda Template
```
[Project name] — Kick-off Meeting
Date: ___  Duration: 90 min  Location / link: ___

Attendees: [list all with roles]

Agenda:
  1. Project objectives and business case (Sponsor, 15 min)
  2. Scope overview — what's IN and what's OUT (PM, 20 min)
  3. Timeline and key milestones (PM, 15 min)
  4. Team structure and RACI (PM, 10 min)
  5. Budget overview (PM, 10 min)
  6. Risks and assumptions (All, 10 min)
  7. Communication plan and reporting cadence (PM, 5 min)
  8. Questions (All, 5 min)

Decision log: [table]
Next steps: [table with owner + due date]
```

---

## Phase 2 — Planning

### Work Breakdown Structure (WBS)

Decompose the project into deliverables. Each leaf node should be estimatable (ideally 8–80 hours).

**Example WBS — Sales Campaign Automation Portal:**
```
1.0 SALES CAMPAIGN AUTOMATION PORTAL
  1.1 Project Management
    1.1.1 Project Charter
    1.1.2 Project Plan (Gantt)
    1.1.3 Status Reports (weekly)
    1.1.4 Change Log
    1.1.5 Project Closure Report
  
  1.2 Requirements
    1.2.1 Stakeholder interviews
    1.2.2 Requirements document
    1.2.3 Requirements sign-off
  
  1.3 Design
    1.3.1 System architecture document
    1.3.2 UI/UX wireframes
    1.3.3 Design review & approval
  
  1.4 Development
    1.4.1 Database schema + setup
    1.4.2 Campaign creation module
    1.4.3 Campaign approval workflow
    1.4.4 Reporting dashboard
    1.4.5 Integration with CRM
    1.4.6 User authentication & roles
  
  1.5 Testing
    1.5.1 Test plan
    1.5.2 Unit testing
    1.5.3 Integration testing
    1.5.4 UAT (User Acceptance Testing)
    1.5.5 UAT sign-off
  
  1.6 Deployment
    1.6.1 Staging deployment
    1.6.2 Stakeholder demo on staging
    1.6.3 Production deployment
    1.6.4 Go-live confirmation
  
  1.7 Closure
    1.7.1 Training (end users)
    1.7.2 Documentation handover
    1.7.3 Formal client acceptance
    1.7.4 Lessons learned
```

---

### Gantt Chart Structure (MS Project)

Use this as your column template in MS Project or Excel:

| WBS | Task Name | Duration | Start | Finish | Predecessor | Resource | % Complete | Milestone |
|-----|-----------|----------|-------|--------|-------------|----------|-----------|-----------|
| 1.1 | Project Management | 120d | D+0 | D+120 | — | PM | — | — |
| 1.2.1 | Stakeholder interviews | 5d | D+1 | D+5 | — | PM | | |
| 1.2.2 | Requirements document | 7d | D+6 | D+12 | 1.2.1 | PM + Analyst | | |
| 1.2.3 | Requirements sign-off | 1d | D+13 | D+13 | 1.2.2 | Sponsor | | ✓ |
| 1.3.1 | Architecture design | 5d | D+14 | D+18 | 1.2.3 | Dev Lead | | |
| 1.3.2 | UI/UX wireframes | 7d | D+14 | D+20 | 1.2.3 | Designer | | |
| 1.3.3 | Design sign-off | 1d | D+21 | D+21 | 1.3.1, 1.3.2 | PO + Sponsor | | ✓ |
| 1.4 | Development | 45d | D+22 | D+66 | 1.3.3 | Dev team | | |
| 1.5.4 | UAT | 10d | D+67 | D+76 | 1.4 | Users + QA | | |
| 1.5.5 | UAT sign-off | 1d | D+77 | D+77 | 1.5.4 | Sponsor | | ✓ |
| 1.6.3 | Production deployment | 1d | D+80 | D+80 | 1.5.5, 1.6.2 | DevOps | | ✓ |
| 1.7.3 | Formal client acceptance | 1d | D+90 | D+90 | 1.7.1, 1.7.2 | Sponsor | | ✓ |

**Key milestones (mark in red in MS Project):**
```
M1: Requirements sign-off    → D+13
M2: Design approved          → D+21
M3: Dev complete             → D+66
M4: UAT sign-off             → D+77
M5: Production go-live       → D+80
M6: Formal acceptance        → D+90
```

---

## Phase 3 — Executing

### Status Report Template (weekly)

```markdown
## Weekly Status Report — Week [N]
**Project:** [Name]  
**PM:** Renan Cunha dos Santos  
**Date:** [DD/MM/YYYY]  
**Overall status:** 🟢 On Track / 🟡 At Risk / 🔴 Off Track

---

### Summary
[2–3 sentence summary of week's progress]

### Schedule Status
| Milestone | Planned date | Forecast date | Status |
|-----------|-------------|--------------|--------|
| M1 — Requirements sign-off | DD/MM | DD/MM | 🟢 |
| M2 — Design approved | DD/MM | DD/MM | 🟢 |

### Key Accomplishments This Week
- [Item 1]
- [Item 2]

### Planned Next Week
- [Item 1]
- [Item 2]

### Issues & Risks
| # | Description | Impact | Probability | Mitigation | Owner | Status |
|---|------------|--------|-------------|-----------|-------|--------|
|   |            |        |             |           |       |        |

### Budget Status
| Category | Budget | Spent to date | Forecast at completion | Variance |
|----------|--------|--------------|----------------------|---------|
| Labour   | €X     | €Y           | €Z                   | €+/-    |
| Tools    | €X     | €Y           | €Z                   | €+/-    |
| Other    | €X     | €Y           | €Z                   | €+/-    |
| **Total**| **€X** | **€Y**       | **€Z**               | **€+/-**|

### Decisions Required
| Decision | Owner | Deadline |
|----------|-------|---------|
|          |       |         |
```

---

## Phase 4 — Monitoring & Controlling

### Change Control Process

```
Change requested (any stakeholder)
        ↓
PM logs Change Request (CR) in Change Log
        ↓
PM assesses impact: scope / schedule / budget / quality
        ↓
Impact < threshold? ──Yes──→ PM approves + updates Gantt
        ↓ No (above threshold)
Change Control Board review (PM + Sponsor + PO)
        ↓
Approved? ──No──→ Change rejected, logged, requester notified
        ↓ Yes
PM updates: Gantt · Budget · Scope document · Stakeholder communication
```

### Change Log Template

| CR# | Date | Requestor | Description | Impact (scope/time/cost) | Status | Decision | Approved by |
|-----|------|-----------|-------------|--------------------------|--------|----------|-------------|
|     |      |           |             |                          |        |          |             |

---

## Phase 5 — Closing

### Formal Acceptance Checklist

- [ ] All deliverables completed and accepted by client
- [ ] UAT signed off by user representatives
- [ ] All open defects resolved or formally deferred (with agreement)
- [ ] Training completed for end users
- [ ] Technical documentation handed over
- [ ] User manual / quick-start guide delivered
- [ ] Final budget reconciliation completed
- [ ] Project closure report written and approved
- [ ] Lessons learned document produced and shared
- [ ] Team recognition completed
- [ ] Project archived in SharePoint / Azure

### Lessons Learned Template

```markdown
## Lessons Learned — [Project Name]

**PM:** Renan Cunha dos Santos  
**Date:** [DD/MM/YYYY]

### What went well
| Area | Observation | Recommendation for next project |
|------|------------|--------------------------------|
|      |            |                                |

### What could be improved
| Area | What happened | Root cause | Recommendation |
|------|--------------|------------|----------------|
|      |              |            |                |

### Key metrics (actuals vs. plan)
| Metric | Planned | Actual | Variance |
|--------|---------|--------|----------|
| Duration | X days | Y days | +/- Z days |
| Budget | €X | €Y | +/- €Z |
| Scope changes | — | N CRs | — |
| Defects found in UAT | — | N | — |
```

---

*Template by Renan Cunha dos Santos · [linkedin.com/in/renan-cunha-santos](https://linkedin.com/in/renan-cunha-santos)*
