# Jira for QA — Practical Learning Documentation

> **Learning Phase:** Jira for Software Testing / QA  
> **Project Used:** Software Development Practice  
> **Jira Project Key:** `SDP`  
> **Learning Style:** Practical, production-oriented, hands-on  
> **Status:** Completed — Jira learning phase

---

## 1. Overview

This document records the practical Jira learning completed as part of the QA learning journey.

The focus was not on learning Jira only through theory. Jira was used as a real-world project and QA management tool. The exercises simulated how a QA tester works with developers, requirements, bugs, priorities, boards, dashboards, reports, filters, and JQL.

The practice project used throughout the exercises was:

- **Project Name:** Software Development Practice
- **Project Key:** `SDP`
- **Board Type:** Kanban-style board
- **Board Columns:** To Do, In Progress, Done
- **Backlog:** Enabled
- **Sprints:** Not used
- **Purpose:** Practice software development and QA workflows

> **Important:** Some development and testing activities in this Jira project were simulations for learning. They should not be presented as evidence of testing a real production application.

---

# 2. Jira Learning Objectives

The main objectives were to learn how to:

- Use Jira in a real software development workflow.
- Create and manage project work items.
- Understand Epics, Stories, Tasks, Sub-tasks, and Bugs.
- Work with backlog and Kanban boards.
- Assign work to team members.
- Communicate through Jira comments.
- Track development and QA progress.
- Report and manage bugs.
- Link related issues and blockers.
- Use labels and priorities.
- Perform developer-to-QA handoffs.
- Create QA dashboards.
- Understand Jira reports.
- Search and filter work items.
- Use JQL for practical QA tasks.
- Create reusable QA filters.

---

# 3. Jira in a Real-World QA Workflow

A typical software workflow practiced in Jira was:

```text
Requirement
    ↓
Epic / Story
    ↓
Task / Sub-task
    ↓
Development
    ↓
Bug Found
    ↓
Bug Report
    ↓
Developer Fix
    ↓
QA Retest
    ↓
Done / Closed
```

Jira was therefore treated as more than a bug-reporting tool. It was used to track work throughout the software development lifecycle.

---

# 4. Important Jira Terms Practiced

| Term | Practical Meaning |
|---|---|
| Project | Container for related software work |
| Issue / Work Item | Individual piece of work in Jira |
| Epic | Large feature or area of work |
| Story | User-focused requirement |
| Task | General development or project work |
| Sub-task | Smaller work item belonging to a parent issue |
| Bug | Defect or unexpected behavior |
| Summary | Short title of an issue |
| Description | Detailed information about the issue |
| Reporter | Person who created/reported the issue |
| Assignee | Person responsible for the issue |
| Priority | Importance/urgency of the work |
| Severity | Impact of a defect; practiced mainly in QA bug reporting |
| Status | Current state of the issue |
| Label | Tag used for categorization/search |
| Attachment | File or screenshot added to an issue |
| Comment | Communication/update added to an issue |
| Epic Link / Parent | Relationship connecting work to a larger feature |
| Board | Visual representation of work |
| Backlog | List of planned work |
| Filter | Saved or temporary search criteria |
| JQL | Jira Query Language used for advanced searching |

---

# 5. Project Setup

## 5.1 Project Created

A Jira project named:

```text
Software Development Practice
```

was created with the key:

```text
SDP
```

The project used a Kanban-style workflow.

### Board

The main board contained:

```text
To Do → In Progress → Done
```

The board was also configured/grouped around Epics during practice.

---

# 6. Day 1 — Jira Practical Introduction

## Objective

Understand Jira by actually using the platform.

## Activities Completed

- Created the Jira project.
- Opened the project dashboard.
- Explored the board.
- Explored the Create button.
- Opened Issues / Work Items.
- Explored project settings.
- Practiced searching for work items.
- Explored filters.
- Observed how work items appear and disappear from board columns based on status.

## Practical Lesson

Jira is used by multiple roles in a development team:

- QA
- Developer
- Business Analyst
- Project Manager
- Scrum Master
- Product Owner

The same Jira project can contain development work, requirements, bugs, and QA-related communication.

---

# 7. Day 2 — Creating Real Project Work

## 7.1 Epic

An Epic named:

```text
User Authentication
```

was created.

The Epic represented the larger authentication/login feature.

---

## 7.2 Story — SDP-2

### Summary

```text
User can log in using email and password
```

### Type

```text
Story
```

### User Story

```text
As a registered user,
I want to log in using my email and password,
so that I can access my account.
```

### Acceptance Criteria

```text
- The user can enter an email address.
- The user can enter a password.
- The user can submit the login form.
- The system allows login with valid credentials.
- The system displays an error message for invalid credentials.
- The system prevents login when required fields are empty.
```

### Other Information

- Priority: Medium
- Label: `authentication`
- Reporter: User

The story was associated with the `User Authentication` Epic.

---

## 7.3 Task — SDP-4

### Summary

```text
Design login page
```

This represented UI/design work for the login feature.

---

# 8. Day 3 — Sub-tasks and Bug Workflow

## 8.1 Sub-task — Login Form Validation

A sub-task was created under the login story.

### Summary

```text
Implement login form validation
```

### Description

```text
Implement validation for the login form.

The form should:
- Validate the email field.
- Validate the password field.
- Prevent submission when required fields are empty.
- Display appropriate validation messages.
```

### Activities

- Assigned to self.
- Moved from To Do to In Progress.
- Added a developer progress comment.
- Practiced the development workflow.

---

## 8.2 Practice Bug

A practice bug was created:

### Summary

```text
Login form allows submission with empty password
```

### Description

```text
## Steps to Reproduce

1. Open the login page.
2. Enter a valid email address.
3. Leave the password field empty.
4. Click the Login button.

## Expected Result

The system should prevent submission and display a validation message indicating that the password is required.

## Actual Result

The login form allows the user to submit the form with an empty password.

## Environment

Web application
```

### Bug Information

- Priority: High
- Label: `authentication`
- Assignee: Self
- Linked to: Login story
- Relationship practiced: `relates to`

> This was a practice bug. The behavior was simulated and was not evidence from testing a real login application.

---

# 9. Bug Lifecycle Practice

The bug was taken through a realistic workflow:

```text
To Do
  ↓
In Progress
  ↓
Developer Investigation
  ↓
Fix Implemented
  ↓
Fixed
  ↓
QA Retest
  ↓
Done
```

## Developer Comment

```text
Investigating the login validation issue.
I will update the password validation and prevent
form submission when the password field is empty.
```

## Developer Fix Comment

```text
The password field validation has been updated.
The form should now prevent submission when the password is empty.
Ready for QA retesting.
```

## QA Retest Comment

```text
Retest performed.

The password validation issue was checked against the
reported requirement. The bug behavior is considered fixed
for this practice workflow.
```

This exercise demonstrated the communication between development and QA.

---

# 10. Day 4 — Backlog and Prioritization

The backlog was used to organize project work.

The practiced order included:

1. `SDP-1` — Set up the project development environment
2. `SDP-4` — Design login page
3. `SDP-2` — User can log in using email and password
4. `SDP-6` — Login form allows submission with empty password

## Priority Practice

Examples:

- `SDP-1` → Highest
- `SDP-4` → High
- Login story → Medium

The exercise demonstrated that backlog ordering and priority are related but are not exactly the same thing.

---

# 11. Task Type Correction — SDP-7

A work item was initially created with the wrong issue type.

It was then moved to the correct type.

### Final Summary

```text
Set up login page UI
```

### Type

```text
Task
```

### Description

```text
Create the basic login page UI.

The page should contain:
- Email input field
- Password input field
- Login button
```

### Workflow Practiced

```text
To Do → In Progress → Done
```

Comments were also added during the workflow.

This demonstrated that Jira work items can be corrected and managed without recreating them unnecessarily.

---

# 12. Day 5 — Issue Search and Filtering

Practical searches were performed for:

- Bugs
- Fixed Bugs
- Issues assigned to me
- High-priority issues
- Highest-priority issues
- Authentication-related issues
- Stories
- Tasks
- Login-related issues

## Saved Filters

Two important saved filters were created/practiced:

### Bugs Ready for Retest

Used to find bugs that require QA retesting.

### My Assigned Work

Used to find work assigned to the current Jira user.

These filters demonstrated how QA testers can create reusable views instead of manually searching every time.

---

# 13. Day 6 — Story → Sub-task → QA Workflow

A second sub-task was created under the login story.

## Sub-task

```text
Implement login button functionality
```

### Description

```text
Implement the login button functionality.

The button should:
- Submit the login form.
- Validate the entered credentials.
- Allow successful login with valid credentials.
- Display an error for invalid credentials.
```

### Workflow

```text
To Do → In Progress → Done
```

A developer completion comment and QA handoff comment were added.

The parent story was then reviewed to check the state of its sub-tasks.

The remaining login validation work was completed, followed by:

```text
Parent Story
To Do → In Progress → Done
```

QA verification comments were added.

> The development and QA verification in this exercise were simulated for Jira learning.

---

# 14. Day 7 — Second Bug Lifecycle

Another practice bug was created.

### Summary

```text
Login accepts an invalid email format
```

### Steps to Reproduce

```text
1. Open the login page.
2. Enter an invalid email address such as `user@`.
3. Enter a valid password.
4. Click the Login button.
```

### Expected Result

```text
The system should reject the invalid email format
and display an appropriate validation message.
```

### Actual Result

```text
The login form accepts the invalid email format.
```

### Environment

```text
Web application
```

### Other Information

- Priority: High
- Label: `authentication`
- Linked to: `SDP-2`
- Assignee: Self

The complete bug workflow was practiced again:

```text
To Do
→ In Progress
→ Developer Fix
→ Done / Fixed
→ QA Retest
```

> This was also a simulated practice defect.

---

# 15. Day 8 — Blockers and Work Management

A task was created:

```text
Prepare login feature test data
```

### Description

```text
Prepare test data required for testing the login feature.

Include:
- Valid user credentials
- Invalid user credentials
- Invalid email formats
- Empty required fields
```

### Workflow

The task was:

```text
To Do → In Progress
```

A blocker was then recorded.

### Blocker Comment

```text
Blocked: waiting for the finalized login requirements before completing the test data.
```

The task was marked as blocked where the Jira workflow allowed it.

After the blocker was resolved, an update was added:

```text
The login requirements have been finalized.
The blocker has been resolved and I can continue the test data preparation.
```

The task was then completed.

---

## SDP-1 Environment Setup

The project environment setup task was also worked on.

Comment:

```text
This task is ready to be picked up for development.
```

Then:

```text
Started working on the project environment setup.
```

This demonstrated how Jira can communicate development progress.

---

# 16. Day 9 — Team Collaboration

Collaboration features were practiced using `SDP-1`.

## Development / QA Comment

```text
Development work is in progress.
QA will verify the environment once the setup is completed.
```

## Screenshot Attachment

A non-sensitive project setup screenshot was attached.

Comment:

```text
Attached the current project setup screenshot for reference.
```

## Issue Linking

`SDP-1` was linked with:

```text
SDP-2
```

using:

```text
relates to
```

`SDP-1` was also linked to:

```text
SDP-7
```

using:

```text
blocks
```

The meaning practiced was:

```text
SDP-1 blocks SDP-7
```

A QA status update was also added:

```text
QA update: The related login feature work is completed,
but the project environment setup is still in progress.
QA verification will begin once the environment is ready.
```

---

# 17. Day 10 — Jira Dashboard

A dedicated dashboard was created.

### Dashboard Name

```text
QA Practice Dashboard
```

### Description

```text
Dashboard for monitoring QA work, bugs, and assigned issues
in the Software Development Practice project.
```

### Visibility

Private / only the user.

---

## Gadgets Practiced

### Filter Results

Configured around the saved:

```text
Bugs Ready for Retest
```

### Assigned to Me

Used to display issues assigned to the current Jira user.

### Pie Chart

Configured using:

```text
Bugs Ready for Retest
```

and grouped by:

```text
Priority
```

This demonstrated how dashboards can provide a quick overview of QA work.

---

# 18. Dashboard Navigation Exercise

The saved filter:

```text
Bugs Ready for Retest
```

was opened from the dashboard.

The navigation path practiced was:

```text
Dashboard
   ↓
Saved Filter
   ↓
Bug
   ↓
Full Bug Details
```

The bug details were inspected without changing the issue.

This demonstrated how a QA dashboard can be used as an entry point to actual work items.

---

# 19. Day 11 — Jira Reports

The current Jira Cloud interface provided reports such as:

- Work items by status
- Work items by type
- Work items by assignee
- Work item creation trend
- Work item cycle time
- Work item lead time
- Work item completion trend
- Work item details

## Report Observations from the Practice Project

### Work Items by Type

The project showed:

```text
2 Bugs
```

### Work Items by Assignee

The report showed:

```text
5 Unassigned
```

### Work Item Cycle Time

The highest observed cycle time was approximately:

```text
8 hours
```

### Work Item Lead Time

The observed lead time was approximately:

```text
25 hours
```

### Work Item Completion Trend

The observed completion value was:

```text
5
```

### Work Item Details

Examples included:

```text
SDP-6 → Bug → Fixed
SDP-9 → Bug → Done
```

These reports demonstrated how Jira can provide project-level visibility without opening every issue individually.

---

# 20. Day 12 — Practical JQL

JQL stands for:

```text
Jira Query Language
```

JQL was practiced through the Jira advanced search interface.

The current Jira UI used:

```text
Basic | JQL
```

to switch into advanced search.

---

## JQL Exercise 1 — Find All Project Work

```jql
project = SDP
```

### Result

The project work items were displayed, including:

```text
SDP-1 through SDP-10
```

---

## JQL Exercise 2 — Find Bugs

```jql
project = SDP
AND issuetype = Bug
```

This returned the project's Bug work items.

---

## JQL Exercise 3 — Find Open Bugs

```jql
project = SDP
AND issuetype = Bug
AND status != Done
```

### Result

```text
SDP-6
```

This demonstrated how QA can find Bugs that are not yet completed.

---

## JQL Exercise 4 — Find Bugs Assigned to Me

```jql
project = SDP
AND issuetype = Bug
AND assignee = currentUser()
```

### Result

```text
SDP-6
SDP-9
```

`currentUser()` was practiced as a way to dynamically refer to the currently logged-in Jira user.

---

## JQL Exercise 5 — Find My Open Bugs

```jql
project = SDP
AND issuetype = Bug
AND assignee = currentUser()
AND status != Done
```

### Result

```text
SDP-6
```

This is a practical QA query for finding the user's own unfinished Bugs.

---

## JQL Exercise 6 — Find High-Priority Bugs

```jql
project = SDP
AND issuetype = Bug
AND priority = High
```

### Result

```text
SDP-6
SDP-9
```

This demonstrated priority-based QA filtering.

---

## JQL Exercise 7 — Find Bugs Ready for Retest

```jql
project = SDP
AND issuetype = Bug
AND status = Fixed
```

### Result

```text
SDP-6
```

This is one of the most practical queries for a QA workflow:

```text
Developer marks Bug Fixed
          ↓
JQL finds Fixed Bugs
          ↓
QA performs retest
```

---

## JQL Exercise 8 — Find Authentication Work

The authentication label was practiced using:

```jql
project = SDP
AND labels = "authentication"
```

The label:

```text
authentication
```

was verified on `SDP-2`.

This demonstrated the importance of checking the actual issue field when a filter unexpectedly returns no results.

---

## JQL Exercise 9 — Authentication Work Not Done

```jql
project = SDP
AND labels = "authentication"
AND status != Done
```

This query was used to find authentication-related work that was not completed.

---

## JQL Exercise 10 — My Active Work

```jql
project = SDP
AND assignee = currentUser()
AND status IN ("To Do", "In Progress")
ORDER BY priority DESC
```

This was the final practical JQL exercise.

It combines:

- Project filtering
- Assignee filtering
- Multiple status values
- Priority sorting

The result is useful for viewing active personal work, with higher-priority work listed first.

---

# 21. Important JQL Patterns Learned

| Pattern | Purpose |
|---|---|
| `project = SDP` | Filter by project |
| `issuetype = Bug` | Find Bugs |
| `status != Done` | Exclude completed work |
| `assignee = currentUser()` | Find work assigned to yourself |
| `priority = High` | Find High-priority work |
| `status = Fixed` | Find Fixed Bugs |
| `labels = "authentication"` | Find labeled work |
| `status IN ("To Do", "In Progress")` | Match multiple statuses |
| `ORDER BY priority DESC` | Sort by priority |

---

# 22. Final QA Filter

A reusable QA filter was created/practiced for Bugs that are ready for retesting.

### Query

```jql
project = SDP
AND issuetype = Bug
AND status = Fixed
```

### Suggested Filter Name

```text
QA - Bugs Ready for Retest
```

This represents a realistic QA workflow where a tester can quickly find Bugs that developers have marked as Fixed.

---

# 23. Bug Reporting Structure Practiced

A good Jira Bug should contain enough information for a developer to reproduce and understand the issue.

The structure practiced was:

```text
Summary
Description
Steps to Reproduce
Expected Result
Actual Result
Environment
Priority
Labels
Assignee
Attachments
Links
Comments
Status
```

A clear Bug should make it possible for another team member to understand the problem without repeatedly asking the reporter for basic information.

---

# 24. QA Communication Practiced

Jira comments were used for different purposes.

### Development Progress

```text
Started working on login form validation.
```

### Investigation

```text
Investigating the login validation issue.
```

### Fix Handoff

```text
Ready for QA retesting.
```

### QA Retest

```text
Retest performed.

The password validation issue was checked against the
reported requirement.
```

### Blocker

```text
Blocked: waiting for the finalized login requirements.
```

### Blocker Resolution

```text
The login requirements have been finalized.
The blocker has been resolved and I can continue the test data preparation.
```

This demonstrated that Jira comments are part of professional team communication, not just notes.

---

# 25. Jira Board Behavior Learned

During practice, it was observed that completed issues can disappear from the active board depending on the board configuration.

For example:

```text
To Do → visible
In Progress → visible
Done → may disappear from active board
```

However, disappearing from the board does **not** mean the work item has been deleted.

The issue can still be found through:

- Search
- Filters
- JQL
- Issue key

For example:

```text
SDP-2
```

can still be searched after it is Done.

---

# 26. Jira vs Manual Spreadsheet Tracking

Before Jira, QA teams may use spreadsheets for simple tracking.

Jira provides additional capabilities such as:

- Issue history
- Status tracking
- Assignment
- Comments
- Attachments
- Issue links
- Priorities
- Labels
- Boards
- Dashboards
- Reports
- JQL
- Workflow tracking

For professional software teams, Jira can therefore serve as a central work-management system.

---

# 27. Production-Oriented QA Workflow Learned

The practical exercises produced the following understanding:

```text
Product Requirement
        ↓
Epic
        ↓
Story
        ↓
Tasks / Sub-tasks
        ↓
Developer Implementation
        ↓
QA Testing
        ↓
Bug Found
        ↓
Bug Created in Jira
        ↓
Developer Investigation
        ↓
Developer Fix
        ↓
Bug Status = Fixed
        ↓
QA Retest
        ↓
Pass → Done
        │
        └── Fail → Reopen / Return to Development
```

This is the main Jira workflow concept practiced throughout the learning phase.

---

# 28. Skills Completed

After completing the Jira phase, the following practical skills were covered:

- [x] Jira project creation
- [x] Jira project navigation
- [x] Kanban board usage
- [x] Backlog management
- [x] Epic creation
- [x] Story creation
- [x] Task creation
- [x] Sub-task creation
- [x] Bug creation
- [x] Assigning issues
- [x] Changing priorities
- [x] Adding labels
- [x] Adding comments
- [x] Attaching screenshots
- [x] Linking issues
- [x] Understanding blockers
- [x] Moving work through statuses
- [x] Developer-to-QA handoff
- [x] QA retest workflow
- [x] Dashboards
- [x] Dashboard gadgets
- [x] Reports
- [x] Filters
- [x] Saved filters
- [x] JQL search
- [x] Combining JQL conditions
- [x] Sorting JQL results
- [x] QA-focused JQL queries

---

# 29. Jira Phase Completion

## Status

**Completed**

The Jira learning phase has reached a practical beginner QA level.

The focus was intentionally kept on using Jira rather than memorizing advanced Jira administration or configuration concepts.

Advanced topics such as custom workflows, Jira automation, complex permissions, advanced administration, and extensive Scrum configuration can be learned later when they become necessary.

---

# 30. Next QA Learning Phase

The next recommended practical phase is:

```text
Jira
  ↓
API Testing with Postman
  ↓
SQL for QA
  ↓
Git & GitHub for QA
  ↓
Test Automation
```

The same learning approach should continue:

> **Use the tool first → perform a realistic QA task → learn the theory needed for that task → document the result.**

---

# 31. Final Summary

The Jira phase successfully moved from basic Jira navigation to practical QA project management.

The most important skills gained were:

```text
Create Work
     ↓
Organize Work
     ↓
Develop
     ↓
Report Bugs
     ↓
Track Bugs
     ↓
Communicate
     ↓
Retest
     ↓
Monitor QA Work
     ↓
Search with JQL
```

Jira is now understood as a **software development and QA collaboration tool**, not simply a bug-reporting application.

---

## Repository Suggestion

A suitable location in the QA learning repository is:

```text
03-practical-manual-testing/
└── jira/
    ├── README.md
    └── jira-for-qa-learning.md
```

Or, if keeping all daily documentation together:

```text
03-practical-manual-testing/
└── notes/
    └── jira-for-qa-learning.md
```
