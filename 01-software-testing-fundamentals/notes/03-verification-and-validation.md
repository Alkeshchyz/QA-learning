# Day 3 — Verification vs Validation

## Overview

Verification and Validation (V&V) are two fundamental concepts in Software Quality Assurance (SQA) and software testing. They help us answer two important questions:

> **Are we building the product correctly?**
> **Are we building the correct product?**

Understanding the difference between verification and validation is important for both practical QA work and QA interviews.

---

## Prerequisites

Before studying this topic, we have covered:

- **Day 1:** Introduction to Software Testing
- **Day 2:** Software Development Life Cycle (SDLC) and Software Testing Life Cycle (STLC)

---

## 1. Verification

### Definition

**Verification** is the process of checking whether software is being developed according to specified requirements, designs, specifications, and standards.

### Simple Definition

> Verification asks: "Are we building the product correctly?"

Verification mainly focuses on reviewing and evaluating work products rather than executing the completed software.

### What Can Be Verified?

During verification, the team may review:

- Requirement documents
- Design documents
- Specifications
- Test plans
- Test cases
- Architecture
- Source code
- Other project documentation

### Example of Verification

Suppose the requirement says:

> Password must contain at least 8 characters.

During verification, the QA team or other team members may review the project documentation. They discover:

```
Requirement:
Password must contain at least 8 characters.

Design:
Password must contain at least 6 characters.
```

There is already an inconsistency between the requirement and the design. This problem can be identified through a review — before executing the application. That is verification.

---

## 2. Validation

### Definition

**Validation** is the process of checking whether the developed software actually satisfies the user's needs and intended requirements.

### Simple Definition

> Validation asks: "Are we building the right product?"

Validation generally involves evaluating or executing the actual software.

### Example of Validation

Suppose the requirement says:

> Password must contain at least 8 characters.

A tester opens the application and enters:

```
abc123
```

The password contains only 6 characters.

- **Expected Result:** Password should be rejected.
- **Actual Result:** Password is accepted.

The tester has discovered a problem by interacting with the actual software. This is validation through testing.

---

## 3. The Easiest Way to Remember

**Verification** — Are we building the product right?

**Validation** — Are we building the right product?

**Memory Trick**

```
Verification → RIGHT PROCESS / PRODUCT CONSTRUCTION
Validation   → RIGHT PRODUCT / USER NEED
```

---

## 4. Verification vs Validation

| Verification | Validation |
|---|---|
| Asks: "Are we building the product right?" | Asks: "Are we building the right product?" |
| Checks against specifications and requirements | Checks against user and business needs |
| Often involves reviews and inspections | Usually involves evaluating/executing the software |
| Focuses on work products | Focuses on the actual product |
| Can happen before software execution | Requires a testable product or system |
| Helps prevent defects early | Helps identify problems in the developed product |

---

## 5. Real-World Example — Food Delivery Application

Imagine a company is developing a food delivery application.

**Requirement:** Users should be able to cancel an order before the restaurant starts preparing it.

### Verification

Before executing the application, QA and other team members can review the requirement and related project artifacts.

**Requirement Review**
QA asks: "Is the requirement clearly defined?" For example:

- When exactly can the user cancel?
- What happens after the restaurant starts preparing the order?
- What happens to the payment?
- What happens to the refund?

**Design Review**
QA checks: "Does the design support order cancellation?"

**Test Case Review**
QA checks: "Did we create test cases for cancellation before restaurant preparation?"

These are examples of verification.

### Validation

Now the application is running. A tester performs the following actions:

```
Login
  ↓
Select restaurant
  ↓
Select food
  ↓
Place order
  ↓
Cancel order before preparation
```

- **Expected Result:** Order should be cancelled.
- **Actual Result:** Order remains active.

The tester has discovered a problem by testing the actual application. This is validation.

---

## 6. Verification Isn't Only a QA Activity

A common beginner misunderstanding is that verification belongs only to QA. In reality, verification activities can involve multiple members of the software development team, including:

- QA engineers
- Developers
- Business analysts
- Project managers
- Technical leads
- Architects

**Common Verification Activities**

1. **Requirement Review** — Checking whether requirements are:
   - Clear
   - Complete
   - Consistent
   - Testable
   - Unambiguous
2. **Design Review** — Checking whether the proposed design satisfies the requirements.
3. **Code Review** — Developers or technical team members inspect source code to identify problems.
4. **Document Review** — Checking project documentation for correctness and consistency.
5. **Inspection** — A formal examination of a work product to identify defects.
6. **Walkthrough** — A team member presents a work product to other team members for discussion and feedback.

---

## 7. Why Verification Matters

Verification helps identify problems early.

Consider this situation: a developer spends two weeks implementing a feature based on an unclear requirement. After development is completed, QA discovers:

> "This isn't what the client actually wanted."

Now the team may need to:

```
Change requirements
  ↓
Modify design
  ↓
Change code
  ↓
Update test cases
  ↓
Retest
  ↓
Possibly redesign the feature
```

This can consume significant time and resources. If the requirement had been properly reviewed earlier, the problem could potentially have been identified before development started.

**Key idea:** Verification helps prevent defects by identifying problems early.

This reflects an important SQA principle: quality is not only about finding defects after development — it is also about preventing problems through appropriate processes and reviews.

---

## 8. Why Validation Matters

Even if requirements and designs look correct on paper, the actual software can still fail.

Consider a payment application.

**Requirement:** User should be able to complete payment successfully.

The development team implements the feature according to the specification. However, during real use, the tester discovers:

- Payment processing time = 60 seconds
- Users frequently abandon the payment process because it takes too long

Technically, the payment functionality may work. However, the product may still fail to satisfy the user's expectations.

Validation helps answer: *Does the actual product satisfy its intended purpose and user needs?*

---

## 9. Verification and Validation Together

Verification and validation are not alternatives. A quality-focused software development process needs both.

```
                 SOFTWARE QUALITY
                        │
              ┌─────────┴─────────┐
              │                   │
        Verification          Validation
              │                   │
       "Build it right"     "Build the right thing"
              │                   │
       Review work            Test the product
       products                against needs
```

---

## 10. Real-World Analogy — Building a House

Imagine you are building a house.

### Verification

You check: *Is the house being built according to the architectural plan?*

You may review:

- Building plans
- Measurements
- Materials
- Structural design
- Construction specifications

This is similar to verification.

### Validation

Now you ask: *Can the customer actually live comfortably in this house?*

You may check:

- Are the rooms usable?
- Is there enough space?
- Does the plumbing work?
- Does the electricity work?
- Does the house satisfy the customer's needs?

This is similar to validation.

---

## 11. Quick Comparison

**Verification**

```
Requirements
     ↓
Design
     ↓
Documents
     ↓
Reviews
     ↓
Inspections
```

**Validation**

```
Developed Software
       ↓
Execute Software
       ↓
Compare Actual vs Expected
       ↓
Identify Defects
       ↓
Confirm User/Business Needs
```

---

## 12. QA Interview Question

**Question:** What is the difference between verification and validation?

**Short Answer:** Verification checks whether the software is being developed correctly according to requirements, specifications, and design. Validation checks whether the developed software satisfies the user's needs and intended requirements.

**Easy Interview Version:** Verification asks, "Are we building the product right?" Validation asks, "Are we building the right product?"

---

## 13. Key Takeaways

- Verification focuses on checking work products and processes.
- Validation focuses on evaluating the actual software.
- Verification commonly involves reviews, inspections, and walkthroughs.
- Validation commonly involves executing and testing the software.
- Verification helps identify problems early.
- Validation confirms whether the actual product satisfies its intended purpose.
- Both verification and validation contribute to software quality.

---

## 14. One-Line Memory

**Verification** = Build the product right.
**Validation** = Build the right product.

---
<!-- Give three verification activities. -->
1. Review the requirement
Check whether "within 7 days" is clearly defined.

2. Review the return policy/design
Verify that the design specifies what happens when the 7-day period expires.

3. Review the test cases
Check whether test cases cover valid returns, expired returns, damaged products, etc.

<!-- Give five validation tests. -->
1. Return a product within 7 days of delivery → Return request should be accepted.
2. Attempt to return a product after 7 days → Return request should be rejected.
3. Attempt to return a product exactly on the 7th day → System should follow the defined return policy.
4. Verify customer ID and product ID → Return should be associated with the correct customer and product.
5. Check return status after submitting a request → Status should change correctly, e.g. Requested → Approved → Returned.
*End of Day 3 guide*