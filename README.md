# Dream Architecture

Architecture notes and decision records for systems worth designing before implementing.

These are design exercises—not descriptions of production systems. Every document should state its assumptions, non-goals, failure modes, and what evidence would change the decision.

## Index

- [ADR-0001: transactional outbox for reliable publication](docs/adr/0001-transactional-outbox.md)
- [Design template](docs/designs/template.md)

## Review checklist

1. Boundaries and ownership
2. Source of truth and consistency requirements
3. Timeouts, retries, duplicates, and poison work
4. Observability and operations
5. Security, recovery, cost, and explicit trade-offs

## Related labs

- [dotnet-lab](https://github.com/trandat1114/dotnet-lab)
- [engineering-playground](https://github.com/trandat1114/engineering-playground)
- [sql-performance-lab](https://github.com/trandat1114/sql-performance-lab)
