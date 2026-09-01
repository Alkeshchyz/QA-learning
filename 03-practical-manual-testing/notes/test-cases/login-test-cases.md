# Login Test Cases

## Overview

This document contains manual test cases for verifying the login functionality of a web application. The suite covers one positive scenario and five negative scenarios.

## Requirement

**Requirement ID:** `REQ-LOGIN-001`

> A registered user should be able to log in using a valid email and password.

## Test Scenarios

| Scenario ID | Test scenario | Classification |
|---|---|---|
| `TS_LOGIN_001` | Verify login with valid credentials. | Positive |
| `TS_LOGIN_002` | Verify login with an incorrect email and password. | Negative |
| `TS_LOGIN_003` | Verify login with an incorrect email but the correct password. | Negative |
| `TS_LOGIN_004` | Verify login with an empty email field. | Negative |
| `TS_LOGIN_005` | Verify login with an empty password field. | Negative |
| `TS_LOGIN_006` | Verify login with an incorrectly formatted email. | Negative |

## Test Case Summary

| Test case ID | Scenario | Type | Execution status |
|---|---|---|---|
| `TC_LOGIN_001` | Valid credentials | Positive | Not Executed |
| `TC_LOGIN_002` | Incorrect email and password | Negative | Not Executed |
| `TC_LOGIN_003` | Incorrect email with correct password | Negative | Not Executed |
| `TC_LOGIN_004` | Empty email | Negative | Not Executed |
| `TC_LOGIN_005` | Empty password | Negative | Not Executed |
| `TC_LOGIN_006` | Incorrectly formatted email | Negative | Not Executed |

## Detailed Test Cases

### TC_LOGIN_001 — Successful Login with Valid Credentials

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_001` |
| **Test Scenario** | Verify successful login with valid credentials. |
| **Preconditions** | User has a registered account and is on the Login page. |
| **Test Data** | Email: `alkesh@gmail.com`<br>Password: `1234` |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Enter the valid registered email address.
4. Enter the correct password.
5. Click the **Login** button.

**Expected Result**

- The user is successfully logged in.
- The user is redirected to the appropriate authenticated page or dashboard.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

---

### TC_LOGIN_002 — Incorrect Email and Password

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_002` |
| **Test Scenario** | Verify login with an incorrect email and password. |
| **Preconditions** | User is on the Login page. |
| **Test Data** | Email: `wronguser@gmail.com`<br>Password: `wrongpassword` |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Enter an unregistered, correctly formatted email address.
4. Enter an incorrect password.
5. Click the **Login** button.

**Expected Result**

- The user cannot log in.
- The user remains on the Login page.
- An appropriate error message is displayed.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

---

### TC_LOGIN_003 — Incorrect Email with Correct Password

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_003` |
| **Test Scenario** | Verify login with an incorrect email but the correct password. |
| **Preconditions** | User has a registered account and is on the Login page. |
| **Test Data** | Email: `wronguser@gmail.com`<br>Password: `1234` |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Enter an unregistered, correctly formatted email address.
4. Enter the correct password.
5. Click the **Login** button.

**Expected Result**

- The user cannot log in.
- The user remains on the Login page.
- An appropriate error message is displayed.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

---

### TC_LOGIN_004 — Empty Email

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_004` |
| **Test Scenario** | Verify login with an empty email field. |
| **Preconditions** | User is on the Login page. |
| **Test Data** | Email: _Leave blank_<br>Password: `1234` |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Leave the Email field empty.
4. Enter a valid password.
5. Click the **Login** button.

**Expected Result**

- The user cannot log in.
- The user remains on the Login page.
- An appropriate validation or error message is displayed.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

---

### TC_LOGIN_005 — Empty Password

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_005` |
| **Test Scenario** | Verify login with an empty password field. |
| **Preconditions** | User is on the Login page. |
| **Test Data** | Email: `alkesh@gmail.com`<br>Password: _Leave blank_ |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Enter a valid registered email address.
4. Leave the Password field empty.
5. Click the **Login** button.

**Expected Result**

- The user cannot log in.
- The user remains on the Login page.
- An appropriate validation or error message is displayed.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

---

### TC_LOGIN_006 — Incorrectly Formatted Email

| Field | Details |
|---|---|
| **Test Case ID** | `TC_LOGIN_006` |
| **Test Scenario** | Verify login with an incorrectly formatted email. |
| **Preconditions** | User is on the Login page. |
| **Test Data** | Email: `alkesh@gmail`<br>Password: `1234` |

**Steps**

1. Open the application.
2. Navigate to the Login page.
3. Enter an incorrectly formatted email address.
4. Enter a valid password.
5. Click the **Login** button.

**Expected Result**

- The user cannot log in.
- The user remains on the Login page.
- An appropriate email-format validation or error message is displayed.

**Actual Result:** _To be filled during test execution._  
**Status:** `Not Executed`

## Positive and Negative Coverage

| Category | Test cases | Count |
|---|---|---:|
| Positive testing | `TC_LOGIN_001` | 1 |
| Negative testing | `TC_LOGIN_002` to `TC_LOGIN_006` | 5 |
| **Total** |  | **6** |

## Execution Status

| Metric | Count |
|---|---:|
| Total test cases | 6 |
| Not Executed | 6 |
| Passed | 0 |
| Failed | 0 |
| Blocked | 0 |

## QA Notes

- This test suite has not been executed. Actual results and final statuses must be recorded only after testing the application.
- `wronguser@gmail.com` is intentionally a valid-format but unregistered email address. This keeps TC_LOGIN_002 and TC_LOGIN_003 separate from the email-format validation test in TC_LOGIN_006.
- The exact wording of an error message is not specified by the requirement. During execution, verify that an appropriate message appears; record the actual wording in the Actual Result field.
- If an expected result does not match the observed behavior, mark the test case as `Failed` and create a bug report with the relevant test-case ID.
