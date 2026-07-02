# Domain-Driven Design (DDD)

## Overview

Domain-Driven Design (DDD) is an approach to software architecture that organizes a system around **business capabilities** rather than technical layers or frameworks.

Instead of asking:

> "How should we structure the code?"

DDD asks:

> "How does the business think about this problem?"

The resulting software reflects the language, rules, and boundaries of the domain it represents.

---

## Goals

Domain-Driven Design aims to:

- Keep business logic independent of infrastructure.
- Reduce complexity through clear boundaries.
- Improve communication between technical and non-technical stakeholders.
- Make large systems easier to evolve over time.
- Enable teams to work independently on different business capabilities.

---

## Core Concepts

### Ubiquitous Language

Every business capability should have a shared language used consistently across:

- Documentation
- Code
- Discussions
- APIs

Using a consistent vocabulary reduces ambiguity and helps the code accurately represent the domain.

---

### Bounded Context

A Bounded Context defines the boundary where a particular domain model is valid.

Each context owns:

- its own language
- its own business rules
- its own data model
- its own implementation

Contexts communicate through well-defined contracts instead of sharing internal models.

---

### Domain Model

The Domain Model represents the core business concepts and behaviors.

It contains:

- Entities
- Value Objects
- Aggregates
- Domain Services
- Domain Events

The Domain Model should remain independent of:

- databases
- web frameworks
- messaging systems
- external APIs

---

### Strategic Design

Strategic Design focuses on the relationships between different business capabilities.

Its purpose is to define:

- system boundaries
- ownership
- integration points
- communication patterns

---

### Tactical Design

Tactical Design focuses on implementing an individual domain model.

Common building blocks include:

- Entities
- Value Objects
- Aggregates
- Domain Events
- Repositories
- Domain Services

---

## Architectural Principles

This repository follows several principles inspired by Domain-Driven Design.

### Business First

The system is organized around business capabilities rather than technical concerns.

---

### Independent Models

Each Bounded Context owns its own model.

Models are not shared across context boundaries.

---

### Explicit Communication

Contexts communicate through:

- Domain Events
- Explicit APIs
- Published contracts

Direct coupling between contexts should be avoided.

---

### Framework Independence

Business logic should not depend on infrastructure.

The Domain layer should remain free of:

- HTTP
- ORM frameworks
- external SDKs
- messaging implementations

---

## Typical Structure

```text
Bounded Context

├── application/
├── domain/
└── infrastructure/
```

### Domain

Contains business rules.

### Application

Coordinates use cases.

### Infrastructure

Implements communication with the outside world.

---

## Benefits

Applying Domain-Driven Design helps:

- reduce coupling
- improve maintainability
- isolate complexity
- support long-term evolution
- enable incremental architectural growth

---

## Relationship with Hexagonal Architecture

Domain-Driven Design defines **how the business is modeled**.

Hexagonal Architecture defines **how that model interacts with external systems**.

These two approaches complement each other and are commonly used together.

---

## References

- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*