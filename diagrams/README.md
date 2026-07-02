# Diagrams

This directory contains high-level architecture and workflow diagrams used throughout the documentation.

The diagrams illustrate architectural concepts and interactions between system components without exposing proprietary implementation details or business-specific logic.

## Purpose

The diagrams help visualize:

- Tenant onboarding and workspace setup
- Event-driven message processing
- AI-assisted workflows
- Communication between bounded contexts
- Overall system architecture

They are intended to complement the documentation in the `docs/` directory and provide a quick understanding of the system design.

## Diagrams

### Tenant Onboarding Workflow

Illustrates the high-level onboarding process for a new tenant, including:

- Invitation
- Account creation
- Authentication
- Workspace access
- Channel connection
- Knowledge setup

### Message & AI Workflow

Illustrates the event-driven processing pipeline:

1. External message received
2. Inbox processes and stores the message
3. Domain events are published
4. AI processes the conversation
5. AI returns a decision
6. Automatic reply or user suggestion
7. Reply delivered through the connected channel

## Notes

These diagrams are simplified representations of the architecture.

Their purpose is to explain architectural patterns, system boundaries, and workflow design rather than implementation details.