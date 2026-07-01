# SaaS Architecture Patterns

> A practical reference for building scalable Python SaaS applications using Domain-Driven Design (DDD), Hexagonal Architecture, and a Modular Monolith.

## Why I Created This Repository

I've had the opportunity to apply Domain-Driven Design, Hexagonal Architecture, and Modular Monolith principles while working on a commercial SaaS application.

Because that codebase is proprietary, I cannot share its implementation publicly.

This repository is an independent reference where I document the architectural patterns, design decisions, and implementation approaches I've learned. All examples are generic and intentionally exclude proprietary business logic, domain models, and company-specific code.

---

## What you'll find here

This repository explains and demonstrates:

- Domain-Driven Design (DDD)
- Hexagonal (Ports & Adapters) Architecture
- Modular Monolith architecture
- Bounded Contexts
- Dependency Injection
- Domain Events
- CQRS (Light)
- Clean dependency boundaries
- Folder organization for long-term maintainability

Rather than focusing on frameworks, the emphasis is on creating software that remains understandable and maintainable as it grows.

---

## Repository Structure

```
saas-architecture-patterns/

├── app/           # Example project structure
├── docs/          # Architecture guides
├── diagrams/      # Visual architecture diagrams
├── resources/     # Books and references
└── README.md
```

---

## Architecture Overview

```
                Clients
                   │
             HTTP / API
                   │
          Application Layer
                   │
             Domain Layer
                   ▲
                   │
      Ports (Interfaces)
                   ▲
                   │
 Infrastructure Adapters
```

### Dependency Rule

```
Infrastructure
      │
      ▼
Application
      │
      ▼
Domain
```

The Domain never depends on frameworks, databases, or external services.

---

## Design Principles

This repository follows several principles that appear consistently across modern software architecture:

- Business logic is independent of frameworks.
- Business capabilities define system boundaries.
- Infrastructure is replaceable.
- Dependencies point inward.
- Integration occurs through events or explicit interfaces.
- Business rules remain inside the domain.

---

## Learning Sources

The architecture presented here is inspired by ideas from:

- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*

This repository is my interpretation and learning resource, not a copy of any production codebase.

---

## Purpose

This project is intended to:

- deepen my understanding of software architecture
- document architectural patterns I've learned
- serve as a reference for future projects
- demonstrate my architectural thinking to employers and collaborators

It intentionally focuses on architecture and organization rather than a specific business domain.

---

## Current Status

This repository is being developed incrementally.

Documentation, diagrams, architectural explanations, and code examples will continue to evolve as I learn and gain more experience.

---

## License

MIT