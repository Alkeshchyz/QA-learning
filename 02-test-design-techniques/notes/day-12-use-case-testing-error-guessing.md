# Day 12 — Use Case Testing + Error Guessing

We've reached the final part of our Test Design Techniques phase.

So far:

- Day 8 → Equivalence Partitioning ✅
- Day 9 → Boundary Value Analysis ✅
- Day 10 → Decision Table Testing ✅
- Day 11 → State Transition Testing ✅
- Day 12 → Use Case Testing + Error Guessing 

Today we'll learn two techniques that are very useful for practical QA.

---

# Part 1 — Use Case Testing

## 1. What Is a Use Case?

A use case describes how a user interacts with a system to achieve a particular goal.

> Example: Customer places an order

The basic flow could be:

```
Login
  ↓
Search product
  ↓
Select product
  ↓
Add to cart
  ↓
Checkout
  ↓
Make payment
  ↓
Order confirmed
```

This is a use case.

---

## 2. What Is Use Case Testing?

> Use Case Testing verifies that the system works correctly through complete user scenarios.

Instead of testing isolated features, we test a real user workflow from beginning to end.

**Example**

Instead of separately testing login, search, cart, and payment, we test:

```
Login
  ↓
Search
  ↓
Add to Cart
  ↓
Checkout
  ↓
Payment
  ↓
Order Confirmation
```

This is closer to how a real customer uses the application.

---

## 3. Main Flow

A main flow is the normal/expected path where everything goes correctly.

**Use Case: Purchase Product**

1. User logs in
2. Searches for product
3. Selects product
4. Adds product to cart
5. Proceeds to checkout
6. Enters address
7. Selects payment method
8. Completes payment
9. Order is confirmed

Expected: the customer successfully places the order.

This is sometimes called the **happy path**.

---

## 4. Alternative / Exception Flows

Real users don't always follow the happy path. For example:

```
Login
  ↓
Wrong password
  ↓
Error message
```

```
Checkout
  ↓
Payment fails
  ↓
Order should NOT be confirmed
```

```
Product
  ↓
Out of stock
  ↓
User cannot purchase
```

These are alternative or exception scenarios.

---

## 5. Use Case Testing Example — Login

**Use Case:** User logs into the application.

**Main flow**

```
Enter email
  ↓
Enter password
  ↓
Click Login
  ↓
Dashboard
```

**Alternative flows**

*Wrong password*

```
Enter email
  ↓
Wrong password
  ↓
Click Login
  ↓
Error message
```

*Empty password*

```
Enter email
  ↓
Password empty
  ↓
Click Login
  ↓
Validation message
```

*Unregistered email*

```
Unregistered email
  ↓
Correct-looking password
  ↓
Login
  ↓
Login rejected
```

A good QA tester doesn't test only the happy path.

---

## 6. Use Case Testing vs Individual Feature Testing

Imagine an e-commerce application.

**Feature testing** — you might test: *"Does the 'Add to Cart' button work?"*

**Use case testing** — you test:

```
Login
  ↓
Search
  ↓
Product
  ↓
Add to Cart
  ↓
Checkout
  ↓
Payment
  ↓
Order Confirmation
```

The second approach checks whether the whole business flow works together. This connects nicely with what you learned in System Testing and Integration Testing.

---

# Part 2 — Error Guessing

Now for a very different technique.

## 7. What Is Error Guessing?

> Error Guessing is a test design technique where testers use their experience, intuition, and knowledge of common mistakes to predict where defects are likely to occur.

It isn't as systematic as EP or BVA. Instead, you think: *"If I were the developer/user, where could this go wrong?"*

---

## 8. Example — Login Page

A beginner might test: correct email, correct password.

An experienced tester starts thinking:

- What if email is empty?
- What if password is empty?
- What if I enter spaces?
- What if I paste the password?
- What if I click Login multiple times?
- What if I use a very long email?
- What if I refresh?
- What if I use special characters?
- What if I enter wrong password repeatedly?

These ideas can come from previous experience with common defects. That's error guessing.

---

## 9. Common Error-Guessing Ideas

When testing a form, you might think about:

- **Empty values** — `Username = ""`, `Password = ""`
- **Null values** — missing input or missing data
- **Special characters** — `@ # $ % & *`
- **Very long input** — 1000 characters
- **Spaces** — `"   username   "`
- **Duplicate clicks** — Click Submit, Click Submit, Click Submit
- **Refresh/back button** — Submit → Refresh → Back
- **Invalid formats** — `abc` instead of `valid@email.com`
- **Network interruption** — Submit payment → Internet disconnects

These aren't necessarily derived from a formal specification — they're tester intuition based on likely failure points.

---

## 10. Error Guessing Example — Payment

Suppose you're testing: *"User can pay for an order."*

A tester may think:

- What if payment is clicked twice?
- What if internet disconnects?
- What if payment succeeds but confirmation doesn't load?
- What if the user presses Back?
- What if payment times out?
- What if the amount is modified?
- What if the payment gateway is unavailable?

These are excellent areas to investigate.

---

## 11. Error Guessing vs Other Techniques

This is important.

```
EP
Input
  ↓
Divide into groups
  ↓
Select representatives

BVA
Identify boundaries
  ↓
Test around boundaries

Decision Table
Conditions
  ↓
Combinations
  ↓
Expected results

State Transition
Current state
  ↓
Event
  ↓
New state

Use Case
User goal
  ↓
Complete workflow

Error Guessing
Tester experience
  ↓
"What could go wrong?"
  ↓
Test it
```

---

## Use Case + Error Guessing Together

In real QA, you don't have to use only one technique.

Suppose we have: *"Customer returns a product."*

**Use Case**

```
Login
  ↓
Open orders
  ↓
Select delivered product
  ↓
Click Return
  ↓
Select reason
  ↓
Submit
  ↓
Return requested
```

**Then use Error Guessing:**

- What if product isn't delivered?
- What if return period expired?
- What if reason is empty?
- What if Return is clicked twice?
- What if internet disconnects?
- What if product ID is invalid?
- What if the page is refreshed?

Now we're thinking much more like a real QA.

---

## The 5 Techniques We've Learned

This is worth saving.

| Technique | Main Question |
|---|---|
| Equivalence Partitioning | What input groups exist? |
| Boundary Value Analysis | What happens at the edges? |
| Decision Table | What happens with combinations of conditions? |
| State Transition | How does the system change states? |
| Use Case Testing | Can the user complete the entire workflow? |
| Error Guessing | Where might defects commonly occur? |

---

*End of Day 12 guide*