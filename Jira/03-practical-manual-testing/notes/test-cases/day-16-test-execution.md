# Day 16 — Test Execution

## Overview

Day 16 moved from writing test cases to executing them against a real application. The practice application was [Sauce Demo](https://www.saucedemo.com/), a public demo site for software-testing practice. Only the demo credentials shown by the site were used; no personal credentials were required.

## Learning Objectives

By the end of this session, the learner was able to:

- execute prepared test cases on an application;
- record an objective Actual Result;
- compare Expected and Actual Results;
- assign a test status: PASS, FAIL, or BLOCKED;
- distinguish retesting from regression testing;
- recognise when a test case or requirement needs clarification; and
- understand how a legitimate failed test can lead to a bug report.

## Test Execution Concepts

### What is test execution?

Test execution is the process of performing the steps in a prepared test case on an application, observing its behaviour, and comparing that behaviour with the expected result.

### Execution workflow

```text
Test Case
   ↓
Execute Steps
   ↓
Observe Actual Result
   ↓
Compare with Expected Result
   ↓
PASS / FAIL / BLOCKED
```

The Actual Result must describe what happened during execution. The Expected Result must not be changed after observing the application.

### Test statuses

| Status | Meaning |
|---|---|
| PASS | The Actual Result matches the Expected Result. |
| FAIL | The Actual Result does not match the Expected Result. |
| BLOCKED | The test cannot be executed because something prevents it, such as an unavailable server or missing access. |

An error message does not automatically mean a test has failed. For example, an invalid-login test passes when the application correctly prevents login and shows the expected error message.

### Expected Result vs Actual Result

| Field | Description |
|---|---|
| Expected Result | What the system should do, based on the requirement or approved test case. |
| Actual Result | What the system actually did during execution. |

Example:

```text
Expected: User should be redirected to the Login page.
Actual:   User remained on the Dashboard.
Status:   FAIL
```

### Retesting vs regression testing

**Retesting** means executing the same previously failed test case again after a developer reports that the issue has been fixed.

```text
FAIL → Developer fix → Retest → PASS
```

**Regression testing** means checking related or existing functionality to confirm that a change did not break something else. For example, after a logout fix, related authentication areas such as login, logout, profile, password change, and dashboard access may be checked.

## Practical Test Execution — Sauce Demo

### Test summary

| Test Case ID | Scenario | Final result |
|---|---|---|
| TC_LOGOUT_01 | Log out of the application | PASS |
| TC_LOGIN_006 | Log in with an invalid username (revised) | PASS |
| TC_CART_001 | Add a product to the cart | PASS |
| TC_CART_002 | Add the same product to the cart multiple times | Requirement needs clarification |
| TC_CART_003 | Remove a product from the cart | PASS |
| TC_CART_004 | Keep a product in the cart after navigating away and returning | PASS |
| TC_CHECKOUT_001 | Prevent checkout when First Name is missing | PASS |

> No confirmed application defect was recorded during this session.

### TC_LOGOUT_01 — Logout

**Scenario:** A user should be able to log out of the application.

**Precondition:** User is logged in and on the Dashboard.

**Steps:**

1. Log in with valid credentials.
2. Navigate to the Dashboard.
3. Click Logout.
4. Click Confirm if a confirmation dialog appears.

**Expected Result:** User should be logged out successfully and redirected to the Login page.

**Actual Result:** User was able to log out successfully and was redirected to the Login page.

**Status:** PASS

### TC_LOGIN_006 — Invalid username (revised)

The original version of this test attempted to validate an incorrectly formatted email address. During review, it was identified that Sauce Demo uses a **Username** field, not an email field. Therefore, an email-format validation expectation did not match the application UI and the case was revised.

**Scenario:** Verify login with an invalid username.

**Precondition:** User is on the Login page.

**Test Data:**

```text
Username: invalid_user
Password: [demo password]
```

**Steps:**

1. Enter an invalid username.
2. Enter the password.
3. Click Login.

**Expected Result:** User should not be logged in and an appropriate error message should be displayed.

**Actual Result:** User was not able to log in, and the application displayed: `Epic sadface: Username and password do not match any user in this service.`

**Status:** PASS

### TC_CART_001 — Add product to cart

**Scenario:** Verify that a user can add a product to the cart.

**Precondition:** User is logged in and on the Products page.

**Steps:**

1. Select any product.
2. Click **Add to cart**.
3. Open the shopping cart.

**Expected Result:** The selected product should be added to the cart and displayed in the cart.

**Actual Result:** The selected product was added to the cart and displayed in the cart.

**Status:** PASS

### TC_CART_002 — Add the same product multiple times

**Scenario:** Verify that a product can be added to the cart multiple times.

**Precondition:** User is logged in and on the Products page.

**Steps:**

1. Select a product.
2. Click **Add to cart**.
3. Click **Add to cart** for the same product again.
4. Open the shopping cart.

**Expected Result in the original case:** The product quantity should increase to 2, **or** the application should prevent the same product from being added twice, according to the intended behaviour.

**Observed behaviour:** The product was added to the cart and its quantity increased to 2.

**Status:** Requirement needs clarification.

#### Requirement ambiguity lesson

The expected result allowed two different outcomes: increasing the quantity to 2 or preventing a duplicate addition. These outcomes cannot both be the single expected behaviour for one requirement.

The observation can be recorded, but the test cannot be conclusively classified as PASS or FAIL until the product requirement specifies which behaviour is intended. A clear, requirement-based expected result is essential for reliable testing.

### TC_CART_003 — Remove product from cart

**Scenario:** Verify that a product can be removed from the cart.

**Precondition:** User is logged in.

**Steps:**

1. Add any product to the cart.
2. Open the cart.
3. Click **Remove** for that product.

**Expected Result:** The selected product should be removed from the cart.

**Actual Result:** The selected product was successfully removed from the cart.

**Status:** PASS

### TC_CART_004 — Cart persistence

**Scenario:** Verify that a selected product remains in the cart after navigating away from the Cart page and returning.

**Precondition:** User is logged in.

**Steps:**

1. Add any product to the cart.
2. Open the Cart.
3. Navigate back to the Products page.
4. Open the Cart again.

**Expected Result:** The previously added product should still be displayed in the cart.

**Actual Result:** The previously added product was still displayed in the cart.

**Status:** PASS

### TC_CHECKOUT_001 — Required First Name validation

**Scenario:** Verify checkout cannot proceed when required customer information is missing.

**Precondition:** User is logged in and has a product in the cart.

**Steps:**

1. Open the Cart.
2. Click Checkout.
3. Leave the First Name field empty.
4. Enter Last Name and Postal Code.
5. Click Continue.

**Expected Result:** The user should not be allowed to continue, and an appropriate validation message should be displayed for the missing First Name.

**Actual Result:** User was unable to continue, and an appropriate validation message was displayed for the missing First Name.

**Status:** PASS

## QA Lessons Learned

1. Record what is observed; do not manufacture a bug just to produce a failure.
2. A PASS is a useful testing outcome when Actual and Expected Results match.
3. An error message can be expected behaviour, so it can result in PASS.
4. Test cases must match the application’s actual UI and requirements. The original email-format version of `TC_LOGIN_006` was unsuitable because Sauce Demo accepts usernames rather than email addresses.
5. Expected results must be specific. Ambiguous expectations, as in `TC_CART_002`, need requirement clarification before a definitive status can be assigned.
6. A FAIL is evidence of a mismatch between expected and actual behaviour; it can then be investigated and, when valid, documented in a bug report.
7. Clear, reproducible steps and precise observations make test execution useful to other testers, developers, and stakeholders.

## Day 16 Outcome

Seven test cases were executed on Sauce Demo. Six were recorded as PASS. One case (`TC_CART_002`) surfaced a test-design and requirement-clarity issue rather than a confirmed product defect. The session established the core manual QA execution cycle and prepared the next topic: professional bug reporting.
