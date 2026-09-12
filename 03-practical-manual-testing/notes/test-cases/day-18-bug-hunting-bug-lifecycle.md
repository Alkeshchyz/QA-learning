# Day 18 — Bug Hunting + Bug Lifecycle

## Overview

On Day 18, I learned how to actively hunt for bugs instead of only executing predefined test cases.

The main focus was understanding how to:

- Find unexpected behavior
- Compare actual results with expected results
- Confirm whether an unexpected behavior is really a bug
- Understand the bug lifecycle
- Understand retesting and regression testing
- Avoid reporting intentional application behavior as a bug

---

## Learning Objectives

By the end of Day 18, I learned:

- What bug hunting means
- How to approach an application with a bug-hunting mindset
- The basic bug lifecycle
- The difference between a failed test and a confirmed bug
- What retesting means
- What regression testing means
- How to investigate suspicious behavior before reporting it
- How to document the results of practical testing

---

## 1. What Is Bug Hunting?

**Bug hunting** is the process of systematically testing an application to find behavior that does not match the expected result or requirement.

Instead of only asking:

> "Does this feature work?"

A QA tester should also ask:

> "How can I make this feature behave incorrectly?"

This mindset helps testers discover unexpected problems and edge cases.

---

## 2. Bug Hunting Mindset

When testing an application, I should think about:

- What happens with unexpected input?
- What happens if I repeat an action?
- What happens if I navigate back and forth?
- What happens if I remove something?
- What happens at the boundary?
- What happens if I perform actions in an unusual order?
- Does the application behave according to the requirement?

The goal is not to intentionally damage the application. The goal is to **explore the application systematically and find behavior that may indicate a defect.**

---

## 3. Bug Lifecycle

A bug normally moves through several stages during its lifetime.

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

If the bug is still present during retesting:

```
Retest
  ↓
Bug Still Exists
  ↓
Reopened
  ↓
In Progress
```

**Common Bug Statuses**

- **New** — the bug has been reported but has not yet been processed.
- **Assigned** — the bug has been assigned to a developer or responsible team member.
- **In Progress** — the developer is currently working on the issue.
- **Fixed** — the developer has made a change intended to resolve the issue.
- **Ready for Retest** — the fix is ready for QA to verify.
- **Retest** — QA checks whether the reported issue has actually been fixed.
- **Closed** — QA confirms that the issue has been fixed successfully.
- **Reopened** — the issue still exists after the fix, so QA sends it back for further development.

---

## 4. Retesting

Retesting means testing a specific bug again after the developer claims that it has been fixed.

```
Bug reported
      ↓
Developer fixes bug
      ↓
QA retests the same scenario
      ↓
Bug fixed → Close
Bug still exists → Reopen
```

**Example**

Suppose the Login button does not work with valid credentials. After the developer fixes it, QA repeats the same test:

1. Enter valid username
2. Enter valid password
3. Click Login

If the user successfully logs in, the bug can be closed. If the problem still occurs, the bug should be reopened.

---

## 5. Regression Testing

Regression testing checks whether a new fix or change has caused problems in other existing features.

For example: a developer fixes the Login functionality. QA should not only test Login again — they may also check:

- Logout
- Product browsing
- Cart
- Checkout
- Other features affected by the change

**Retesting vs Regression Testing**

| Retesting | Regression Testing |
|---|---|
| Checks whether a specific bug was fixed | Checks whether existing functionality still works |
| Focuses on the reported defect | Focuses on affected/existing features |
| Usually repeats the failed test | May involve multiple test cases |

---

## 6. How to Confirm a Bug

An unexpected result does not automatically mean there is a bug. Before reporting a defect:

1. Reproduce the behavior.
2. Compare the actual result with the expected result.
3. Check the requirement.
4. Verify the test data.
5. Verify the test environment.
6. Repeat the test if necessary.
7. Decide whether the behavior is actually a defect.

**Important QA Rule**

> A failed test does not automatically mean there is a bug.

A test can fail because:

- The test case is incorrect.
- The requirement was misunderstood.
- The expected result was wrong.
- The behavior is intentional.
- There is an actual defect.

---

## 7. Practical Testing — Sauce Demo

For practical testing, I used Sauce Demo.

**Application:** Sauce Demo — Web Application

### Test 1 — Cart Badge After Removing Product

- **Test ID:** TC_ID_001
- **Scenario:** Verify that the cart item count updates correctly after removing a product.
- **Environment:** Sauce Demo — Web application / Cart functionality
- **Precondition:** User is on the Login page.

**Steps**

1. Log in to Sauce Demo.
2. Add any product to the cart.
3. Observe the cart badge.
4. Open the cart.
5. Remove the product.
6. Observe the cart badge again.

- **Expected Result:** The product should disappear from the cart, and the cart badge should no longer indicate that the product is in the cart.
- **Actual Result:** The product disappeared from the cart, and the cart badge no longer indicated that the product was in the cart.
- **Status:** PASS

**Conclusion:** The cart badge updated correctly after the product was removed. No defect was identified during this test.

### Test 2 — Cart Quantity After Navigation

- **Test ID:** TC_ID_001
- **Scenario:** Verify that the cart maintains the correct product quantity after navigating between pages.
- **Environment:** Sauce Demo — Web application / Cart functionality
- **Precondition:** User is on the Login page.

**Steps**

1. Log in.
2. Add one product to the cart.
3. Open the cart.
4. Go back to the Products page.
5. Open the cart again.
6. Check the product and quantity.

- **Expected Result:** The product should remain in the cart, and its quantity should remain unchanged after navigating between pages.
- **Actual Result:** The product remained in the cart, and its quantity remained unchanged after navigating between pages.
- **Status:** PASS

**Conclusion:** The cart maintained the product and its quantity after navigating between pages. No defect was identified during this test.

### Test 3 — Adding the Same Product Multiple Times

- **Test ID:** TC_ID_002
- **Scenario:** Verify that adding the same product multiple times results in the expected cart quantity.
- **Environment:** Sauce Demo — Web application / Cart functionality
- **Precondition:** User is on the Login page.

**Steps**

1. Log in to Sauce Demo.
2. Choose one product.
3. Click Add to cart.
4. Try to click Add to cart again for the same product.
5. Open the cart.
6. Check the product quantity.

**Initial Observation**

Initially, the test appeared to fail because the same product could not be added multiple times. However, the behavior was investigated further.

**Investigation**

After the product was added once, the Add to Cart button changed to Remove. This means the application intentionally prevents the same product from being added again through the same button. Therefore, the observed behavior was not treated as a defect.

- **Final Expected Result:** The application should prevent the same product from being added multiple times if duplicate additions are not supported.
- **Actual Result:** After adding the product once, the Add to Cart button changed to Remove, preventing the same product from being added again.
- **Status:** PASS

**Conclusion:** The behavior was intentional application behavior and was not a confirmed bug. No bug report was created for this behavior.

---

## 8. Important Lesson from Test 3

This was an important practical QA lesson.

**Initially:**

- Expected: Same product can be added multiple times
- Actual: Same product cannot be added multiple times
- Result: FAIL

**After investigating the application's behavior:**

- Requirement / Intended behavior: Duplicate addition is not supported
- Actual: Add to Cart changes to Remove
- Result: PASS

Therefore:

> Never report a bug simply because the actual result is different from your initial assumption.

First confirm the requirement and intended behavior.

---

## Day 18 Test Summary

| Test ID | Scenario | Result |
|---|---|---|
| TC_ID_001 | Cart badge after removing product | PASS |
| TC_ID_001 | Cart quantity after navigation | PASS |
| TC_ID_002 | Adding the same product multiple times | PASS |

**Note:** Test IDs should normally be unique within a test suite. The first two exercises were documented as `TC_ID_001` during practice, but in a real project I should assign unique IDs such as `TC_CART_001`, `TC_CART_002`, and `TC_CART_003`.

---

## Key QA Lessons

**1. Failed Test ≠ Confirmed Bug**
A failed test only tells me that the actual result did not match the current expected result. I must investigate before reporting a defect.

**2. Requirements Matter**
The expected behavior should come from the requirement or intended application behavior, not from assumptions.

**3. Reproduce Before Reporting**
A suspected issue should be reproducible and clearly documented.

**4. Retesting and Regression Are Different**

- Retesting: verify that a specific bug has been fixed.
- Regression testing: verify that the fix has not broken existing functionality.

**5. Think Like a Bug Hunter**

A QA tester should explore:

```
Normal behavior
      ↓
Edge cases
      ↓
Unexpected actions
      ↓
Observe behavior
      ↓
Compare with requirement
      ↓
Confirm defect
```

---

## Day 18 Summary

Today I learned how to move beyond simply executing test cases and start thinking like a bug hunter.

I practiced testing cart functionality in Sauce Demo and learned that an unexpected behavior must be investigated before it is reported as a bug.

I also learned the basic bug lifecycle, retesting, regression testing, and the importance of requirements when determining whether something is actually a defect.

---

## Day 18 Status

**Completed**

Topics completed:

- Bug Hunting
- Bug Hunting Mindset
- Bug Lifecycle
- Bug Statuses
- Retesting
- Regression Testing
- Confirming a Bug
- Practical Bug Hunting
- Sauce Demo Testing
- Distinguishing Failed Tests from Actual Bugs

**Day 18: DONE **

---

### One Thing I Intentionally Corrected

You used `TC_ID_001` for two different tests during practice. I've **kept your original practice records**, but added a note explaining that in a real QA project, every test case should have a **unique Test ID**.

For the next days, we'll use a cleaner naming convention such as:

```
TC_LOGIN_001
TC_CART_001
TC_CART_002
TC_CHECKOUT_001
```

---

*End of Day 18 guide*