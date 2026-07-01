# SaaS Architecture Patterns

> A practical reference for building scalable Python SaaS applications using Domain-Driven Design (DDD), Hexagonal Architecture, and a Modular Monolith.

## Why this repository?

As I progressed from WordPress development into backend engineering, I realized that building software is not just about writing code—it is about organizing complexity.

This repository is my personal knowledge base and reference implementation for the architectural patterns used in modern SaaS applications. It documents the concepts I've learned from studying industry-recognized architecture practices and applying them to real-world software projects.

The goal is not to build another framework.

The goal is to understand **why large SaaS systems are structured the way they are.**

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