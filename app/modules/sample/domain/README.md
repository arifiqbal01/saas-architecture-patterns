# Domain Layer

## Overview

The Domain layer contains the core business model and business rules of a Bounded Context.

It represents **what the business does**, independent of how the application is delivered or how data is stored.

The Domain is the most stable part of the system and should remain free of technical concerns such as databases, web frameworks, messaging systems, or external APIs.

---

## Responsibilities

The Domain is responsible for:

- Defining business concepts.
- Enforcing business rules.
- Protecting invariants.
- Modeling business behavior.
- Raising Domain Events.

The Domain does **not** coordinate workflows or communicate with external systems.

---

## Structure

```text
domain/

├── entities/
├── value_objects/
├── events/
├── ports/
├── services/
└── exceptions.py
```

---

## Components

### Entities

Entities represent business objects with identity.

Their identity remains the same even when their attributes change.

Entities encapsulate business behavior and protect their own invariants.

---

### Value Objects

Value Objects describe concepts that are defined entirely by their attributes.

They are immutable and contain no identity.

Value Objects help express the domain language while reducing accidental complexity.

---

### Domain Events

Domain Events represent important business facts that have already occurred.

They allow other parts of the system to react without introducing direct dependencies.

The Domain raises events but does not publish them.

---

### Ports

Ports define the contracts required by the Domain.

They describe what the Domain needs from the outside world without specifying how those dependencies are implemented.

Typical examples include repository interfaces and external provider interfaces.

---

### Domain Services

Domain Services contain business behavior that does not naturally belong to a single Entity or Value Object.

They should be used only when the behavior is part of the domain but cannot be assigned to an existing model.

---

### Exceptions

Domain Exceptions represent violations of business rules.

They communicate business failures without exposing infrastructure-specific errors.

---

## Dependency Rule

The Domain must not depend on:

- Databases
- HTTP
- Web frameworks
- ORMs
- External SDKs
- Messaging implementations

All dependencies point inward toward the Domain.

```text
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

---

## Design Principles

The Domain should:

- Focus on business behavior rather than data.
- Be independent of infrastructure.
- Express the ubiquitous language.
- Protect business invariants.
- Remain stable as technologies evolve.

---

## Summary

The Domain is the heart of a Bounded Context.

Everything outside the Domain exists to support, execute, or persist the business model—not define it.