# Day 10 — Decision Table Testing

Yesterday we learned Boundary Value Analysis. Today we're learning a technique that's especially useful when a feature's result depends on multiple conditions.

## The Key Idea

> Decision Table Testing helps us test combinations of conditions and their corresponding actions/results.

Instead of asking *"What happens if I enter this value?"* we ask *"What should happen for every important combination of conditions?"*

---

## 1. Why Do We Need Decision Tables?

Imagine an e-commerce website has this rule:

> A customer gets free delivery if they are a premium member and their order is above Rs. 2,000.

There are two conditions:

- Condition 1 → Premium member?
- Condition 2 → Order > Rs. 2,000?

Each condition can be Yes / No, so there are multiple combinations. We can organize them in a decision table.

---

## 2. Basic Decision Table

| Conditions / Rules | Rule 1 | Rule 2 | Rule 3 | Rule 4 |
|---|---|---|---|---|
| Premium member? | Y | Y | N | N |
| Order > Rs. 2,000? | Y | N | Y | N |
| Free delivery? | Y | N | N | N |

Now we've covered all four possible combinations.

| Premium? | Order > 2000? | Result |
|---|---|---|
| Y | Y | Free delivery |
| Y | N | Paid delivery |
| N | Y | Paid delivery |
| N | N | Paid delivery |

---

## 3. Parts of a Decision Table

A decision table normally contains:

- **Conditions** — the things that influence the result. Example: Premium member? / Order > Rs. 2,000?
- **Actions / Results** — what the system should do. Example: Free delivery / Paid delivery
- **Rules** — each column represents one possible combination of conditions.

---

## 4. Why Is This Useful for QA?

Without a decision table, a tester might test "premium + large order" and forget "non-premium + large order" or "premium + small order."

Decision tables help us systematically cover the combinations.

---

## 5. Simple Login Example

> Requirement: A user can log in only if the email is valid and the password is correct.

There are two conditions: valid email? and correct password?

**Decision table:**

| Conditions / Rules | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Valid email? | Y | Y | N | N |
| Correct password? | Y | N | Y | N |
| Login successful? | Y | N | N | N |

So our tests become:

| Test | Email | Password | Expected |
|---|---|---|---|
| 1 | Valid | Correct | Login |
| 2 | Valid | Incorrect | Reject |
| 3 | Invalid | Correct | Reject |
| 4 | Invalid | Incorrect | Reject |

This is much more systematic than randomly trying inputs.

---

## 6. Real QA Example — Product Return

Let's connect this to the application we've been using.

> Requirement: A customer can return a product if the product was delivered and the return period has not expired.

We can identify:

- Condition 1 → Product delivered?
- Condition 2 → Within 7-day return period?

**Decision table:**

| Conditions / Rules | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Product delivered? | Y | Y | N | N |
| Within 7 days? | Y | N | Y | N |
| Return allowed? | Y | N | N | N |

**Test scenarios**

- **R1** — Delivered: Yes, Within 7 days: Yes → Expected: Return accepted
- **R2** — Delivered: Yes, Within 7 days: No → Expected: Return rejected
- **R3** — Delivered: No, Within 7 days: Yes → Expected: Return rejected
- **R4** — Delivered: No, Within 7 days: No → Expected: Return rejected

---

## 7. Another Example — Login With Account Status

> Requirement: A user can log in only if their credentials are correct and their account is active.

Conditions: credentials correct? and account active?

**Decision table:**

| Conditions / Rules | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Credentials correct? | Y | Y | N | N |
| Account active? | Y | N | Y | N |
| Login allowed? | Y | N | N | N |

Again, we have systematically covered the combinations.

---

## The Important Concept

With Equivalence Partitioning, we asked: *what groups of inputs exist?*
With Boundary Value Analysis, we asked: *what happens around the edges?*
With Decision Tables, we ask: *what happens when multiple conditions combine?*

```
EP
  ↓
Groups

BVA
  ↓
Boundaries

Decision Table
  ↓
Condition combinations
```

---

## 8. When Should You Use Decision Tables?

Decision tables are particularly useful when:

- There are multiple conditions.
- Different combinations produce different results.
- Business rules are complicated.
- There are many IF/ELSE conditions.
- You want systematic test coverage.

For example: *"Discount depends on membership + order amount + coupon."* That's a great candidate.

---

## 9. More Complex Example

> Requirement: A customer gets a discount if they are a premium member OR they have a valid coupon.

Conditions: premium member? and valid coupon?

**Decision table:**

| Conditions / Rules | R1 | R2 | R3 | R4 |
|---|---|---|---|---|
| Premium member? | Y | Y | N | N |
| Valid coupon? | Y | N | Y | N |
| Discount? | Y | Y | Y | N |

Notice the difference from our previous example — here the rule is **OR**, not **AND**. This is why decision tables are powerful: they make business logic visible.

---

## AND vs OR

**AND** — both conditions must be true.

| A | B | A AND B |
|---|---|---|
| Y | Y | Yes |
| Y | N | No |
| N | Y | No |
| N | N | No |

**OR** — at least one condition must be true.

| A | B | A OR B |
|---|---|---|
| Y | Y | Yes |
| Y | N | Yes |
| N | Y | Yes |
| N | N | No |

As a QA, understanding these combinations is important.

---

*End of Day 10 guide*