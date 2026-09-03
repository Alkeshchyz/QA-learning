# Day 14 — Professional Test Case Design & Organization

Yesterday you created your first 6 login test cases. Today we're going to make you better at writing and organizing them like a QA tester.

The goal isn't to memorize definitions. We'll improve the test suite you already created.

---

## 1. Test Scenario vs Test Case vs Test Suite

This is an important distinction.

**Test Scenario** — a high-level condition/functionality that needs to be tested.

> Example: Verify login functionality.

**Test Case** — a specific set of steps, data, and expected results used to test one condition.

> Example: Verify login with valid credentials.

**Test Suite** — a collection of related test cases. Your six login cases together form a **Login Test Suite**.

```
LOGIN FUNCTIONALITY
       │
       ↓
  Test Scenario
       │
       ├── TC_LOGIN_001
       ├── TC_LOGIN_002
       ├── TC_LOGIN_003
       ├── TC_LOGIN_004
       ├── TC_LOGIN_005
       └── TC_LOGIN_006
```

---

## 2. Test Case ID

A good ID makes test cases easy to identify. You've already started doing this correctly: `TC_LOGIN_001`, `TC_LOGIN_002`, `TC_LOGIN_003` ...

A useful pattern is:

```
TC_[FEATURE]_[NUMBER]
```

For example:

```
TC_LOGIN_001
TC_LOGIN_002

TC_PAYMENT_001
TC_PAYMENT_002

TC_RETURN_001
TC_RETURN_002
```

This becomes especially useful when your project has hundreds of test cases.

---

## 3. Preconditions

A precondition describes what must be true **before** executing the test.

> Example: User is on the Login page. For a successful login: user has a registered account.

- ❌ **Bad:** "Open application and go to login page." — that's a test step, not a precondition.
- ✅ **Good:** "User is on the Login page."

---

## 4. Test Data

Test data is the information you use while executing a test.

**Example**

- Email: `alkesh@gmail.com`
- Password: `1234`

For an invalid email:

- Email: `alkesh@gmail`
- Password: `1234`

**Important distinction**

These are different: *wrong email* and *invalid email format*.

For example, `wronguser@gmail.com` is a valid email format, but could be an unregistered email. While `wronguser@gmail` has an invalid format.

That's why your `TC_LOGIN_003` and `TC_LOGIN_006` shouldn't use the same type of test data.

---

## 5. Test Steps

Test steps should be:

**Clear**

- ❌ "Login with credentials."
- ✅
  1. Enter a valid email.
  2. Enter a valid password.
  3. Click Login.

**Reproducible**

Another tester should be able to follow your steps without asking you what you meant.

**One action at a time**

Instead of "Enter email and password and click Login," prefer:

1. Enter email.
2. Enter password.
3. Click Login.

---

## 6. Expected Result

This is one of the most important parts of a test case. It tells us: *what should happen?*

- ❌ **Bad:** "Login successful."
- ✅ **Better:** "User should be successfully logged in and redirected to the dashboard."

For a failed login: *"User should not be logged in and should remain on the Login page. An appropriate error message should be displayed."*

> Rule: your expected result should be observable and testable.

---

## 7. Actual Result

Don't write the actual result before executing the test.

**Before execution:**

> Actual Result: To be filled during test execution.

After execution, you record what actually happened.

**Example**

- Expected: User should remain on Login page.
- Actual: User was redirected to the dashboard.

Now we have a potential defect.

---

## 8. Status

**Before execution:** `Not Executed`

**After execution, normally:** `PASS`, `FAIL`, or `BLOCKED`

**Example**

- Expected: Login should fail. Actual: Login failed. → **Status: PASS**
- Expected: Login should fail. Actual: User was logged in. → **Status: FAIL**

---

## 9. Positive vs Negative Testing

Your current login suite is actually a good example.

**Positive** — testing whether the system works with valid input.

```
Valid email
    +
Valid password
    ↓
Login succeeds
```

**Negative** — testing how the system behaves with invalid/unexpected input: wrong email, wrong password, empty email, empty password, invalid email format.

Your current suite:

| Test Case | Type |
|---|---|
| TC_LOGIN_001 | Positive |
| TC_LOGIN_002 | Negative |
| TC_LOGIN_003 | Negative |
| TC_LOGIN_004 | Negative |
| TC_LOGIN_005 | Negative |
| TC_LOGIN_006 | Negative |

---

## 10. Avoid Duplicate Test Cases

Suppose you have:

- TC001 → Wrong email + wrong password
- TC002 → Wrong email + wrong password

These are essentially testing the same condition — that's unnecessary duplication. Instead, each test should ideally cover a meaningfully different condition.

Your current cases cover:

- Valid credentials
- Wrong email + wrong password
- Wrong email + correct password
- Empty email
- Empty password
- Invalid email format

That's reasonable coverage for a basic login suite.

---

## 11. Requirement Traceability

Now we're getting into something used in professional QA.

You have `REQ-LOGIN-001`:

> Requirement: A registered user should be able to log in using a valid email and password.

Then your test cases can be linked to that requirement:

| Requirement | Test Case |
|---|---|
| REQ-LOGIN-001 | TC_LOGIN_001 |
| REQ-LOGIN-001 | TC_LOGIN_002 |
| REQ-LOGIN-001 | TC_LOGIN_003 |
| REQ-LOGIN-001 | TC_LOGIN_004 |
| REQ-LOGIN-001 | TC_LOGIN_005 |
| REQ-LOGIN-001 | TC_LOGIN_006 |

This relationship is called **traceability**. Later, when you work with Jira or other test-management tools, you'll see this concept again.

---

## 12. Professional Test Case Format

Eventually, instead of keeping each test case as a large block of text, you'll often use a table/spreadsheet:

| ID | Scenario | Preconditions | Test Data | Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| TC_LOGIN_001 | Valid login | Registered user | Valid credentials | Enter credentials → Login | Dashboard displayed | — | Not Executed |
| TC_LOGIN_002 | Wrong credentials | Login page | Invalid credentials | Enter credentials → Login | Login rejected | — | Not Executed |
| TC_LOGIN_003 | Wrong email | Login page | Wrong email + valid password | Enter credentials → Login | Login rejected | — | Not Executed |

This is much easier to manage when you have 50, 100, or 500 test cases.

---

*End of Day 14 guide*