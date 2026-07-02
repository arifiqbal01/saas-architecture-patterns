# Frontend Architecture

## Overview

The frontend follows a **feature-oriented architecture** inspired by Domain-Driven Design (DDD) and Clean Architecture principles.

Rather than organizing the application by technical layers (components, hooks, pages, services), the codebase is organized around **business capabilities**. Each feature owns its own application logic, domain model, infrastructure, and user interface.

This approach keeps features independent, reduces coupling, and allows the application to scale as new capabilities are introduced.

---

## Goals

The frontend architecture aims to:

- Organize code by business capability.
- Keep features self-contained.
- Separate business logic from UI implementation.
- Reduce coupling between features.
- Improve maintainability and scalability.

---

## High-Level Structure

```text
frontend/

├── app/
├── core/
├── features/
├── infra/
├── lib/
├── shared/
├── styles/
├── types/
└── ui/
```

---

## Core

The `core` directory contains application-wide functionality shared across features.

Typical responsibilities include:

- Authentication
- Session management
- Global providers
- Error handling
- Shared application services

Core modules should remain generic and independent of individual business features.

---

## Features

Each business capability is implemented as an independent feature.

```text
features/

├── auth/
├── channels/
├── inbox/
├── knowledge/
├── media/
└── users/
```

Every feature owns its own architecture and should minimize dependencies on other features.

---

## Feature Structure

A feature typically follows this structure:

```text
feature/

├── application/
├── domain/
├── infrastructure/
└── ui/
```

---

### Domain

The Domain contains the feature's business model.

Typical contents include:

- Business entities
- Types
- Constants
- Validation rules
- Business-specific utilities

The Domain remains independent of UI and networking concerns.

---

### Application

The Application layer coordinates feature-specific workflows.

Typical responsibilities include:

- Commands
- Queries
- Mutations
- Feature services
- Application hooks

This layer connects the UI with the Domain while remaining independent of implementation details.

---

### Infrastructure

Infrastructure manages communication with external systems.

Typical responsibilities include:

- API clients
- DTOs
- Data mappers
- HTTP requests
- State synchronization

Infrastructure translates external data into the feature's Domain Model.

---

### UI

The UI layer contains presentation components.

Typical contents include:

- Screens
- Components
- Layouts
- Feature hooks
- UI context

The UI is responsible only for presentation and user interaction.

---

## Shared Modules

Common functionality shared across multiple features is extracted into shared modules.

Examples include:

- Reusable UI components
- Utility functions
- Common types
- Shared hooks

Shared modules should remain generic and avoid feature-specific business logic.

---

## State Management

State is managed using the most appropriate tool for each responsibility.

- **React Query** manages server state, caching, and asynchronous data fetching.
- **Zustand** manages lightweight client-side application state.
- **React Context** is used for localized UI state where appropriate.

This separation keeps server state and client state independent while reducing unnecessary complexity.

---

## Styling

The UI is styled using **Tailwind CSS**, allowing components to remain composable and consistent without maintaining large custom stylesheet hierarchies.

---

## Benefits

This architecture provides several advantages:

- Feature isolation
- Clear ownership
- Scalable folder organization
- Reduced coupling
- Improved maintainability
- Consistent architectural patterns across the frontend and backend

---

## Relationship with the Backend

The frontend mirrors the architectural principles used by the backend.

Both organize code around business capabilities and separate concerns into dedicated layers.

This consistency simplifies development and makes it easier to reason about the system as a whole.

---

## Technologies

The frontend is built using:

- Next.js
- React
- TypeScript
- Tailwind CSS
- React Query
- Zustand

---

## References

- Eric Evans — *Domain-Driven Design: Tackling Complexity in the Heart of Software*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*