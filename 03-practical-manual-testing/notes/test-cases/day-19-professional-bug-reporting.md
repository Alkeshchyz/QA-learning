# Day 19 — Professional Bug Reporting

## Overview

On Day 19 I learned how to write bug reports that a development team can actually act on.

Finding the bug is only half the job. You still have to explain what went wrong clearly enough that someone else — who wasn't standing next to you when it happened — can understand it, reproduce it, and fix it without pinging you five times to ask what you meant. That means being able to say what went wrong, where it happened, how to reproduce it, what you expected versus what you actually got, and how serious and urgent the issue really is.

A good bug report does the explaining for you. If it's written well, a developer can pick it up, reproduce the problem, and start fixing it — no back-and-forth required.

---

## Learning Objectives

By the end of Day 19, I learned:

- What makes a good bug report
- How to write a clear bug title
- How to write reproducible steps
- How to write expected and actual results
- How to select severity
- How to select priority
- The difference between severity and priority
- What information developers actually need from QA
- Common mistakes people make in bug reports
- How to write a professional bug report
- How a bug moves from QA to development and back to QA

---

## 1. What Is a Bug Report?

A **bug report** is how QA communicates a defect to the rest of the team. The bar for a good one is simple: another person should be able to read it, understand the problem, and reproduce it — without needing you to explain it out loud.

A basic bug report usually contains:

```
Bug ID
Title
Environment
Precondition
Steps to Reproduce
Test Data
Expected Result
Actual Result
Severity
Priority
Status
Attachments
```

---

## 2. Why Bug Reporting Actually Matters

A sloppy bug report costs everyone time. It leads to confusion, back-and-forth questions, developers who can't reproduce the issue, fixes aimed at the wrong problem, and general wasted effort on both sides.

A well-written one avoids all of that — the developer reads it once and knows exactly what to do.

> QA goal: make the bug easy to understand and easy to reproduce.

---

## 3. Bug Report Structure

### 3.1 Bug ID

A unique identifier assigned to the defect, e.g. `BUG_CART_001`. It's what lets the team track and reference the issue later without confusion.

### 3.2 Bug Title

The title should communicate three things at a glance: *what* happened, *where*, and any condition that matters.

A title like **"Cart is not working"** doesn't really tell anyone anything. Compare that with **"Cart allows checkout without required customer information"** — the second one already tells the developer roughly where to look and what's broken.

A good title tends to be short, specific, clear, and descriptive. Titles like "Error," "Problem," "Not working," "Bug in cart," or "Something wrong" aren't titles so much as placeholders — avoid them.

---

## 4. Environment

The environment is where the bug was found — the application, browser, OS, device, and version, whatever's relevant to the project. For example:

```
Application: Sauce Demo
Platform: Web
Browser: Chrome
Operating System: Windows
```

---

## 5. Preconditions

A precondition is whatever needs to be true *before* someone follows your reproduction steps — for example, that the user is logged in, the product exists, or it's already in the cart. Skip this and another tester may not even get to the point where the bug shows up.

---

## 6. Steps to Reproduce

Steps should be numbered, clear, and in the exact order they happened. For example:

1. Open the application.
2. Log in with valid credentials.
3. Add a product to the cart.
4. Open the cart.
5. Click Checkout.
6. Leave First Name empty.
7. Enter Last Name and Postal Code.
8. Click Continue.

Compare that to something like "Login and go to cart and checkout and try to continue" — technically it describes the same actions, but nobody can actually follow it step by step.

---

## 7. Test Data

Test data is whatever values you used while testing:

```
Username: test_user
Password: ********
Product: Sauce Labs Backpack
First Name: Alkesh
Last Name: Tester
Postal Code: 44600
```

One important rule here: never put real passwords, API keys, tokens, or anything sensitive into a bug report. Use safe test credentials or placeholders instead.

---

## 8. Expected Result

This is what *should* happen, based on the requirement or the app's intended behavior — not on a guess. For example:

> The user should not be allowed to continue checkout when the required First Name field is empty.

Base this on requirements, acceptance criteria, or business rules — not on what you personally assumed the app would do.

---

## 9. Actual Result

This is what actually happened when you tested it:

> The application allowed the user to continue checkout without entering a First Name.

Describe what you observed. Don't exaggerate it, and don't speculate about what's causing it — that's for the developer to dig into.

---

## 10. Severity

Severity is really just: *how badly does this bug hurt the system?* A rough scale:

- **Critical** — a major system failure or a critical function is unusable (e.g. the app crashes right after launch).
- **High** — an important/core function is broken (e.g. users can't log in with valid credentials).
- **Medium** — something's broken, but there's a workaround or the impact is limited (e.g. a search filter misbehaves, but users can still browse manually).
- **Low** — minor impact (e.g. a button's text is slightly misaligned).

---

## 11. Priority

Priority is a different question: *how urgently does this need to get fixed?*

- **High** — fix it ASAP (e.g. login is broken right before a major release).
- **Medium** — should be fixed, but it's not on fire (e.g. a non-critical filter behaving oddly).
- **Low** — can wait (e.g. a minor UI alignment issue).

---

## 12. Severity vs Priority

People mix these up constantly.

| Severity | Priority |
|---|---|
| Impact of the bug | Urgency of fixing the bug |
| How badly the system is affected | How quickly it should be fixed |
| Mainly a technical/functional question | Mainly a business/release-timing question |

> Severity = how *bad* is it? Priority = how *soon* do we fix it?

---

## 13. Severity and Priority Don't Always Match

They can move independently of each other, and it's worth seeing a few examples of that:

**High severity + high priority** — users can't log in at all. The impact is serious and it needs fixing now.

**Low severity + high priority** — the company logo is wrong on the homepage right before a big marketing campaign launches. Technically, that's a low-severity cosmetic issue. But given the timing, it's high priority.

**High severity + low priority** — a serious bug in a feature that's barely used and already scheduled for removal. Severe on paper, but not worth rushing a fix for.

The right classification always depends on the project and the business context around it.

---

## 14. Attachments

Screenshots, screen recordings, console logs, error logs, network traces — anything that helps someone see what you saw. A screenshot is usually enough for a UI bug; a screen recording earns its keep when the bug only shows up after a specific sequence of actions.

---

## 15. What Makes a Bug Report Developer-Friendly

A developer should be able to read your report and immediately answer: what's broken, where, how to reproduce it, what should happen, what actually happens, how serious it is, and how urgent it is. If your report answers all of that without anyone needing to ask a follow-up question, it's doing its job.

---

## 16. Common Bug Reporting Mistakes

**A vague title.** "Login problem" tells you nothing. "Login fails when valid credentials are entered" tells you exactly what to look into.

**Missing steps.** "Login doesn't work" leaves the developer guessing. Spell it out: open the login page, enter a valid username, enter a valid password, click Login.

**A fuzzy expected result.** "Login should work" isn't a testable statement. "User should be authenticated and redirected to the Dashboard" is.

**Blending expected and actual results together.** Keep them clearly separate:

- Expected: user should be redirected to Dashboard.
- Actual: user remains on Login page and an error message is displayed.

**Defaulting every bug to High/High.** Not every bug is critical and urgent — think about the actual impact and timing before you pick severity and priority.

**Reporting an assumption as a bug.** This was the big lesson from Day 18: unexpected behavior needs investigating before it becomes a bug report.

```
Unexpected behavior
        ↓
Check requirement
        ↓
Reproduce
        ↓
Investigate
        ↓
Confirm defect
        ↓
Create bug report
```

---

## 17. Bug Reporting Workflow

Here's roughly how it flows in a real team:

```
Execute Test Case
       ↓
Unexpected Result
       ↓
Reproduce
       ↓
Check Requirement
       ↓
Confirm Bug
       ↓
Create Bug Report
       ↓
Developer Reviews
       ↓
Bug Assigned
       ↓
Developer Fixes
       ↓
Ready for Retest
       ↓
QA Retests
       ↓
 ┌───────────────┐
 │               │
PASS            FAIL
 │               │
 ↓               ↓
Closed        Reopened
```

---

## 18. Practical Bug Report Example

**Bug Report — Login**

| Field | Value |
|---|---|
| Bug ID | BUG_LOGIN_001 |
| Test ID | TC_LOGIN_001 |
| Title | Login fails with valid credentials |
| Environment | Application: Sauce Demo · Platform: Web · Browser: Chrome · OS: Windows |
| Precondition | User is on the Login page. |
| Steps to Reproduce | 1. Open Sauce Demo. 2. Navigate to the Login page. 3. Enter a valid username. 4. Enter the correct password. 5. Click Login. |
| Test Data | Username: `<valid test username>`, Password: `<valid test password>` |
| Expected Result | User should successfully log in and be redirected to the Products page. |
| Actual Result | User is unable to log in and an error message is displayed. |
| Severity | High |
| Priority | High |
| Status | New |

**Reasoning:** Login is core functionality — if valid users can't get in, they can't reach anything the app protects. That's significant impact, so it warrants a quick look.

---

## 19. Bug Report Quality Checklist

Before submitting a bug, check that you have:

- [ ] Unique Bug ID
- [ ] Clear title
- [ ] Correct environment
- [ ] Clear precondition
- [ ] Numbered reproduction steps
- [ ] Test data included
- [ ] Expected result included
- [ ] Actual result included
- [ ] Severity selected correctly
- [ ] Priority selected correctly
- [ ] Status included
- [ ] Evidence attached when useful
- [ ] No sensitive credentials included
- [ ] Bug reproduced
- [ ] Requirement checked

---

## 20. Day 19 Practical Exercise

For today's exercise, I need to write a professional bug report for a defect found during testing.

**Scenario**

The application has this requirement:

> A user must enter First Name, Last Name, and Postal Code before continuing checkout.

While testing, I did the following:

1. Log in.
2. Add a product to the cart.
3. Open the cart.
4. Click Checkout.
5. Leave First Name empty.
6. Enter Last Name.
7. Enter Postal Code.
8. Click Continue.

**What I observed:** the application let me continue checkout even though First Name was empty — a direct violation of the requirement.

**My task:** write the full bug report myself (Bug ID, Test ID, Title, Environment, Precondition, Steps to Reproduce, Test Data, Expected Result, Actual Result, Severity, Priority, Status) using this scenario, without copying the Login example above. The point is to actually practice writing one from scratch.

---

## Day 19 Key Takeaways

1. A bug report communicates a defect clearly to the development team.
2. A good bug title is specific and descriptive.
3. Reproduction steps need to be clear and repeatable.
4. Expected and actual results should always be kept separate.
5. Severity describes impact.
6. Priority describes urgency.
7. Severity and priority don't always agree with each other.
8. Check the requirement before reporting a defect as a bug.
9. Evidence (screenshots, recordings, logs) makes reports easier to act on.
10. A good bug report lets someone else reproduce the issue without needing extra explanation.

---

## Day 19 Summary

Day 19 was about professional bug reporting — turning a confirmed defect into something a developer can actually pick up and act on, and understanding how severity and priority get decided along the way.

The goal was never just to say "there's a bug." It's to clearly lay out what happened, where, how to reproduce it, what should have happened instead, what actually happened, and how important it is to fix.

---

## Day 19 Status

**In Progress**

Topics covered:

- Bug Report Structure
- Bug ID
- Bug Title
- Environment
- Preconditions
- Steps to Reproduce
- Test Data
- Expected Result
- Actual Result
- Severity
- Priority
- Severity vs Priority
- Attachments
- Common Bug Reporting Mistakes
- Developer-Friendly Bug Reports
- Bug Reporting Workflow
- Practical Bug Report Exercise

Day 19 gets marked DONE once the practical exercise is actually finished.

---

### How We'll Do Day 19

Don't just save the document and call it done yet. **Do the exercise at the bottom yourself.**

Write the bug report for the checkout scenario and send it over. I'll review it like a QA lead reviewing your bug report, flag anything that needs fixing, and then we'll officially mark **Day 19 DONE**.

---

*End of Day 19 guide*