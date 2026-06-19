# Definition of Done + Acceptance Criteria Guide
**Author:** Renan Cunha dos Santos — Senior PM & Scrum Master (PSM I · PSPO I)

> Used in AI/VR projects at The Wise Dreams and software delivery at Intelcia/MEO.

---

## Part 1 — Definition of Done (DoD)

The DoD is the shared team agreement on what "complete" means for any user story. It applies to **every** story, every sprint. No exceptions.

### Standard DoD Checklist (AI/Tech Projects)

#### Development
- [ ] Code written and peer-reviewed (minimum 1 reviewer)
- [ ] Unit tests written and passing (coverage ≥ 80% for new code)
- [ ] Integration tests pass
- [ ] No critical or high-severity bugs open
- [ ] Code merged to main/develop branch (no open PRs)

#### Quality Assurance
- [ ] QA testing completed against acceptance criteria
- [ ] Regression test suite passed
- [ ] Edge cases tested (empty inputs, timeouts, error states)
- [ ] Performance benchmarks met (as defined per story)

#### Product & Documentation
- [ ] Product Owner reviewed and accepted the story
- [ ] Acceptance criteria all verified (see Part 2)
- [ ] User-facing copy reviewed and approved
- [ ] Technical documentation updated (if applicable)
- [ ] API documentation updated (if applicable)

#### Deployment
- [ ] Deployed to staging environment
- [ ] Smoke test on staging passed
- [ ] Feature flag configured (if applicable)
- [ ] Rollback plan documented

#### Sprint Closure
- [ ] Jira ticket status updated to Done
- [ ] Story closed in sprint board
- [ ] Velocity updated in sprint report

---

### DoD for AI/LLM-Specific Stories (additional items)

- [ ] Model response validated against test dataset (accuracy threshold met)
- [ ] Latency benchmarked (P95 response time ≤ defined SLA)
- [ ] Hallucination/error rate within acceptable range
- [ ] Fallback behaviour tested (model timeout, API failure)
- [ ] Prompt versioned and documented
- [ ] Data privacy review completed (PII handling confirmed)

---

## Part 2 — Acceptance Criteria Writing Guide

Acceptance criteria define the conditions a story must meet to be accepted. Written by the PM/SM together with the Product Owner during backlog refinement.

### Format: Given / When / Then (BDD style)

```
Given [precondition / initial context]
When  [action or event]
Then  [expected outcome]
```

This format is unambiguous, testable, and eliminates interpretation disputes.

---

### Examples from Real Projects

#### Example 1 — LLM Query Feature (The Wise Dreams)
**User Story:** As a hotel manager, I want to query the LLM via natural language to get occupancy forecasts.

**Acceptance Criteria:**
```
Given I am logged in as a hotel manager
When I type a natural language query (e.g. "What will occupancy be next weekend?")
Then the system returns a forecast within 3 seconds
  And the response accuracy is ≥ 85% against historical data
  And if the model times out, a fallback message is shown

Given the model API is unavailable
When I submit a query
Then the system shows a user-friendly error message (not a raw error)
  And the error is logged for the engineering team
```

#### Example 2 — CSV Export Feature (The Wise Dreams)
**User Story:** As a TUI analyst, I want to export forecast data to CSV with one click.

**Acceptance Criteria:**
```
Given I am viewing a forecast report
When I click "Export to CSV"
Then a CSV file downloads automatically
  And the file includes column headers in the first row
  And the file is UTF-8 encoded (supports accented characters)
  And the filename includes the date (e.g. forecast_2025-11-01.csv)
  And the feature works on mobile browsers
```

#### Example 3 — Sales Campaign Portal (Intelcia/MEO)
**User Story:** As a sales team member, I want to launch a new campaign without opening an IT ticket.

**Acceptance Criteria:**
```
Given I am logged in with a sales role
When I complete the campaign creation form and click "Launch"
Then the campaign is created and activated within 30 seconds
  And I receive a confirmation email with campaign details
  And the campaign appears in my dashboard immediately
  And no IT team member action is required
  
Given I try to launch a campaign with missing required fields
When I click "Launch"
Then the form shows inline validation errors
  And the campaign is NOT created
```

---

### Acceptance Criteria Anti-Patterns to Avoid

| ❌ Avoid | ✅ Instead |
|---------|----------|
| "The feature should work correctly" | Define what "correctly" means specifically |
| "The system should be fast" | "Response time ≤ 2 seconds at P95" |
| "Users should be able to export data" | Specify file format, encoding, filename, trigger |
| "It should look good on mobile" | "Renders without horizontal scroll on 375px viewport" |
| "Handle errors gracefully" | Define each error state and expected message |
| "The form should validate" | List every field, rule, and error message |

---

### Acceptance Criteria Checklist (before story enters sprint)

- [ ] At least 1 happy path scenario defined
- [ ] At least 1 failure/error scenario defined
- [ ] Edge cases identified (empty state, maximum input, no data)
- [ ] Performance requirement specified (if applicable)
- [ ] Testable — QA can write test cases directly from these criteria
- [ ] Product Owner agrees these criteria = done
- [ ] Dev team confirms criteria are achievable in this sprint

---

*Template by Renan Cunha dos Santos · [linkedin.com/in/renan-cunha-santos](https://linkedin.com/in/renan-cunha-santos)*
