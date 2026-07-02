# Domain Events

## Overview

A Domain Event represents something important that has happened within the business domain.

Unlike commands, which express an intention to perform an action, Domain Events represent **facts**. Once an event occurs, it cannot be changed.

Domain Events enable different parts of the system to react to business changes without creating direct dependencies between them.

---

## Goals

Domain Events help to:

- Decouple business capabilities.
- Enable event-driven workflows.
- Improve modularity.
- Support eventual consistency.
- Simplify integration between bounded contexts.

---

## Core Concepts

### Business Facts

A Domain Event represents something that has already happened.

Examples include:

- A resource was created.
- A user completed an action.
- A workflow finished.
- A state changed.

Events describe outcomes rather than requests.

---

### Immutable

Domain Events are immutable.

Once published, an event should never be modified.

If the business state changes again, a new event should be emitted.

---

### Past Tense Naming

Events are typically named in the past tense because they describe completed actions.

Examples:

- ResourceCreated
- UserRegistered
- PaymentCompleted

This naming convention clearly communicates that the event has already occurred.

---

## Event Lifecycle

A typical event lifecycle follows these steps:

```text
Application
      │
      ▼
Domain
      │
Business State Changes
      │
      ▼
Domain Event Raised
      │
      ▼
Application
      │
      ▼
Event Bus
      │
      ├────────► Handler A
      ├────────► Handler B
      └────────► Handler C
```

The Domain raises events.

The Application collects and publishes them.

Consumers react independently.

---

## Publishers and Consumers

The component that raises an event does not know who will consume it.

This provides loose coupling between different parts of the system.

Multiple consumers can react to the same event without modifying the original publisher.

---

## Benefits

Using Domain Events provides several advantages:

- Loose coupling
- Better scalability
- Independent workflows
- Easier feature expansion
- Clear integration boundaries

New functionality can often be added by introducing new event handlers rather than modifying existing business logic.

---

## Domain Events vs Commands

Although both are used in event-driven systems, they serve different purposes.

| Command | Domain Event |
|---------|--------------|
| Requests an action | Represents a completed action |
| Future-oriented | Past-oriented |
| Usually one handler | Zero or many handlers |
| Can be rejected | Has already happened |

Commands express intent.

Domain Events communicate facts.

---

## Domain Events and Bounded Contexts

Domain Events are a common mechanism for communication between bounded contexts.

Instead of directly calling another context, a context publishes an event.

Interested consumers subscribe to the event and react independently.

This approach avoids direct dependencies while allowing the system to evolve over time.

---

## Relationship with CQRS

Domain Events are commonly used alongside CQRS.

A typical sequence is:

1. A Command changes the Domain.
2. The Domain raises one or more Domain Events.
3. The Application publishes the events.
4. Event handlers execute follow-up actions.
5. Read Models are updated if required.

This keeps the write model focused on business behavior while allowing the read side to evolve independently.

---

## Best Practices

- Raise events from the Domain.
- Keep events immutable.
- Publish events after successful business operations.
- Design handlers to be independent.
- Avoid embedding business logic inside the Event Bus.

---

## References

- Eric Evans — *Domain-Driven Design*
- Vaughn Vernon — *Implementing Domain-Driven Design*
- Harry Percival & Bob Gregory — *Architecture Patterns with Python*