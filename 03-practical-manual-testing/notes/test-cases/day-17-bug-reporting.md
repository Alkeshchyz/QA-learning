# Day 17 — Bug Reporting 

## Overview

Day 17 focuses on **Bug Reporting**.

As a QA tester, finding a defect is only part of the job. A tester must also communicate the defect clearly so that developers can understand, reproduce, investigate, and fix it.

The goal of this day is to learn how to create a professional and developer-friendly bug report.

---

## Learning Objectives

By the end of Day 17, I learned:

- What a bug/defect is
- What a bug report is
- Bug reporting workflow
- Bug report structure
- How to write a good bug title
- How to write reproduction steps
- Expected Result vs Actual Result
- Severity vs Priority
- Common severity levels
- Bug status and lifecycle
- How to determine whether a failed test is actually a bug

---

## 1. What Is a Bug?

A **bug/defect** is a problem in the software where the actual behavior differs from the expected behavior or the software does not meet a specified requirement.

**Example**

- **Expected Result:** User should be redirected to the Login page after logout.
- **Actual Result:** User remains on the Dashboard after clicking Logout.

The difference between the expected and actual behavior indicates a potential bug.

---

## 2. Failed Test vs Bug

An important QA lesson is:

> A failed test does not automatically mean there is a bug.

A failure can happen because:

- The test case was incorrectly designed.
- The requirement was misunderstood.
- The test data was incorrect.
- The environment has a problem.
- The application actually contains a defect.

Therefore, a QA tester should investigate the failure before reporting it as a bug.

---

## 3. Bug Reporting Workflow

A typical bug workflow is:

```
Execute Test Case
       ↓
      FAIL
       ↓
Investigate
       ↓
Confirm / Reproduce
       ↓
Create Bug Report
       ↓
Developer Fix
       ↓
Retest
       ↓
PASS / FAIL
       ↓
Regression Testing
```

---

## 4. Bug Report Structure

A professional bug report can contain the following fields:

| Field | Description |
|---|---|
| Bug ID | Unique identifier for the bug |
| Title | Short and clear description of the issue |
| Environment | Application/environment where the issue occurred |
| Precondition | Required state before reproducing the bug |
| Steps to Reproduce | Exact steps required to reproduce the issue |
| Test Data | Data used during testing |
| Expected Result | What should happen |
| Actual Result | What actually happened |
| Severity | Impact of the bug |
| Priority | Urgency of fixing the bug |
| Status | Current state of the bug |
| Evidence | Screenshot, video, logs, etc. |

---

## 5. Bug ID

Every bug should have a unique identifier.

```
BUG_ID_001
BUG_ID_002
BUG_ID_003
```

The ID makes it easier to track and reference the issue.

---

## 6. Bug Title

A good bug title should be:

- Short
- Specific
- Clear
- Descriptive

**❌ Poor Title**

> Login not working

This is too vague.

**❌ Poor Title**

> There is a very serious problem when I try to login with correct credentials

This is unnecessarily long.

**✅ Better Title**

> Login fails with valid credentials and displays "Invalid username or password"

A developer should be able to understand the main problem from the title.

---

## 7. Steps to Reproduce

Steps to Reproduce describe exactly how to reproduce the issue.

**Example**

1. Open the application.
2. Navigate to the Login page.
3. Enter a valid username.
4. Enter a valid password.
5. Click the Login button.

The steps should be clear enough that another tester or developer can follow them without guessing.

---

## 8. Expected Result

The Expected Result describes what the application should do.

> Example: User should be able to log in successfully and be redirected to the Dashboard.

---

## 9. Actual Result

The Actual Result describes what the application actually did during execution.

> Example: User was unable to log in, and the application displayed "Invalid username or password."

---

## 10. Expected vs Actual

This is one of the most important parts of bug reporting.

- **Expected:** User should be logged in and redirected to the Dashboard.
- **Actual:** User remained on the Login page and received an error message.

The difference between these two results helps identify the defect.

---

## 11. Severity

Severity describes how seriously the bug affects the application or its functionality.

For practice, the following levels are used:

- **Critical** — the application or a critical function is unusable.
- **High** — a major functionality is broken and has significant impact.
- **Medium** — important functionality is affected, but a workaround may exist.
- **Low** — the issue has limited impact.

---

## 12. Priority

Priority describes how urgently the bug should be fixed.

For example, a login problem may have Severity: High and Priority: High, because login is a core functionality and users may not be able to access authenticated services.

---

## 13. Severity vs Priority

These two concepts are commonly confused.

> Severity = Impact
> Priority = Urgency

Severity asks: *"How badly does this bug affect the system?"*

Priority asks: *"How urgently should this bug be fixed?"*

---

## 14. Bug Status

A bug can move through different states during its lifecycle.

A simplified workflow is:

```
New
  ↓
Assigned
  ↓
In Progress
  ↓
Fixed
  ↓
Ready for Retest
  ↓
Retest
  ↓
Closed
```

If the issue still exists after the developer's fix:

```
Ready for Retest
       ↓
      FAIL
       ↓
     Reopen
```

---

## 15. Practical Bug Report Exercise

**Scenario**

> Requirement: A user with valid credentials should be successfully logged in and redirected to the Dashboard.

Test Data: Username: `alkesh`, Password: `correct_password`

After clicking Login, the application displays "Invalid username or password." The user remains on the Login page.

**Bug Report**

| Field | Value |
|---|---|
| Bug ID | BUG_ID_001 |
| Title | Login fails with valid credentials and displays "Invalid username or password" |
| Environment | Sauce Demo — Web application / Login page |
| Precondition | User is on the Login page. |
| Steps to Reproduce | 1. Open the application. 2. Enter valid username. 3. Enter valid password. 4. Click the Login button. |
| Test Data | Username: [valid test username], Password: [valid test password] |
| Expected Result | User should be able to log in successfully and be redirected to the Dashboard. |
| Actual Result | User was unable to log in, and the application displayed "Invalid username or password." |
| Severity | High |
| Priority | High |
| Status | New |

---

## 16. Severity and Priority Reasoning

**Severity: High**
Reason: Without being able to log in, users cannot access services or features that require authentication.

**Priority: High**
Reason: Login is a core functionality, so the issue should be fixed quickly.

---

## 17. Important QA Lessons

**Lesson 1 — Don't manufacture bugs**

A QA tester should report what actually happens.

```
Expected ≠ Actual
        ↓
   Investigate
        ↓
  Confirm defect
```

Do not intentionally mark a test as FAIL just to create a bug report.

**Lesson 2 — Compare Expected and Actual**

Never assume: *"Error message = FAIL."*

Instead ask: *"Does the actual behavior match the expected behavior?"*

If yes → PASS. If no → FAIL.

**Lesson 3 — Test cases must match the application**

During practical testing, an earlier login test case expected an email-format validation. However, Sauce Demo uses a username field rather than an email field. The application returned:

> Epic sadface: Username and password do not match any user in this service

This taught an important lesson:

> A test case must be based on the application's actual requirements and behavior.

A poorly designed test case should not automatically result in a bug report.

**Lesson 4 — Keep the bug report consistent**

These fields should describe the same situation:

```
Title
  ↓
Steps
  ↓
Test Data
  ↓
Expected Result
  ↓
Actual Result
```

For example, the title should not say that login succeeds if the Actual Result says login fails.

---

## 18. Bug Report Template

Use this template for future bugs:

```
Bug ID:

Title:

Environment:

Precondition:

Steps to Reproduce:
1.
2.
3.
4.

Test Data:

Expected Result:

Actual Result:

Severity:

Priority:

Status:
```

---

## 19. Day 17 Summary

Today I learned how to turn a testing failure into a clear and professional bug report.

The most important concepts learned were:

- Bug/defect
- Bug report
- Bug ID
- Bug title
- Environment
- Preconditions
- Steps to Reproduce
- Test Data
- Expected Result
- Actual Result
- Severity
- Priority
- Bug Status
- Bug lifecycle
- Severity vs Priority
- Failed test vs actual defect

**QA Workflow Learned**

```
Requirement
    ↓
Test Case
    ↓
Test Execution
    ↓
PASS / FAIL
    ↓
Investigate
    ↓
Bug Report
    ↓
Developer Fix
    ↓
Retest
    ↓
Regression
    ↓
Close
```

**Day 17 Status:** Completed ✅

---

*End of Day 17 guide*