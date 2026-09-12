# Day 9 — Boundary Value Analysis (BVA)

Yesterday we learned Equivalence Partitioning (EP):

> Divide inputs into groups that should behave similarly.

Today we're going one step further.

## The Key Idea

> Bugs frequently occur around the boundaries/edges of valid and invalid input ranges.

So instead of testing random values, we specifically test values around the boundary.

---

## 1. Simple Example

> Requirement: Age must be between 18 and 60.

From Equivalence Partitioning:

```
< 18       → INVALID
18–60      → VALID
> 60       → INVALID
```

The boundaries are 18 and 60. With Boundary Value Analysis, we test around those boundaries:

```
17   → INVALID
18   → VALID
19   → VALID

59   → VALID
60   → VALID
61   → INVALID
```

Our test values:

| Value | Expected |
|---|---|
| 17 | Reject |
| 18 | Accept |
| 19 | Accept |
| 59 | Accept |
| 60 | Accept |
| 61 | Reject |

This is the classic 3-value approach around each boundary: **Boundary − 1, Boundary, Boundary + 1**

---

## 2. Why Do We Test Boundaries?

Imagine a developer writes:

```python
if age > 18:
    allow()
```

But the requirement says: *Age 18 and above is allowed.* The developer accidentally used `> 18` instead of `>= 18`.

What happens?

- 17 → Reject
- 18 → ❌ Reject (should be Accept)
- 19 → Accept

If we only tested 25, 30, and 40, we might never discover the problem. But BVA tells us: test 17, 18, 19. And we immediately find the defect.

---

## 3. BVA + Equivalence Partitioning

These two techniques work very well together.

> Requirement: Password must contain 8–20 characters.

**Step 1 — Equivalence Partitioning**

```
< 8       → INVALID
8–20      → VALID
> 20      → INVALID
```

**Step 2 — Identify boundaries**

8 and 20

**Step 3 — Apply BVA**

Around 8: `7 → Invalid`, `8 → Valid`, `9 → Valid`
Around 20: `19 → Valid`, `20 → Valid`, `21 → Invalid`

**Final test values:** 7, 8, 9, 19, 20, 21

---

## 4. Another Example — Product Quantity

> Requirement: Customer can purchase 1–5 products.

**EP:**

```
< 1       → INVALID
1–5       → VALID
> 5       → INVALID
```

**Boundaries:** 1 and 5

**BVA:**

```
0 → Reject
1 → Accept
2 → Accept

4 → Accept
5 → Accept
6 → Reject
```

---

## 5. Important: Boundary Doesn't Always Mean Numbers

BVA is easiest to understand with numeric ranges, but the underlying idea is about limits.

> Requirement: Username must contain 5–15 characters.

**Boundaries:** 5 and 15

Test:

```
4 characters  → Reject
5 characters  → Accept
6 characters  → Accept

14 characters → Accept
15 characters → Accept
16 characters → Reject
```

---

## 6. BVA for the Return-Period Example

Let's return to our practical QA example:

> Customers can return a product within 7 days of delivery.

The boundary is 7 days, so we'd want to test around it:

```
6 days → Accept
7 days → Accept
8 days → Reject
```

This is much better than only testing 3 days and 10 days, because the most important question is: *what happens exactly at the limit?*

---

## 7. The "Minimum / Maximum" Pattern

Whenever you see requirements like *"Between X and Y,"* immediately think:

```
Minimum
Minimum - 1
Minimum + 1

Maximum - 1
Maximum
Maximum + 1
```

**For 18–60:**

```
17
18
19

59
60
61
```

**For 1–5:**

```
0
1
2

4
5
6
```

**For 8–20 characters:**

```
7
8
9

19
20
21
```

---

## Easy Memory Trick

> EP asks: "What are the different groups?"
> BVA asks: "What happens at the edges of those groups?"

```
Requirement
     ↓
Equivalence Partitioning
     ↓
Find valid/invalid groups
     ↓
Boundary Value Analysis
     ↓
Test the edges
```

---

## 8. EP vs BVA

| Equivalence Partitioning | Boundary Value Analysis |
|---|---|
| Divides inputs into groups | Focuses on boundaries |
| Tests representative values | Tests values around limits |
| Reduces number of test cases | Targets edge-related defects |
| Example: `<18`, `18–60`, `>60` | Example: `17, 18, 19, 59, 60, 61` |

**Interview answer**

If someone asks: *"What is the difference between EP and BVA?"*

You can say: *Equivalence Partitioning divides input data into groups with similar expected behavior, while Boundary Value Analysis focuses on testing values at and around the boundaries of those groups.*

---

*End of Day 9 guide*