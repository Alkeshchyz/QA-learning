# Day 11 — State Transition Testing

## 1. What Is State Transition Testing?

> State Transition Testing is a test design technique used to test how a system behaves when it moves from one state to another because of an event or action.

The important words are:

```
State → Event → Transition → New State
```

For example, an online order can have different states:

```
Order Placed
  ↓
Payment Successful
  ↓
Confirmed
  ↓
Shipped
  ↓
Delivered
```

Each stage is a state.

---

## 2. What Is a State?

A state represents the current condition/status of the system.

**For an e-commerce order:**

- Placed
- Paid
- Confirmed
- Shipped
- Delivered
- Cancelled
- Returned
- Refunded

**For a user account:**

- Active
- Locked
- Suspended
- Deactivated

---

## 3. What Is an Event?

An event is something that causes the system to change state.

```
Order Placed
  ↓
Payment completed
  ↓
Order Confirmed
```

Here, *payment completed* = event, and *Placed → Confirmed* = state transition.

---

## 4. Simple Example — Login Account

Suppose a website locks an account after 3 consecutive failed login attempts.

```
Active
  ↓
1 failed login
  ↓
Failed attempt 1
  ↓
2 failed logins
  ↓
Failed attempt 2
  ↓
3 failed logins
  ↓
Locked
```

The states could be: Active, Failed Attempt 1, Failed Attempt 2, Locked

The events are: incorrect password, correct password

---

## 5. State Transition Diagram

We can visualize it:

```
                Correct Login
             ┌───────────────┐
             │               ↓
        ┌────────┐       ┌────────┐
        │ Active │       │ Active │
        └───┬────┘       └────────┘
            │
       Wrong password
            ↓
   ┌──────────────────┐
   │ Failed Attempt 1 │
   └────────┬─────────┘
            │
       Wrong password
            ↓
   ┌──────────────────┐
   │ Failed Attempt 2 │
   └────────┬─────────┘
            │
       Wrong password
            ↓
       ┌────────┐
       │ Locked │
       └────────┘
```

The diagram helps us understand what should happen after each event.

---

## 6. Why Is This Useful for QA?

A normal test might check: *"Can the user log in?"*

But State Transition Testing asks: *"What happens after different sequences of actions?"*

For example:

- Wrong password → Wrong password → Wrong password → Account should become **Locked**
- Wrong password → Correct password → Account should become **Active / Logged in**

The sequence matters. That's what makes state transition testing different from the techniques we've already learned.

---

## 7. Real Example — E-commerce Order

Let's use our familiar e-commerce application.

Possible states:

```
Placed
  ↓
Paid
  ↓
Confirmed
  ↓
Shipped
  ↓
Delivered
```

There can also be another path:

```
Placed
  ↓
Cancelled
```

And after delivery:

```
Delivered
  ↓
Return Requested
  ↓
Return Approved
  ↓
Refunded
```

So the overall workflow might look like:

```
                 ┌───────────┐
                 │  Placed   │
                 └─────┬─────┘
                       │
              Payment successful
                       ↓
                 ┌───────────┐
                 │   Paid    │
                 └─────┬─────┘
                       │
                       ↓
                ┌────────────┐
                │ Confirmed  │
                └──────┬─────┘
                       │
                       ↓
                 ┌──────────┐
                 │ Shipped  │
                 └────┬─────┘
                      │
                      ↓
                ┌───────────┐
                │ Delivered │
                └─────┬─────┘
                      │
                 Return request
                      ↓
               ┌──────────────┐
               │Return Request│
               └──────┬───────┘
                      │
                      ↓
                 ┌──────────┐
                 │ Refunded │
                 └──────────┘
```

---

## 8. Valid Transitions

A valid transition is a state change that the system should allow.

Example: `Placed → Paid` if payment succeeds.

Or: `Delivered → Return Requested` if the return conditions are satisfied.

---

## 9. Invalid Transitions

This is where QA becomes interesting.

We also need to test transitions that should **not** happen.

- `Delivered → Shipped` ❌ Should not happen. An order that has already been delivered shouldn't suddenly become shipped again.
- `Cancelled → Shipped` ❌ Should not happen. A cancelled order shouldn't be shipped.

So we don't only test *"What should happen?"* — we also test *"What should NOT happen?"*

---

## 10. State Transition Table

Instead of a diagram, we can use a table.

| Current State | Event | Expected Next State |
|---|---|---|
| Placed | Payment successful | Paid |
| Placed | Customer cancels | Cancelled |
| Paid | Order confirmed | Confirmed |
| Confirmed | Shipment created | Shipped |
| Shipped | Product delivered | Delivered |
| Delivered | Valid return request | Return Requested |
| Return Requested | Refund processed | Refunded |

This table can directly help us create test cases.

---

## 11. State Transition Test Cases

From this:

| Current State | Event | Expected State |
|---|---|---|
| Placed | Payment successful | Paid |
| Placed | Cancel | Cancelled |
| Paid | Confirm | Confirmed |

we can create:

**Test Case 1**
- Initial State: Placed
- Action: Complete payment
- Expected: Order moves to Paid

**Test Case 2**
- Initial State: Placed
- Action: Cancel order
- Expected: Order moves to Cancelled

**Test Case 3**
- Initial State: Cancelled
- Action: Attempt payment
- Expected: Payment should not be accepted; order should remain Cancelled

That third one is particularly important because we're testing an invalid transition.

---

## 12. State Transition vs Decision Table

Don't confuse these.

**Decision Table** — focus: combination of conditions. Example: Premium? + Coupon?

**State Transition** — focus: change from one state to another based on events/actions. Example: `Placed → Paid → Shipped → Delivered`

**Memory trick:**

```
Decision Table
     ↓
CONDITIONS

State Transition
     ↓
STATES + EVENTS
```

---

## 13. State Transition vs BVA

Again:

**BVA** — Age: `17 → 18 → 19`. Focus = boundary.

**State Transition:**

```
Active
  ↓ wrong password
Failed Attempt 1
  ↓ wrong password
Failed Attempt 2
  ↓ wrong password
Locked
```

Focus = state changes and sequences.

---

## 14. Where You'll Actually Use This

As a QA, you'll encounter state transitions everywhere.

- **Login:** `Active → Failed → Locked`
- **Order:** `Placed → Paid → Shipped → Delivered`
- **Payment:**
  ```
  Initiated → Processing → Successful
                          ↓
                        Failed
  ```
- **Return:** `Requested → Approved → Returned → Refunded`
- **Account:** `Active → Suspended → Deactivated`

This is why this technique is worth learning.

---

## The Core Formula

Remember:

```
CURRENT STATE
      +
     EVENT
      ↓
EXPECTED NEXT STATE
```

Example:

```
Delivered
    +
Valid return request
    ↓
Return Requested
```

---

*End of Day 11 guide*