# Day 6 — Types of Software Testing

Today we're covering the main testing types from the roadmap you uploaded. The roadmap specifically puts these before test-design techniques: functional vs non-functional, smoke, sanity, regression, retesting, exploratory, ad-hoc, and UAT, followed by black-box/white-box/grey-box testing.

The goal today is not to memorize definitions. We want you to understand when a tester would use each one.

---

## 1. Functional Testing

### What Is It?

Functional testing checks whether the software's features and functions behave according to requirements.

> Simple question: "Does the feature work correctly?"

**Example — Login**

Requirement: *A registered user should be able to log in with valid credentials.*

You test:

- Email: `user@gmail.com`
- Password: `correct123`

Expected: user successfully logs in. That's functional testing.

Other examples:

- Add product to cart
- Submit registration form
- Reset password
- Place an order
- Cancel an order

---

## 2. Non-Functional Testing

Non-functional testing focuses on how well the software works, rather than simply whether the feature works. Examples include:

- Performance
- Security
- Usability
- Compatibility
- Reliability

**Example**

Your login feature works correctly. But login takes 20 seconds. Functionally, login works — but the performance is poor. That's where non-functional testing becomes important.

**Easy memory**

> Functional = What does it do?
> Non-functional = How well does it do it?

---

## 3. Smoke Testing

Smoke testing is a quick, broad check to determine whether a build is stable enough for more detailed testing.

Imagine developers give you Version 2.1. Before spending several hours testing it, you check the most important functionality:

| Check | Result |
|---|---|
| Application opens? | ✅ |
| Login works? | ✅ |
| Dashboard loads? | ✅ |
| Product search works? | ✅ |
| Checkout opens? | ❌ |

If a critical feature is broken, you may stop detailed testing and send the build back.

> Think: "Is this build stable enough to test further?"

---

## 4. Sanity Testing

Sanity testing is a focused check of a particular area after changes or fixes.

Imagine a developer fixes: *"Checkout button doesn't work."*

You receive the new build. Instead of immediately running the entire test suite, you first check:

```
Checkout button
  ↓
Checkout page
  ↓
Payment
```

If the fix works and the related area looks reasonable, you can continue with broader testing.

> Think: "Did this specific change/fix work properly?"

---

## 5. Smoke vs Sanity

This is a common interview question.

| Smoke | Sanity |
|---|---|
| Broad and shallow | Narrow and focused |
| Checks overall build stability | Checks a specific change/fix |
| Usually covers critical functionality | Focuses on affected functionality |
| "Can we test this build?" | "Does this particular change look correct?" |

**Memory trick**

> Smoke → Build
> Sanity → Specific change

---

## 6. Retesting

Retesting means testing a specific defect again after the developer claims it has been fixed.

**Example**

You reported: `BUG-001 — Login accepts incorrect password`

Developer fixes it. You test the exact scenario again:

```
Wrong password
  ↓
Login
  ↓
Expected: Error
Actual: Error
```

The bug passes retesting.

> Think: "Was the bug actually fixed?"

---

## 7. Regression Testing

Regression testing checks whether existing functionality has been negatively affected by new changes. This is different from retesting.

Suppose a developer fixes the login system. You don't only check the original login bug — you may also check:

```
Login
  ↓
Logout
  ↓
Password reset
  ↓
Profile
  ↓
Cart
  ↓
Checkout
```

Why? Because changing one part of the application can accidentally break another part.

> Think: "Did the new change break something that was already working?"

---

## Retesting vs Regression

This is very important.

**Retesting** — focus: the specific defect

```
Bug
  ↓
Fix
  ↓
Test the same bug again
```

**Regression** — focus: existing functionality potentially affected by the change

```
Change
  ↓
Test related/existing functionality
  ↓
Make sure nothing else broke
```

**Easy memory**

> Retesting = Test the fix
> Regression = Test for side effects

---

## 8. Exploratory Testing

Exploratory testing means learning, designing tests, and executing tests at the same time, rather than strictly following predefined test cases.

**Example**

You're testing a registration page. You start with normal registration, then start exploring:

- Empty fields
- Very long name
- Special characters
- Copy/paste
- Multiple clicks
- Back button
- Refresh
- Different browsers

You're using your knowledge and observations to discover problems.

> Think: "Explore the application and learn while testing."

This can be particularly useful when requirements are incomplete or time is limited.

---

## 9. Ad-Hoc Testing

Ad-hoc testing is informal testing without a predefined structured test plan or test cases. The tester uses experience and intuition to try to find defects.

**Example**

You are testing a login page and think: *"What happens if I click the Login button 20 times quickly?"* You try it. That's an ad-hoc test.

**Exploratory vs Ad-Hoc**

They can look similar, but conceptually:

- Exploratory testing is a more purposeful testing approach where learning, test design, and execution happen together.
- Ad-hoc testing is more informal and spontaneous.

---

## 10. User Acceptance Testing (UAT)

We touched this during Day 5.

UAT = User Acceptance Testing. The purpose is to determine whether the software satisfies business/user needs and is acceptable for use.

**Example**

An e-commerce company has a requirement: *Customers must be able to return products within 7 days.*

Business representatives test the complete process:

```
Purchase
  ↓
Delivery
  ↓
Return request
  ↓
Return approval
  ↓
Refund
```

They verify that the system meets the business expectation.

> Think: "Is this product acceptable for the real business/user?"

---

## 11. Black-Box Testing

Black-box testing means testing software without needing to know its internal implementation/code. You focus on:

```
Input
  ↓
Software
  ↓
Output
```

**Example**

You test a login page. You don't need to know how the developer implemented authentication. You provide a username and password, and check expected result vs actual result.

Most manual functional testing you'll perform as a beginner QA fits naturally into this way of thinking.

---

## 12. White-Box Testing

White-box testing involves knowledge of the internal code, logic, or structure of the software.

**Example**

A developer tests:

```python
if age >= 18:
    allow()
else:
    reject()
```

They may create tests specifically around the internal branches and conditions.

White-box testing is commonly associated with developers or testers with programming knowledge.

---

## 13. Grey-Box Testing

Grey-box testing is somewhere between black-box and white-box testing. The tester has some knowledge of the internal system, but doesn't necessarily test by examining every line of code.

For example, a QA tester may know:

```
Frontend
  ↓
REST API
  ↓
Database
```

They can use that knowledge to create better tests while still primarily testing the application from the outside.

---

## The Big Picture

Don't memorize all these as one giant list. Organize them mentally:

```
TESTING TYPES
│
├── Functional
│
├── Non-functional
│
├── Build/change focused
│   ├── Smoke
│   ├── Sanity
│   ├── Retesting
│   └── Regression
│
├── Experience-based
│   ├── Exploratory
│   └── Ad-hoc
│
├── Acceptance
│   └── UAT
│
└── Knowledge of internals
    ├── Black-box
    ├── White-box
    └── Grey-box
```

---

## One Scenario — Multiple Testing Types

Imagine you're testing an online shopping application.

| Type | Question |
|---|---|
| Functional | Can I add a product to the cart? |
| Non-functional | Does the cart load within an acceptable time? |
| Smoke | Does the new build open, login, search and checkout? |
| Sanity | Did the newly fixed checkout button work? |
| Retesting | Does the specific checkout bug now pass? |
| Regression | Did fixing checkout break payment, cart, or order history? |
| Exploratory | Explore checkout and try unusual inputs/actions. |
| Ad-hoc | Randomly try clicking checkout multiple times quickly. |
| UAT | Does the business accept the complete purchasing process? |
| Black-box | Test the application without knowing its internal code. |
| White-box | Test internal code branches/logic. |
| Grey-box | Use some knowledge of APIs/database architecture to improve testing. |

---

*End of Day 6 guide*