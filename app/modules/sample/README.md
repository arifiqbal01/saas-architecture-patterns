# Sample Bounded Context

This module demonstrates the internal structure of a single **Bounded Context** in a Domain-Driven Design (DDD) application.

It is intentionally generic and does not represent a real business domain. Its purpose is to illustrate how business logic can be organized using DDD and Hexagonal Architecture.

## Structure

```text
sample/

├── application/
├── domain/
└── infrastructure/
```

### Domain

Contains the business model and rules.

Examples:

- Entities
- Value Objects
- Domain Events
- Repository Ports
- Domain Services

The Domain is independent of frameworks, databases, and external services.

---

### Application

Coordinates business use cases.

Responsibilities include:

- Executing commands
- Coordinating workflows
- Managing transactions
- Publishing domain events

The Application layer orchestrates business operations but does not contain business rules.

---

### Infrastructure

Implements communication with the outside world.

Examples include:

- Database repositories
- HTTP APIs
- External service adapters
- Message brokers

Infrastructure depends on the Domain through interfaces (Ports).

---

## Dependency Direction

```
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

Dependencies always point inward. The Domain never depends on infrastructure.

---

This folder exists solely to demonstrate architectural organization and does not contain production business logic.