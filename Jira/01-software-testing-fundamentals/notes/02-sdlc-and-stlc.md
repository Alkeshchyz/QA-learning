# Day 2: Where Does Testing Fit Into Software Development?

Today we move from "What is testing?" to "Where does testing fit into software development?"

This is important because a QA engineer doesn't work separately from development. QA is involved throughout the software development process.

## 🎯 Day 2 Objectives

By the end of today, you should understand:

- ✓ What is SDLC?
- ✓ SDLC phases
- ✓ What is STLC?
- ✓ STLC phases
- ✓ SDLC vs STLC
- ✓ Where QA fits into SDLC
- ✓ How a real project moves from requirement → testing → release

## 1. What Is SDLC?

**SDLC** = Software Development Life Cycle

It is a structured process used to develop software from the initial idea/requirement through development, testing, deployment, and maintenance.

Think of it as:

```
Idea
  ↓
Requirements
  ↓
Design
  ↓
Development
  ↓
Testing
  ↓
Deployment
  ↓
Maintenance
```

**Example:**

Imagine a company wants to build a food delivery app. The company doesn't immediately tell developers, "Start coding." There are multiple steps before and after coding.

## 2. SDLC Phases

We'll use a simple model for now.

### Phase 1 — Requirement Analysis

The team determines: What should the software do?

For our food delivery app, the user should be able to:

- Register
- Login
- Search restaurants
- Add food to cart
- Make payment
- Track order

**QA Involvement:**

A QA shouldn't wait until the software is finished. QA can review requirements and ask:

- "What happens if payment fails?"
- "Can users order when a restaurant is closed?"
- "What happens when the food becomes unavailable?"

> This is already quality thinking.

### Phase 2 — Design

The team decides: How will we build it? This can include:

- UI design
- Database design
- System architecture
- API design

**Example:**

```
Mobile App
  ↓
Backend API
  ↓
Database
```

**QA Involvement:** QA can review designs and identify potential problems early.

### Phase 3 — Development

Developers write the actual code.

**Example:**

```
Login UI
  ↓
Login API
  ↓
Database
```

**QA Involvement:**

QA may start preparing:

- Test scenarios
- Test cases
- Test data
- Testing environments

> Important: QA work doesn't necessarily begin only after coding finishes.

### Phase 4 — Testing

Now the software is tested against its requirements. QA executes test cases and reports defects.

**Example:**

- **Expected:** Invalid password → Error message
- **Actual:** Invalid password → User successfully logs in

> QA reports the defect.

### Phase 5 — Deployment

Once the software meets the release criteria, it is deployed to users.

**Example:**

```
Development
  ↓
Testing/Staging
  ↓
Production
```

### Phase 6 — Maintenance

After release, users may discover problems. There may also be:

- New features
- Bug fixes
- Security updates
- Performance improvements
- Compatibility changes

**QA Involvement:** QA tests these changes and performs regression testing where appropriate.

## 3. What Is STLC?

**STLC** = Software Testing Life Cycle

STLC describes the specific activities performed during the testing process.

Think:

- SDLC = entire software development journey
- STLC = testing journey within/alongside that development process

## 4. STLC Phases

A commonly used STLC structure is:

```
Requirement Analysis
  ↓
Test Planning
  ↓
Test Case Development
  ↓
Test Environment Setup
  ↓
Test Execution
  ↓
Test Closure
```

Let's understand each.

### 1. Requirement Analysis

QA studies the requirements.

**Example:** User must be able to reset their password using their registered email.

QA asks:

- What happens with an unregistered email?
- What if the email is empty?
- What if the reset link expires?
- How long should the reset link remain valid?

### 2. Test Planning

The team decides:

- What will we test?
- Who will test?
- What tools will we use?
- How much time do we have?
- What are the risks?
- What is the testing scope?

**Example:**

- Tool: Jira
- API testing: Postman
- Browser testing: Chrome/Firefox
- Testing period: 5 days

### 3. Test Case Development

Now QA creates detailed test cases.

**Example:**

| Test Case | Action | Expected Result |
|---|---|---|
| TC-001 | Enter valid login credentials | Dashboard opens |
| TC-002 | Enter wrong password | Error displayed |
| TC-003 | Leave password empty | Validation message |

### 4. Test Environment Setup

QA prepares the environment where testing will happen.

**Example:**

- Browser: Chrome
- OS: Windows
- Application: v1.2
- Database: Test DB
- API: Test server

### 5. Test Execution

Now we actually execute the test cases.

| Test Case | Result |
|---|---|
| TC-001 | PASS |
| TC-002 | PASS |
| TC-003 | FAIL |

If something doesn't behave as expected:

> Create a bug report.

### 6. Test Closure

After testing is completed, QA summarizes the results.

**Example:**

- Total test cases: 100
- Passed: 94
- Failed: 6
- Blocked: 0

Bugs by severity:

- Critical bugs: 0
- High bugs: 1
- Medium bugs: 4
- Low bugs: 1

Then QA prepares the necessary reports/documentation.

> This connects directly with the SQA article we researched earlier: maintaining records such as test cases, defects, changes and testing cycles is part of SQA.

## 5. SDLC vs STLC

This is something you should be able to explain in an interview.

| Feature | SDLC | STLC |
|---|---|---|
| Full Form | Software Development Life Cycle | Software Testing Life Cycle |
| Scope | Covers entire development process | Focuses specifically on testing |
| Phases | Requirement → Development → Testing → Deployment → Maintenance | Requirement analysis → Planning → Cases → Environment → Execution → Closure |
| People Involved | Developers, QA, BA, PM, etc. | Primarily focuses on testing activities |
| Nature | Broader | More specific |

**Easy memory trick:**

- SDLC = Build the software
- STLC = Test the software

> But remember: QA participates early in SDLC, not only during the testing phase.

## 6. Real-World Example

Let's say you're working at a Nepali software company developing an online shopping application.

**SDLC:**

```
Business requirement
  ↓
UI/architecture design
  ↓
Development
  ↓
Testing
  ↓
Production
  ↓
Maintenance
```

At the same time, QA follows testing activities:

```
Read requirements
  ↓
Plan testing
  ↓
Write test cases
  ↓
Prepare environment
  ↓
Execute tests
  ↓
Report defects
  ↓
Retest fixes
  ↓
Test closure
```

Notice something important:

> QA isn't simply "developer finished → QA tests." QA is involved throughout the process.

## 7. Day 2 Tester Mindset

Whenever you see a software feature, start thinking:

**Requirement → How can I test it?**

**Example:** Requirement: "User can withdraw money from an ATM."

Immediately think:

**Valid:**

- Correct PIN
- Sufficient balance
- Valid amount

**Invalid:**

- Wrong PIN
- Insufficient balance
- Zero amount
- Negative amount
- Amount greater than daily limit
- ATM has insufficient cash

> That thinking will become much more important when we learn test case design techniques.

---

*End of Day 2 guide*