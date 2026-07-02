# Dependency Injection (DI)

## Overview

Dependency Injection (DI) is a design pattern that provides an object's dependencies from the outside rather than allowing it to create them itself.

Its primary purpose is to reduce coupling between application components, making the system easier to test, maintain, and evolve.

In a Hexagonal Architecture, Dependency Injection enables the Domain and Application layers to remain independent of Infrastructure.

---

## Goals

Dependency Injection aims to:

- Reduce coupling between components.
- Improve testability.
- Support interchangeable implementations.
- Keep business logic independent of infrastructure.
- Centralize dependency configuration.

---

## Core Concepts

### Dependency

A dependency is any component another component requires to perform its work.

Examples include:

- Repository implementations
- External service clients
- Message buses
- Configuration providers

A component should depend on **abstractions**, not concrete implementations.

---

### Injection

Instead of creating dependencies internally, they are provided from the outside.

```text
❌ Creates dependency internally

Application Service
        │
        ▼
New Repository()

────────────────────────

✅ Dependency injected

Repository Implementation
        │
        ▼
Application Service
```

This keeps components focused on their own responsibilities.

---

### Inversion of Control

Dependency Injection is a form of **Inversion of Control (IoC)**.

Rather than deciding which implementation to use, components declare what they need.

A central composition mechanism decides which implementation to provide.

---

## Composition Root

The Composition Root is the single place where dependencies are created and connected.

Typical responsibilities include:

- Creating repositories
- Creating external service clients
- Registering event handlers
- Configuring application services

A common structure is:

```text
bootstrap/

├── containers/
├── wiring/
└── application.py
```

Business logic should never perform dependency wiring.

---

## Dependency Direction

Dependencies should always point toward the Domain.

```text
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

The Domain does not know which database, framework, or external provider is being used.

---

## Benefits

Applying Dependency Injection provides several advantages:

- Loose coupling
- Easier testing
- Replaceable infrastructure
- Clear separation of concerns
- Better maintainability

Changing an infrastructure implementation should not require changes to business logic.

---

## Testing

Dependency Injection makes testing straightforward.

During testing, real infrastructure can be replaced with lightweight alternatives such as:

- Test repositories
- Fake services
- Mock implementations
- In-memory adapters

This allows business logic to be tested independently of external systems.

---

## Relationship with Hexagonal Architecture

Hexagonal Architecture defines **where dependencies should point**.

Dependency Injection provides **the mechanism** for connecting those dependencies at runtime.

Together they ensure that:

- The Domain remains infrastructure-independent.
- The Application coordinates business workflows.
- Infrastructure can be replaced without affecting business logic.

---

## Best Practices

- Depend on abstractions, not implementations.
- Keep dependency wiring in one place.
- Avoid creating infrastructure inside business logic.
- Inject dependencies through constructors or application composition.
- Keep the Domain unaware of infrastructure details.

---

## References

- Martin Fowler — *Inversion of Control Containers and the Dependency Injection Pattern*
- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*