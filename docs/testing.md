# Testing Strategy

## Overview

The testing strategy follows the architectural boundaries of the application.

Each Bounded Context owns its own test suite, allowing business capabilities to be tested independently while minimizing coupling between modules.

Tests are organized to validate business behavior first, followed by application workflows and infrastructure integrations.

---

## Goals

The testing strategy aims to:

- Validate business rules independently.
- Keep tests isolated and maintainable.
- Mirror the application architecture.
- Test each layer according to its responsibility.
- Build confidence through incremental testing.

---

## Test Pyramid

```text
              End-to-End
           Integration Tests
       Application Layer Tests
          Domain Unit Tests
```

Business rules are tested at the lowest level, while broader system behavior is verified through a smaller number of integration and end-to-end tests.

---

## Test Organization

Tests follow the same structure as the application.

```text
tests/

├── identity/
├── inbox/
├── channels/
└── shared/
```

Each Bounded Context owns its own test suite.

Within a context:

```text
tests/inbox/

├── domain/
├── application/
├── infrastructure/
└── integration/
```

This structure keeps tests aligned with architectural boundaries.

---

## Domain Tests

Domain tests verify business behavior.

Typical characteristics:

- Fast execution
- Pure business logic
- No database
- No HTTP
- No external services
- No framework dependencies

These tests provide the highest confidence at the lowest cost.

---

## Application Tests

Application tests verify use case orchestration.

Typical responsibilities include validating:

- Workflow execution
- Transaction boundaries
- Repository coordination
- Event publication

Business rules remain the responsibility of the Domain.

---

## Infrastructure Tests

Infrastructure tests verify technical integrations.

Examples include:

- Repository implementations
- Persistence mapping
- External service adapters
- API integrations
- Messaging components

These tests ensure infrastructure correctly implements the contracts defined by higher layers.

---

## Integration Tests

Integration tests verify that multiple layers work together correctly.

Typical scenarios include:

- Persistence operations
- Dependency wiring
- Event-driven workflows
- Cross-layer interactions

Integration tests provide confidence that architectural components collaborate as expected.

---

## Test Isolation

Each Bounded Context manages its own test configuration, fixtures, and dependencies.

This approach:

- prevents cross-context coupling
- simplifies maintenance
- improves test readability
- supports independent evolution of modules

---

## Architectural Principles

The testing strategy follows several principles:

- Test business behavior before infrastructure.
- Keep tests close to the code they verify.
- Isolate Bounded Contexts.
- Prefer many fast tests over few slow tests.
- Mirror the application architecture.

---

## Summary

Testing is organized around architectural boundaries rather than technical layers.

By aligning tests with Bounded Contexts and application layers, the system remains maintainable, scalable, and easier to evolve as new business capabilities are introduced.

---

## References

- Eric Evans — *Domain-Driven Design: Tackling Complexity in the Heart of Software*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*