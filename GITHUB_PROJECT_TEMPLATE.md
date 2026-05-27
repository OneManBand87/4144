# NeuroDIV GitHub Project Management Template

This template defines a reusable **GitHub Projects field schema** and operating model for:
- Accounting workflows
- AI build tasks
- Research tasks
- Deliverable tracking

Use this document as the standard when creating or updating a GitHub Project.

## 1) Standard Field Schema

### Core required fields

| Field name | Field type | Required | Purpose | Example values |
|---|---|---:|---|---|
| Status | Single select | Yes | Lifecycle tracking | Backlog, Ready, In Progress, In Review, Blocked, Done, Archived |
| Priority | Single select | Yes | Ordering & urgency | P0 Critical, P1 High, P2 Medium, P3 Low |
| Owner | People | Yes | Accountability | @username |
| Effort | Number | Yes | Relative sizing / expected work | 1, 2, 3, 5, 8, 13 |
| Due date | Date | No (recommended for deliverables) | Deadline tracking | 2026-06-01 |
| Iteration/Sprint | Iteration | Yes (for active delivery projects) | Sprint cadence | Sprint 2026-W22 |
| Issue type | Single select | Yes | Work classification | Feature, Bug, Research, Ops, Accounting, Documentation |
| Parent issue | Parent issue field | No (required for sub-work) | Roll-up planning | #123 |
| Sub-issue progress | Sub-issue progress field | Auto | Child completion roll-up | 0–100% (computed) |

### Recommended optional fields

| Field name | Field type | Required | Purpose | Example values |
|---|---|---:|---|---|
| Workstream | Single select | No | Functional lane | Finance, Platform, AI, Research, Delivery |
| Risk score | Number | No | Delivery risk indicator | 1-5 |
| Review date | Date | No | Planned review/checkpoint | 2026-06-07 |
| External links | Text | No | Docs/spec references | URL to brief/spec |
| Blockers | Text | No | Constraint tracking | "Waiting on API approval" |
| PR status | Single select | No | Dev flow checkpoint | Not Started, Open, Awaiting Review, Merged |

---

## 2) Field Type-to-Use Mapping

| Field type | Best use |
|---|---|
| Text | Notes, blockers, external links |
| Number | Effort score, risk score, hours |
| Date | Due dates, review dates |
| Single select | Priority, status, workstream |
| Iteration | Sprint planning |
| Issue fields | Structured issue metadata |
| Parent/sub-issue fields | Hierarchical task tracking |
| Pull request fields | Dev workflow tracking |

---

## 3) Project Setup Checklist

Use this checklist whenever creating a new project.

### A. Define project structure
- [ ] Confirm project scope (accounting, AI build, research, deliverables, or mixed).
- [ ] Decide required fields from the core schema.
- [ ] Define status stages and priority scale.

### B. Add custom fields
- [ ] Create all core fields: Status, Priority, Owner, Effort, Due date, Iteration/Sprint, Issue type.
- [ ] Enable Parent issue and Sub-issue progress.
- [ ] Add optional fields needed by workflow (Risk score, Review date, PR status, Blockers).

### C. Create default views
- [ ] **Table view**: full metadata and sorting by Priority, Due date.
- [ ] **Board view**: grouped by Status.
- [ ] **Roadmap view**: grouped by Iteration/Sprint or sorted by Due date.

### D. Add filters and saved slices
- [ ] Filter by Owner (personal queue views).
- [ ] Filter by Status (active work).
- [ ] Filter by Iteration/Sprint (current cycle).
- [ ] Filter by Issue type (e.g., Research-only).

### E. Configure automation rules
- [ ] On item added, set Status = Backlog.
- [ ] On PR linked and opened, set Status = In Review (or PR status = Open).
- [ ] On PR merged, set Status = Done.
- [ ] On status moved to Done, set completion date (if used).

### F. Link work items
- [ ] Link issues and pull requests.
- [ ] Ensure major module issues are parents.
- [ ] Ensure implementation steps are sub-issues.

---

## 4) NeuroDIV Task Architecture Pattern

### Convert scattered ideas into trackable work
1. Capture each idea as an issue.
2. Tag Issue type and Workstream.
3. Assign Owner and Effort.
4. Schedule into an Iteration/Sprint.

### Use hierarchy intentionally
- **Parent issues**: major modules / initiatives (e.g., "AI Reconciliation Engine").
- **Sub-issues**: concrete execution tasks (API work, validation tests, report outputs).
- **Sub-issue progress**: monitor implementation completion at parent level.

### Use iterations for weekly build cycles
- Create weekly iterations (e.g., 2026-W22, 2026-W23).
- Move unfinished items forward explicitly during planning.
- Keep no more than one active iteration per owner unless justified.

---

## 5) Field Governance Policy

### Required fields policy
- Required at intake: Status, Priority, Owner, Effort, Issue type.
- Required before sprint start: Iteration/Sprint.
- Required for committed deliverables: Due date.

### Field administration policy
- Only project admins can rename/delete fields.
- Any schema change requires documented rationale in project notes/changelog.
- Do not repurpose field meanings without announcement.

### Naming conventions
- Use Title Case field names.
- Keep names short and explicit (e.g., "Due date", not "Target Delivery Deadline").
- Prefix team-specific fields if needed (e.g., "AI: Model Version").

### Labels vs fields
Use **fields** when data is:
- Structured, filterable, sortable, or required for reporting.

Use **labels** when data is:
- Lightweight categorization across repos (topic tags, tech tags, ad hoc markers).

### Archive policy
- Archive completed items after 30 days (or team SLA).
- Keep parent issues open until all sub-issues complete and outcomes are documented.
- Run a monthly archive + stale backlog review.

---

## 6) Reusable Prompt for Project Design

Use this with AI assistants or internal planning docs:

> "Design a GitHub Projects field structure for [project], including custom fields, views, automations, and issue hierarchy."

Optional expansion prompt:

> "Include required vs optional fields, recommended status values, iteration cadence, governance rules, and suggested filters for role-based views."
