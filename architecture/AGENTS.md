# Architecture Standards

## Purpose
Define architectural patterns for resilient, scalable systems.

## Scope
Microservices, cloud-native design, 12-factor principles, and failure handling.

## Rules

### Always
- Build cloud-native microservices around business capabilities
- Design services as independently deployable units
- Keep services stateless with separate data stores
- Use loose coupling via lightweight APIs (REST)
- Follow Twelve-Factor App principles
- Design for horizontal scaling
- Use interfaces and abstract classes for clear boundaries
- Implement retry patterns for transient failures
- Use circuit breaker patterns to prevent cascading failures
- Apply bulkhead patterns to isolate failing services

### Never
- Create tightly coupled services
- Mix business concerns in one service
- Create stateful services without clear separation
