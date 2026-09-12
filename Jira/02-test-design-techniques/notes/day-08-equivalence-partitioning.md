# Day 8 — Equivalence Partitioning

Now we're moving from "What is testing?" to "How does a tester decide what to test?" This is a major step toward the practical workflow you've been asking about.

## Phase 2 Roadmap

- **Day 8** → Equivalence Partitioning
- **Day 9** → Boundary Value Analysis
- **Day 10** → Decision Table Testing
- **Day 11** → State Transition Testing
- **Day 12** → Use Case Testing + Error Guessing

↓

 Practical Manual QA Project

Today we'll start with Day 8 — Equivalence Partitioning (EP).

---

## 1. The Problem

Imagine you have a registration form.

> Requirement: Age must be between 18 and 60.

Possible inputs include: 1, 2, 3 ... 18, 19, 20 ... 60, 61, 62, 63 ... 100

Do we need to test every possible age?

 No. That would be inefficient.

Instead, we divide the possible inputs into groups where we expect the system to behave similarly. These groups are called **equivalence partitions**.

---

## 2. What Is Equivalence Partitioning?

> Equivalence Partitioning is a test design technique where input data is divided into groups (partitions) that are expected to behave similarly.

The idea is: if one value from a partition behaves correctly, other values from that same partition are expected to behave similarly. Therefore, instead of testing every value, we select representative values.

---

## 3. Simple Example

> Requirement: Age must be between 18 and 60.

We can divide the input into three partitions:

- **Partition 1** — Age < 18 → INVALID
- **Partition 2** — 18 ≤ Age ≤ 60 → VALID
- **Partition 3** — Age > 60 → INVALID

Visually:

```
          INVALID        VALID         INVALID
-----------|=========================|-----------
           18                         60
        below 18                   above 60
```

We can select one representative value from each:

| Partition | Example Value | Expected |
|---|---|---|
| Age < 18 | 15 | Reject |
| 18–60 | 30 | Accept |
| Age > 60 | 70 | Reject |

Instead of testing dozens of ages, we've selected 3 representative cases.

---

## 4. Why Does This Work?

The assumption is that values within the same partition should behave similarly.

For example, 15, 16, and 17 are all in the "Age < 18" partition. If the system rejects 15, we'd generally expect it to reject 16 and 17 as well.

Likewise, 25, 35, 45, and 55 are all within the valid partition — we don't necessarily need to test every one.

---

## 5. Valid vs Invalid Partitions

This is one of the most important things to understand.

**Valid partition** — contains inputs that should be accepted. Example: 18–60

**Invalid partition** — contains inputs that should be rejected. Example: below 18, above 60

```
Requirement: Age = 18–60

       VALID
   ┌───────────────┐
   │     18–60     │
   └───────────────┘
      ↑         ↑
 INVALID       INVALID
   <18            >60
```

---

## 6. Another Example — Password Length

> Requirement: Password must contain 8–20 characters.

Partitions:

- **Partition 1** — Less than 8 characters → INVALID
- **Partition 2** — 8–20 characters → VALID
- **Partition 3** — More than 20 characters → INVALID

Representative test data:

| Partition | Input | Expected |
|---|---|---|
| < 8 | `abc123` | Reject |
| 8–20 | `abc12345` | Accept |
| > 20 | `abcdefghijklmnopqrstu` | Reject |

Again, we're reducing a huge number of possible inputs into meaningful groups.

---

## 7. Another Example — E-commerce Quantity

> Requirement: A customer can purchase 1–10 items.

Partitions:

- Quantity < 1 → INVALID
- Quantity 1–10 → VALID
- Quantity > 10 → INVALID

Representative values:

| Partition | Example | Expected |
|---|---|---|
| < 1 | 0 | Reject |
| 1–10 | 5 | Accept |
| > 10 | 11 | Reject |

---

## Important: EP Doesn't Mean "Only 3 Test Cases"

This is a common beginner misunderstanding.

If you identify `< 18`, `18–60`, `> 60`, you've identified 3 partitions. You might choose one representative value from each partition for a basic EP test.

But in a real project, you may need additional tests based on:

- Risk
- Business rules
- Different data types
- Other conditions
- Boundary values
- Security requirements

And that's exactly why Boundary Value Analysis comes next.

---

## EP vs Normal Guessing

Without a technique, a beginner might test: 18, 25, 30, 35, 40, 45, 50, 55, 60

Why these numbers? *"They look reasonable."*

That's not a systematic approach.

With Equivalence Partitioning, we think: *what groups of inputs should behave similarly?*

```
<18      → invalid
18–60    → valid
>60      → invalid
```

Now our test selection has a reason behind it. That's what test design techniques give you.

---

## 8. EP With Different Input Types

Equivalence Partitioning isn't only for numbers. It can be used for:

**Email**

> Requirement: User must enter a valid email address.

Possible partitions: valid email, invalid email, empty email.

| Input | Result |
|---|---|
| `user@gmail.com` | Valid |
| `usergmail.com` | Invalid |
| *(empty string)* | Empty |

**Login**

> Requirement: Only registered users can log in.

Partitions: registered user, unregistered user, empty credentials.

**File Upload**

> Requirement: Only PDF files under 5 MB are accepted.

Possible partitions:

- Valid PDF < 5 MB
- PDF > 5 MB
- Non-PDF file < 5 MB
- Non-PDF file > 5 MB

Notice something important: a requirement can have more than three partitions. You identify partitions based on the different expected behaviors.

---

## 9. The Core Question

Whenever you see a requirement, ask:

> "Can I divide the possible inputs into groups that should behave similarly?"

If yes → Equivalence Partitioning may be useful.

---

## Practical QA Example

Let's take the requirement we've already been using:

> Customers can return a delivered product within 7 days of delivery.

Possible partitions:

- **Partition 1 — Before/within allowed period:** Return ≤ 7 days → VALID
- **Partition 2 — After allowed period:** Return > 7 days → INVALID

| Partition | Example | Expected |
|---|---|---|
| Valid | Day 5 | Return accepted |
| Invalid | Day 10 | Return rejected |

But there's something interesting here... what about **Day 7**?

That's where Boundary Value Analysis becomes extremely useful. We'll study that tomorrow.

---

## EP vs Boundary Value Analysis

Don't confuse them.

**Equivalence Partitioning** — focuses on groups of inputs. Example: `<18`, `18–60`, `>60`

**Boundary Value Analysis** — focuses on the edges of those groups. Example: `17, 18, 19` and `59, 60, 61`

```
EP
  ↓
Identify partitions

BVA
  ↓
Test the boundaries
```

They are often used together.

---

*End of Day 8 guide*