# 1. What is Scalability?

Scalability refers to a system's ability to handle increased workload (e.g., more users, requests, or data) without compromising performance, reliability, or efficiency. A scalable system can grow seamlessly by adding resources (like servers, storage, or bandwidth) to accommodate higher demand.

### Types of Scalability

- Vertical scaling
- Horizontal scaling

---

# 2. What is Availability?

Availability refers to a system's ability to remain operational and accessible to users over a given period, despite failures (hardware crashes, network issues, software bugs, etc.). It is often measured as a percentage of uptime in a year (e.g., "99.9% availability").

---

# 3. What is Consistency?

Consistency means everyone sees the same information at the same time. There are two types of consistency

- Strong consistency
- Eventual consistency

### What is a Strong consistency?

Strong consistency means consistent/same data visible to everyone **immediately, without any delay.**

## 🏦 Strong Consistency in Banking

## ✅ Example: Bank Account Balance

### Scenario:

- A customer has ₹10,000 in their savings account.
- They initiate an **online transfer of ₹5,000** to another account.

### With Strong Consistency:

1. The banking system **updates the balance** to ₹5,000 immediately after the transfer.
2. If the customer **refreshes their balance** or accesses their account from another device:
   - They will **immediately see ₹5,000**.
3. No part of the system shows the old balance of ₹10,000 after the transaction.

---

## 🛡️ Why It Matters in Banking:

- Prevents **double spending** or overdrafts.
- Maintains **trust and accuracy** in financial transactions.
- Ensures **regulatory compliance** by always showing the most recent data.

---

## 🔁 Without Strong Consistency (e.g., Eventual Consistency):

- After the transfer, one system might still show ₹10,000 for a short time.
- This could lead to:
  - **Confusion** for the user.
  - **Incorrect decisions**, like initiating another transfer based on stale data.

---

## 🧠 Conclusion:

> In banking, **strong consistency is crucial** to ensure the correctness of critical operations like balance checks, fund transfers, and withdrawals.

---

## What is Eventual Consistency?

Eventual consistency means data will become consistent over time, but not necessarily instantly.

### 🔄 Eventual Consistency in Banking

---

## 🏦 Example: Transaction History in a Distributed Banking System

### Scenario:

- A user transfers ₹2,000 from their account using the mobile app.
- The transaction is processed and recorded on the **primary database** (Region A).
- The user's account is **replicated to other regions** (Region B, Region C).

### With Eventual Consistency:

1. The transaction shows up **immediately** in Region A.
2. If the user logs in from a different location (e.g., another app/server using Region B) **just after the transfer**:
   - They might **not see the latest ₹2,000 transaction** in their transaction history.
3. After a few seconds or minutes (when replication is complete), the transaction **appears everywhere**.

---

## 🧭 Where It's Acceptable in Banking:

- **Non-critical operations**:
  - Transaction history list
  - Notification systems
  - Analytics dashboards
- Used where **slight delay is tolerable** and doesn’t affect money flow or correctness.

---

## ⚠️ Risks Without Strong Consistency:

- Temporary **inconsistencies** in reports or UI.
- Confusing UX if a user doesn't see recent actions instantly

---

# 4. Single Point of Failure (SPOF)

## 🧠 Definition

A **Single Point of Failure (SPOF)** is a **part of a system** that, if it fails, **will stop the entire system from working**. It represents a **critical vulnerability** in the system's architecture.

---

## 🔧 Real-World Example: Banking Server

- Imagine a bank has **one main server** handling **all online transactions**.
- If that server goes **offline** due to a crash or power failure:
  - **All online banking services stop** working.
  - Users cannot transfer money, check balances, or pay bills.

👉 That **server** is a **Single Point of Failure**.

---

## 🚨 Why SPOFs are Dangerous

- Causes **complete service outages**.
- Leads to **loss of revenue** and **customer trust**.
- Becomes a **target** for attackers (e.g., DDoS attacks).

---

## 🛡️ How to Avoid SPOFs

| Strategy             | Description                                       |
| -------------------- | ------------------------------------------------- |
| Redundancy           | Use multiple servers or components.               |
| Load Balancing       | Distribute traffic to avoid overloading one node. |
| Failover Mechanisms  | Switch to backup systems automatically.           |
| Cloud Infrastructure | Use distributed cloud services (e.g., AWS, GCP).  |

---

## 🧠 Conclusion

> A **Single Point of Failure** is any **critical part of a system** that can bring everything down if it fails. Designing for **fault tolerance and high availability** is key to avoiding SPOFs.
