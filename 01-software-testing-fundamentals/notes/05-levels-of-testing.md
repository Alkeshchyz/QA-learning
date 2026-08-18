# Day 5 — Levels of Testing

Today we're learning where testing happens in the software development process.

The four levels we'll focus on are:

- Unit Testing
- Integration Testing
- System Testing
- Acceptance Testing

The easiest way to understand them is to imagine we're building an e-commerce application.

---

## 1. Unit Testing

### What Is It?

Unit testing tests the smallest individual components of software in isolation. A "unit" could be:

- A function
- A method
- A class
- A small component

Usually, developers write and run unit tests.

**Example**

Suppose the e-commerce application has a function:

```
calculate_total(price, quantity)
```

For `price = Rs. 500`, `quantity = 2` → Expected: `Rs. 1000`

A unit test checks whether that individual function works correctly.

> Unit = one small piece

---

## 2. Integration Testing

Now imagine several individual components need to communicate. For example:

```
Login Service
  ↓
User Database
  ↓
Authentication API
```

Each component might work perfectly by itself. But what if they don't communicate correctly? That's where integration testing comes in.

**Example**

A user logs into an e-commerce website.

```
Login UI
  ↓
Login API
  ↓
Authentication Service
  ↓
Database
```

Integration testing checks whether these components work correctly together.

> Integration = components working together

---

## 3. System Testing

Now we test the complete integrated application as a whole. For our e-commerce system:

```
Login
  ↓
Search product
  ↓
Add to cart
  ↓
Checkout
  ↓
Payment
  ↓
Order confirmation
```

System testing checks whether the entire application behaves according to its requirements. This is where manual QA engineers often spend significant time.

**Example**

Test scenario: *A registered user should be able to purchase a product successfully.*

The tester may execute the complete flow:

```
Login
  ↓
Search
  ↓
Product selection
  ↓
Cart
  ↓
Address
  ↓
Payment
  ↓
Order confirmation
```

> System = complete software

---

## 4. Acceptance Testing

Now we ask: *"Is this software acceptable to the customer/business/user?"*

Acceptance testing focuses on whether the system satisfies the business requirements and intended use. It may involve:

- Customer representatives
- Business users
- Product owners
- End users
- QA/team members, depending on the organization

A common form is **UAT — User Acceptance Testing**.

Suppose the business requirement is:

> Customers must be able to return products within 7 days.

During acceptance testing, business users may verify that the complete return process works as expected. If the business is satisfied with the system, it can proceed toward release.

> Acceptance = Is the product acceptable to the customer/business?

---

## The Four Levels Together

Remember this sequence:

```
UNIT
  ↓
INTEGRATION
  ↓
SYSTEM
  ↓
ACCEPTANCE
```

Or: **One piece → Pieces together → Whole system → Customer acceptance**

---

## Real-World E-Commerce Example

Imagine we're building Daraz-like functionality.

**Unit Testing**

Test: `calculateDiscount()` — does the function calculate the discount correctly?

**Integration Testing**

Test:

```
Cart
  ↓
Order Service
  ↓
Payment Service
```

Do these services communicate correctly?

**System Testing**

Test:

```
Login
  ↓
Search
  ↓
Cart
  ↓
Checkout
  ↓
Payment
  ↓
Order confirmation
```

Does the complete application work?

**Acceptance Testing**

Business/user asks: *"Can customers actually purchase products and receive the expected order confirmation?"* Does the application satisfy the business requirement?

---

## Important Distinction

Don't think: *"Unit = small testing, System = big testing."* That's incomplete.

The main difference is the scope and interaction being evaluated.

| Level | Main Focus |
|---|---|
| Unit | Individual component |
| Integration | Interaction between components |
| System | Complete integrated system |
| Acceptance | Business/user requirements |

---

## Who Usually Performs Them?

This can vary between organizations, so don't treat this as an absolute rule.

| Level | Common Participants |
|---|---|
| Unit | Developers |
| Integration | Developers + QA |
| System | QA/Testers |
| Acceptance | Business users/Product Owner/Customer + QA |

A modern team may have developers and QA involved at multiple levels.

---

## Common Beginner Mistake

Don't say: *"QA only performs system testing."*

QA can contribute to all levels, depending on the organization. For example, QA might:

- Review unit-test coverage
- Create integration test scenarios
- Perform system testing
- Support UAT

The responsibilities depend on the team's process.

---

## Let's Connect This With SDLC/STLC

You learned SDLC on Day 2. Now connect the concepts:

```
Requirements
  ↓
Design
  ↓
Development
  ↓
Testing
  ↓
Deployment
```

During development/testing, different testing levels can occur:

```
Unit Testing
  ↓
Integration Testing
  ↓
System Testing
  ↓
Acceptance Testing
```

They aren't necessarily performed as one rigid sequence in every modern development methodology, but this model is useful for understanding their scope.

---

## Example: Banking Application

Let's make sure you can apply the concept outside e-commerce.

**Unit Testing**

Test: `calculateInterest()` — does it calculate interest correctly?

**Integration Testing**

Test: Account service ↔ Transaction service — do they exchange data correctly?

**System Testing**

Test: Login → Account → Transfer → Transaction history — does the complete banking system work?

**Acceptance Testing**

Business/user verifies: *Can customers safely transfer money according to the business requirements?*

---

## Quick Memory Trick

- **UNIT** — "Does this piece work?"
- **INTEGRATION** — "Do these pieces work together?"
- **SYSTEM** — "Does the whole system work?"
- **ACCEPTANCE** — "Does it satisfy the customer/business?"

If you remember those four questions, you've understood the concept.

---

*End of Day 5 guide*