# Day 15 — Test Data & Positive/Negative Testing

## 1. What Is Test Data?

Test Data is the information we use to execute a test case.

For a login page:

```
Email:    alkesh@gmail.com
Password: 1234
```

Both are test data.

Other examples:

| Feature | Test Data |
|---|---|
| Login | Email, password |
| Registration | Name, email, password |
| Payment | Card number, expiry, CVV |
| Search | Search keywords |
| Return product | Order ID, product ID |
| Signup | Username, email, phone |

---

## 2. Types of Test Data

### Valid Test Data

Data that should be accepted by the system.

**Example**

```
Email: alkesh@gmail.com
Password: 1234
```

Expected: Login successful

### Invalid Test Data

Data that should be rejected.

**Example**

```
Email: alkesh@gmail
```

Expected: Login should not be successful

### Empty / Missing Data

Testing when a required field is left empty.

**Example**

```
Email: [empty]
Password: 1234
```

Expected: Validation message should appear

### Boundary Data

Data around the allowed limits.

Suppose password requirements are: minimum = 8 characters, maximum = 20 characters.

Good test data:

```
7 characters   → Invalid
8 characters   → Valid
9 characters   → Valid
20 characters  → Valid
21 characters  → Invalid
```

This connects directly to the Boundary Value Analysis you learned earlier. 

---

## 3. Positive Testing

Positive testing checks whether the system works correctly with valid input.

**Example:** Login with a registered email and correct password.

```
Email:    alkesh@gmail.com
Password: 1234
```

Expected: User successfully logs in.

> Think: "Give the system what it expects."

---

## 4. Negative Testing

Negative testing checks whether the system handles invalid or unexpected input correctly.

**Example:** Login with an incorrect password.

```
Email:    alkesh@gmail.com
Password: wrong123
```

Expected: Login should fail.

> Think: "Give the system something it shouldn't accept."

---

## 5. Positive vs Negative

| Positive | Negative |
|---|---|
| Valid email | Invalid email |
| Correct password | Wrong password |
| Required field filled | Required field empty |
| Valid card | Expired card |
| Valid age | Age below allowed limit |
| Valid order ID | Invalid order ID |

A good QA engineer needs both.

---

## Important QA Mindset

Don't just ask: *"Does it work?"*

Ask: *"What happens if I give it something wrong?"*

For example, a login system may work perfectly with `user@gmail.com` / `password123`. But what happens with:

```
""
" "
abc
abc@
123
very-long-input........
```

That's where bugs often appear.

---

*End of Day 15 guide*