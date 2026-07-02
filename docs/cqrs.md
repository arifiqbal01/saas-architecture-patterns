# Command Query Responsibility Segregation (CQRS)

## Overview

Command Query Responsibility Segregation (CQRS) is an architectural pattern that separates **write operations (Commands)** from **read operations (Queries)**.

Instead of using a single model for both reading and writing data, CQRS allows each side to be optimized for its specific purpose.

CQRS does **not** require separate databases or microservices. It can be applied within a modular monolith using independent write and read models.

---

## Goals

CQRS aims to:

- Separate business logic from query logic.
- Optimize read and write operations independently.
- Simplify complex business workflows.
- Improve scalability for read-heavy applications.
- Reduce coupling between domain models and UI requirements.

---

## Core Concepts

### Command

A Command represents an intention to change the system.

Examples include:

- Create
- Update
- Delete
- Execute an action

Commands:

- modify state
- execute business rules
- may fail if business rules are violated

Commands are handled by the write side of the application.

---

### Query

A Query retrieves information without modifying the system.

Queries:

- never change state
- return data optimized for presentation
- do not execute business rules

Queries are handled by the read side.

---

### Write Model

The write model is responsible for maintaining business consistency.

Responsibilities include:

- enforcing business rules
- validating invariants
- modifying aggregates
- raising domain events

The write model is typically implemented using Domain-Driven Design.

---

### Read Model

The read model is optimized for retrieving data efficiently.

Unlike the write model, it may:

- denormalize data
- aggregate information
- reshape data for user interfaces

Read models are designed for fast queries rather than enforcing business rules.

---

## CQRS Flow

A typical CQRS flow looks like this:

```text
          Command
             │
             ▼
        Application
             │
             ▼
          Domain
             │
             ▼
       Persist Changes
             │
             ▼
       Domain Events
             │
             ▼
       Update Read Model

-------------------------------

            Query
              │
              ▼
         Read Model
              │
              ▼
          Client / UI
```

---

## Benefits

Separating reads and writes provides several advantages:

- Cleaner business models
- Faster and simpler queries
- Independent optimization of reads and writes
- Reduced complexity in large systems
- Better alignment with event-driven architectures

---

## CQRS and Domain Events

CQRS is commonly used together with Domain Events.

A typical sequence is:

1. A Command modifies the Domain.
2. The Domain raises one or more Domain Events.
3. Event handlers update one or more Read Models.
4. Clients query the updated Read Models.

This approach keeps the write model focused on business behavior while allowing the read model to evolve independently.

---

## CQRS in a Modular Monolith

CQRS can be implemented without distributed systems.

A common approach is:

```text
Client
   │
   ▼
Application
   │
   ▼
Domain
   │
   ▼
Database

──────────────

Client
   │
   ▼
Read Model
   │
   ▼
Database / View
```

Both sides may share the same physical database while remaining logically independent.

---

## When to Use CQRS

CQRS is most beneficial when:

- business logic is complex
- read and write requirements differ
- the application is event-driven
- different views require different data shapes

For small CRUD applications, a single model is often sufficient.

---

## Relationship with Domain-Driven Design

Domain-Driven Design focuses on protecting business rules.

CQRS complements DDD by allowing:

- the write model to remain focused on business behavior
- the read model to focus on efficient data retrieval

Together they provide a clear separation between decision-making and data presentation.

---

## References

- Greg Young — *CQRS*
- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*