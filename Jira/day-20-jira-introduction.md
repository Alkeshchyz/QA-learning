# Day 20 — Jira Introduction and Bug Tracking

## Objective

- To understand what Jira is and why it is used in software testing.
- To learn important Jira terms.
- To understand how QA engineers use Jira to report and track bugs.
- To learn the basic bug lifecycle in Jira.
- To understand the difference between Jira and Excel-based bug tracking.

---

## 1. What is Jira?

**Jira** is a project management and issue-tracking tool developed by Atlassian. It is widely used by software development and QA teams to manage tasks, bugs, and project work.

In software testing, Jira helps QA engineers report defects, communicate with developers, monitor bug status, and track fixes.

### Simple Example

Suppose a QA engineer finds that a user can continue checkout without entering a required First Name.

Instead of only writing the bug in a notebook or Excel sheet, the QA engineer can create a **Bug issue in Jira**. The development team can then view, investigate, fix, and update the issue.

---

## 2. Why is Jira Important for QA?

QA engineers use Jira to:

1. Report software defects.
2. Assign bugs to developers.
3. Track the current status of bugs.
4. Add comments and additional information.
5. Attach screenshots, videos, and logs.
6. Monitor whether a bug has been fixed.
7. Retest resolved bugs.
8. Reopen bugs if the issue still exists.
9. Maintain a history of project issues.
10. Collaborate with developers and other team members.

### Example

```text
QA finds a bug
      ↓
Bug is reported in Jira
      ↓
Developer investigates
      ↓
Developer fixes the bug
      ↓
QA retests the bug
      ↓
Bug is closed or reopened
```

---

## 3. Jira in the Software Testing Workflow

Jira is commonly used after a defect is identified during testing.

```text
Requirement
    ↓
Test Case
    ↓
Test Execution
    ↓
Bug Found
    ↓
Bug Reported in Jira
    ↓
Developer Fixes Bug
    ↓
QA Retests Bug
    ↓
Pass → Close
Fail → Reopen
```

### Explanation

- **Requirement:** Describes what the software should do.
- **Test Case:** Defines how a functionality will be tested.
- **Test Execution:** QA performs the test case.
- **Bug Found:** Actual behavior does not match the expected behavior.
- **Bug Reported:** QA creates an issue in Jira.
- **Developer Fixes:** Developer investigates and corrects the defect.
- **QA Retests:** QA checks whether the defect has been fixed.
- **Close:** The bug is confirmed as fixed.
- **Reopen:** The bug still exists and requires further work.

---

## 4. Important Jira Terms

| Term | Meaning |
|---|---|
| **Project** | A workspace where related issues are managed. |
| **Issue** | Any work item created in Jira. |
| **Bug** | A defect or unexpected behavior in software. |
| **Task** | A piece of work that needs to be completed. |
| **Story** | A user requirement or feature. |
| **Epic** | A large body of work that can be divided into smaller issues. |
| **Summary** | A short title describing the issue. |
| **Description** | Detailed information about the issue. |
| **Reporter** | The person who creates the issue. |
| **Assignee** | The person responsible for working on the issue. |
| **Priority** | Indicates how urgently the issue should be handled. |
| **Severity** | Describes how seriously the bug affects the system. |
| **Status** | The current stage of the issue. |
| **Label** | A keyword used to categorize or filter issues. |
| **Attachment** | A screenshot, video, log, or other evidence attached to an issue. |
| **Comment** | Additional discussion or information added to an issue. |
| **Workflow** | The sequence of statuses through which an issue moves. |
| **Board** | A visual display of issues organized by status. |
| **Backlog** | A list of work items that are planned or waiting to be worked on. |
| **Issue Key** | A unique identifier assigned to an issue, such as `QA-101`. |

---

## 5. Jira Issue Types

Jira supports different types of issues depending on the project.

### Bug

Used to report a defect.

**Example:**

> Checkout allows users to continue without entering the required First Name.

### Task

Used for a specific piece of work.

**Example:**

> Prepare test data for checkout testing.

### Story

Used to describe a user requirement or feature.

**Example:**

> As a customer, I want to add products to my cart.

### Epic

Used for a large feature or body of work containing smaller issues.

**Example:**

> E-commerce Checkout System.

### Important Note

For manual QA learning, the most important issue type is **Bug**.

---

## 6. Jira Bug Report Structure

A professional Jira bug should contain clear and useful information.

### Common Fields

- **Issue Type:** Bug
- **Summary:** Short and descriptive bug title
- **Description:** Detailed explanation of the defect
- **Environment:** Application, platform, browser, or device
- **Precondition:** Conditions required before testing
- **Steps to Reproduce:** Exact steps to observe the bug
- **Expected Result:** What should happen
- **Actual Result:** What actually happened
- **Severity:** Impact of the defect
- **Priority:** Urgency of fixing the defect
- **Labels:** Keywords for categorization
- **Attachments:** Screenshots, videos, or logs
- **Reporter:** Person who reported the bug
- **Assignee:** Person responsible for the issue
- **Status:** Current stage of the bug

### Example Summary

**Good:**

> Checkout allows users to continue without entering the required First Name

**Poor:**

> Checkout bug

A good summary clearly explains **what is wrong and where it happens**.

---

## 7. Severity vs Priority

Severity and priority are related, but they are not the same.

### Severity

**Severity describes how seriously a bug affects the system.**

Examples:

- **Critical:** System crash or complete system failure.
- **High:** Major functionality is affected.
- **Medium:** Important functionality has a problem, but a workaround exists.
- **Low:** Minor issue with limited impact.

### Priority

**Priority describes how urgently a bug should be fixed.**

Common priority levels:

- Highest
- High
- Medium
- Low
- Lowest

### Example

A spelling mistake on the homepage:

- **Severity:** Low
- **Priority:** High

**Reason:** The defect has little technical impact, but the homepage is visible to many users.

### Remember

```text
Severity = Impact
Priority = Urgency
```

---

## 8. Common Jira Bug Statuses

Different Jira projects may use different status names.

| Status | Meaning |
|---|---|
| **Open / New** | Bug has been reported. |
| **Assigned** | Bug has been assigned to someone. |
| **In Progress** | Developer is working on the bug. |
| **Resolved / Fixed** | Developer claims the bug has been fixed. |
| **Ready for Retest** | QA should test the fix. |
| **Closed** | QA confirms the bug is fixed. |
| **Reopened** | Bug still exists after retesting. |
| **Rejected / Won't Fix** | Team decides not to fix the issue. |
| **Duplicate** | The same bug has already been reported. |

### Important

The exact statuses depend on the Jira project and workflow configuration.

---

## 9. Basic Bug Lifecycle

A common bug lifecycle is:

```text
New
 ↓
Assigned
 ↓
In Progress
 ↓
Resolved
 ↓
Ready for Retest
 ↓
Retest
 ├── Pass → Closed
 └── Fail → Reopened
                ↓
            In Progress
```

### QA Responsibility

QA should not simply report a bug and forget about it.

A QA engineer should:

1. Find the defect.
2. Reproduce the defect.
3. Record clear steps.
4. Report the bug.
5. Monitor the status.
6. Retest after the developer fixes it.
7. Check related functionality.
8. Close the bug if fixed.
9. Reopen the bug if it still exists.

---

## 10. Jira Comments and Attachments

### Comments

Comments are used to communicate with developers and other team members.

Examples:

- Providing additional reproduction information.
- Explaining test results.
- Reporting retest results.
- Asking questions about the issue.
- Confirming whether the bug is fixed.

### Attachments

Useful attachments include:

- Screenshots
- Screen recordings
- Console errors
- Network responses
- Log files

### Example

```text
Retest Result:
The issue was retested using the original steps.
The required First Name validation is now displayed.
The bug is ready to be closed.
```

---

## 11. Jira vs Excel Bug Tracking

| Excel / Google Sheets | Jira |
|---|---|
| Simple bug list | Full issue-tracking system |
| Manual status updates | Workflow-based status tracking |
| Limited collaboration | Team collaboration |
| Basic comments | Discussion history |
| Manual assignment | Assignee management |
| Suitable for small projects | Suitable for professional teams |
| Limited issue history | Detailed issue history |

### Conclusion

Excel is useful for learning and small projects, but Jira is more suitable for professional software development teams.

---

## 12. Jira Features Important for QA

The most useful Jira features for a beginner QA engineer are:

### Create Issue

Used to create bugs, tasks, and other work items.

### Issue Details

Contains the complete information about a bug.

### Status

Shows the current stage of the issue.

### Comments

Allows communication between QA and developers.

### Attachments

Stores evidence related to the issue.

### Assignee

Shows who is responsible for the issue.

### Priority

Helps the team decide which issues need attention first.

### Labels

Help categorize and search issues.

### Search and Filters

Help QA engineers find specific bugs.

### Board

Shows issues visually according to their status.

---

## 13. Example: Sauce Demo Bug in Jira

The following example is based on the checkout validation defect identified during practical testing.

### Issue Type

Bug

### Summary

Checkout allows users to continue without entering the required First Name

### Description

The checkout form allows the user to continue even when the required First Name field is left empty. This allows incomplete customer information to proceed through the checkout process.

### Environment

Sauce Demo — Web Application / Checkout Page

### Precondition

User is logged in and has at least one product in the cart.

### Steps to Reproduce

1. Open Sauce Demo.
2. Log in with valid credentials.
3. Add any product to the cart.
4. Open the cart.
5. Click Checkout.
6. Leave the First Name field empty.
7. Enter a valid Last Name.
8. Enter a valid Postal Code.
9. Click Continue.

### Expected Result

The application should prevent the user from continuing and display a validation message indicating that First Name is required.

### Actual Result

The application allows the user to continue without entering First Name.

### Severity

High

### Priority

High

### Labels

`checkout`, `validation`, `saucedemo`

### Status

New

---

## 14. Practical Learning Plan

During this Jira learning phase, the following practical exercises will be completed:

1. Create a Jira Cloud account.
2. Create a QA Learning project.
3. Explore the Jira dashboard and board.
4. Create the first bug using the Sauce Demo checkout defect.
5. Add a description, priority, and labels.
6. Attach a screenshot as evidence.
7. Assign the issue.
8. Change the issue status.
9. Add comments.
10. Simulate a developer fix.
11. Retest the bug.
12. Close the bug if fixed.
13. Reopen the bug if it still exists.
14. Create a second independent bug.
15. Search and filter issues using Jira.

---

## 15. Key Takeaways

- Jira is an issue-tracking and project management tool.
- QA engineers use Jira to report and track bugs.
- A Jira issue can be a bug, task, story, or other work item.
- A good bug report must contain clear reproduction steps.
- Severity describes impact, while priority describes urgency.
- Jira statuses show the current stage of a bug.
- QA engineers must retest fixed bugs.
- A bug should be closed only after confirming that it is fixed.
- If the bug still exists, it should be reopened.
- Jira improves communication and collaboration between QA and developers.

---


```