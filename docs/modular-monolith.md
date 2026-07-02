# Modular Monolith

## Overview

A Modular Monolith is an architectural style where an application is developed as a **single deployable unit** while being organized into **independent business modules**.

Each module owns its own business model, application logic, and infrastructure, allowing the system to scale in complexity without becoming tightly coupled.

Unlike a traditional layered monolith, modules communicate through explicit interfaces or events rather than sharing internal implementation details.

---

## Goals

A Modular Monolith aims to:

- Organize software around business capabilities.
- Reduce coupling between modules.
- Keep deployment simple.
- Enable independent evolution of business modules.
- Prepare the system for future architectural growth.

---

## Core Concepts

### Business Modules

The application is divided into modules that represent business capabilities.

Each module owns its own:

- Domain
- Application
- Infrastructure

Modules should not expose their internal implementation.

---

### Single Deployment

Although the application contains multiple modules, it is deployed as a single application.

Benefits include:

- Simple deployment
- Single codebase
- Shared runtime
- Easier development workflow

---

### Explicit Communication

Modules communicate through explicit boundaries.

Typical integration mechanisms include:

- Domain Events
- Public application interfaces
- Published contracts

Direct access to another module's internal implementation should be avoided.

---

## Typical Structure

```text
app/

├── modules/
│   ├── module-a/
│   │   ├── application/
│   │   ├── domain/
│   │   └── infrastructure/
│   │
│   ├── module-b/
│   │   ├── application/
│   │   ├── domain/
│   │   └── infrastructure/
│   │
│   └── module-c/
│       ├── application/
│       ├── domain/
│       └── infrastructure/
│
├── api/
├── bootstrap/
└── shared/
```

---

## Dependency Direction

Each module follows the same dependency rule.

```text
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

Business modules should remain independent from one another.

---

## Benefits

A Modular Monolith provides several advantages:

- Clear business boundaries.
- Simpler deployment than distributed systems.
- Easier debugging.
- Lower operational complexity.
- Faster local development.
- Strong architectural consistency.

---

## Relationship with Domain-Driven Design

A Modular Monolith complements Domain-Driven Design.

DDD defines **how business capabilities are modeled**.

A Modular Monolith defines **how those capabilities are organized within a single application**.

Each Bounded Context naturally becomes an independent module.

---

## Evolution

A Modular Monolith is not an alternative to microservices.

Instead, it provides a stable foundation that allows individual modules to be extracted if operational requirements change.

Because each module owns its own model and dependencies, architectural evolution becomes significantly easier.

---

## When to Use

A Modular Monolith is well suited for systems that:

- contain multiple business capabilities
- expect long-term growth
- require clear architectural boundaries
- do not yet require distributed deployment

---

## Summary

A Modular Monolith combines the simplicity of a single application with the organizational benefits of modular design.

By organizing software around business capabilities and enforcing explicit boundaries, it enables systems to grow without sacrificing maintainability.

---

## References

- Eric Evans — *Domain-Driven Design: Tackling Complexity in the Heart of Software*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*