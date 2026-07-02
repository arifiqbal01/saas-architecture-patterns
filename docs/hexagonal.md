# Hexagonal Architecture (Ports & Adapters)

## Overview

Hexagonal Architecture, also known as **Ports and Adapters**, is an architectural style that isolates the core business logic from external technologies.

The primary goal is to ensure that the business domain remains independent of infrastructure such as databases, web frameworks, messaging systems, and third-party services.

Instead of the application depending directly on external systems, communication occurs through well-defined interfaces called **Ports**.

---

## Goals

Hexagonal Architecture aims to:

- Protect business logic from infrastructure changes.
- Improve testability through dependency inversion.
- Allow external technologies to be replaced with minimal impact.
- Promote clear separation of responsibilities.
- Support long-term maintainability.

---

## Core Concepts

### Domain

The Domain contains the core business model and business rules.

It should have no knowledge of:

- HTTP
- Databases
- ORMs
- External APIs
- Frameworks

The Domain represents the center of the application.

---

### Ports

Ports define how the Domain communicates with the outside world.

They are interfaces that describe required behavior without specifying implementation.

Typical examples include:

- Repository interfaces
- External provider interfaces
- Event bus interfaces

Ports belong to the Domain because they represent business requirements rather than technical implementations.

---

### Adapters

Adapters implement the Ports.

They translate between external systems and the Domain Model.

Examples include:

- Database repositories
- REST controllers
- AI providers
- Message brokers
- External APIs

Adapters belong to the Infrastructure layer.

---

## Dependency Rule

Dependencies always point toward the Domain.

```text
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

The Domain never imports or depends on Infrastructure.

This dependency direction allows infrastructure to evolve without affecting business logic.

---

## Layer Responsibilities

### Domain

Responsible for:

- Business rules
- Entities
- Value Objects
- Aggregates
- Domain Events
- Ports

Must remain independent of technical concerns.

---

### Application

Coordinates business use cases.

Responsibilities include:

- Executing workflows
- Managing transactions
- Loading aggregates
- Persisting changes
- Publishing events

The Application layer orchestrates work but does not contain business rules.

---

### Infrastructure

Provides implementations for external communication.

Typical responsibilities include:

- Database persistence
- HTTP APIs
- External services
- Messaging systems
- File storage

Infrastructure depends on the Domain through Ports.

---

## Request Flow

A typical request follows this path:

```text
Client
   │
   ▼
API Adapter
   │
   ▼
Application
   │
   ▼
Domain
   │
   ▼
Port
   │
   ▼
Infrastructure Adapter
   │
   ▼
External System
```

Business decisions occur inside the Domain.

Infrastructure is responsible only for communication and data translation.

---

## Benefits

Applying Hexagonal Architecture provides several advantages:

- Independent business logic
- Replaceable infrastructure
- Easier testing
- Reduced coupling
- Clear dependency direction
- Improved maintainability

---

## Relationship with Domain-Driven Design

Domain-Driven Design defines **how the business is modeled**.

Hexagonal Architecture defines **how the application communicates with external systems**.

DDD focuses on business concepts.

Hexagonal Architecture focuses on dependency management.

Together they create an architecture where business logic remains stable while infrastructure can evolve independently.

---

## References

- Alistair Cockburn — *Hexagonal Architecture*
- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*