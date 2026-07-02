# Application Layer

## Overview

The Application layer coordinates the execution of business use cases.

It acts as the bridge between external requests and the Domain Model by orchestrating workflows, managing transactions, and interacting with infrastructure through Ports.

The Application layer contains **application-specific logic**, not business rules.

---

## Responsibilities

The Application layer is responsible for:

- Executing use cases.
- Coordinating workflows.
- Managing transaction boundaries.
- Loading and persisting aggregates.
- Publishing Domain Events.
- Mapping data between external interfaces and the Domain.

The Application layer should **not** contain business rules. Those belong in the Domain.

---

## Structure

```text
application/

├── commands/
├── dto/
├── ports/
├── queries/
├── services/
└── use_cases/
```

---

## Components

### Commands

Commands represent requests that modify the system.

A command expresses an intention to perform an action and is handled by a single use case.

---

### Queries

Queries retrieve information without modifying the system.

They are responsible only for reading data and preparing responses for consumers.

---

### DTO (Data Transfer Objects)

DTOs define the data exchanged between layers.

They isolate the Domain Model from external representations such as APIs or messaging contracts.

---

### Application Ports

Application Ports define interfaces used by the Application layer to communicate with external systems.

These interfaces are implemented by the Infrastructure layer.

---

### Application Services

Application Services coordinate multiple components to execute a business use case.

Typical responsibilities include:

- Loading aggregates
- Calling Domain methods
- Persisting changes
- Publishing Domain Events

Application Services should orchestrate behavior, not implement business rules.

---

### Use Cases

A Use Case represents a single business operation from the application's perspective.

Each Use Case should have one clear responsibility and coordinate the steps required to complete that operation.

---

## Typical Flow

```text
Client
    │
    ▼
Application
    │
Load Aggregate
    │
    ▼
Domain
    │
Business Rules
    │
    ▼
Persist Changes
    │
    ▼
Publish Domain Events
```

The Application layer coordinates the flow but delegates business decisions to the Domain.

---

## Dependency Rule

The Application layer depends on the Domain but not on Infrastructure implementations.

```text
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

Infrastructure dependencies are accessed through Ports.

---

## Design Principles

The Application layer should:

- Coordinate, not decide.
- Keep use cases focused and cohesive.
- Depend on abstractions rather than implementations.
- Remain independent of infrastructure details.
- Delegate business rules to the Domain.

---

## Summary

The Application layer orchestrates business workflows by connecting external requests with the Domain Model.

It manages application flow while ensuring that business logic remains encapsulated within the Domain.