+++
title: "Distributed Transactions: Understanding Two-Phase Commit"
date: 2026-02-18
draft: false
tags: ["transactions", "2PC", "databases", "consistency", "backend"]
categories: ["Databases", "Backend"]
description: "A beginner-friendly guide to transactions, focusing on the two-phase commit protocol for distributed systems."


[cover]
image = "https://images.unsplash.com/photo-1581091870627-3f89b4c5c9e5?auto=format&fit=crop&w=1600&q=80"
alt = "Distributed systems network illustration"
caption = "Distributed transactions and Two-Phase Commit"
relative = false
+++

# Introduction

In distributed systems and modern databases, maintaining **data consistency** is critical. This post introduces the concept of **transactions**, explains **ACID properties**, and dives into the **Two-Phase Commit (2PC) protocol** to ensure reliable distributed transactions.

---

## What is a Transaction?

A transaction is a **sequence of operations** performed as a single unit of work. Transactions are designed to be **atomic, consistent, isolated, and durable (ACID)**:

- **Atomic**: All operations succeed or none.  
- **Consistent**: Database moves from one valid state to another.  
- **Isolated**: Concurrent transactions don’t interfere.  
- **Durable**: Changes are permanent once committed.

---

## Challenges in Distributed Systems

- Multiple databases or nodes can be involved.  
- Partial failures can leave the system in an inconsistent state.  
- Simple commit/rollback is not enough when operations span multiple systems.

---

## Two-Phase Commit (2PC)

The **Two-Phase Commit protocol** solves these problems by coordinating distributed transactions in **two phases**:

1. **Prepare Phase**:  
   - The coordinator asks all participants if they are ready to commit.  
   - Each participant responds with `Yes` (ready) or `No` (abort).

2. **Commit Phase**:  
   - If all participants said `Yes`, the coordinator sends a **commit command**.  
   - If any participant said `No`, the coordinator sends an **abort command**.

---

## Example Workflow

```text
Coordinator -> Participant1: Prepare
Coordinator -> Participant2: Prepare
Participant1 -> Coordinator: Yes
Participant2 -> Coordinator: Yes
Coordinator -> Participant1: Commit
Coordinator -> Participant2: Commit
