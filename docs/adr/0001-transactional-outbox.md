# ADR-0001: transactional outbox for reliable publication

## Context

An API changes business data and needs to publish an integration event. A direct broker publish after the database write creates a dual-write failure window.

## Decision

Write the domain change and an outbox record in one database transaction. A separate dispatcher reads pending records, publishes them, and records an explicit delivery state.

## Consequences

- Consumers must be idempotent because delivery can be at-least-once.
- Dispatch latency is not zero; callers must not assume immediate propagation.
- The dispatcher needs leases, retry classification, alerting, and retention.

## Alternatives considered

- Publish before the database commit: events can describe data that never commits.
- Publish after the database commit: committed data can miss an event.
- Distributed transaction: adds operational coupling and may not be supported across the chosen components.

## What would change this decision?

If the operation has no cross-boundary event requirement, a simpler transactional write is preferable. If the database and broker support a proven transaction boundary with acceptable operational cost, reassess this design.
