# Software Engineering Rules

When designing and implementing software:

## SOLID Principles

- **S**ingle Responsibility: One reason to change per class
- **O**pen/Closed: Open for extension, closed for modification
- **L**iskov Substitution: Subtypes must be substitutable
- **I**nterface Segregation: No unused method dependencies
- **D**ependency Inversion: Depend on abstractions

## Design Patterns (Apply When Needed)

- **Strategy**: Interchangeable algorithms
- **Observer**: One-to-many state notification
- **Factory**: Encapsulate object creation
- **Builder**: Complex object construction
- **Adapter**: Interface compatibility

## Domain-Driven Design

- Define Bounded Contexts with clear boundaries
- Use Ubiquitous Language in code and communication
- Identify Aggregates with single root entity
- Separate Core Domain from supporting contexts

## Clean Code

- Intention-revealing names
- Small functions (single purpose)
- No premature abstraction (Rule of Three)
- Comments for "why", not "what"

## Avoid Over-Engineering

- Three similar lines > premature abstraction
- Solve the current problem, not hypothetical futures
- Delete unused code completely
- Simple is better than clever

**For detailed patterns:** Use `/software-engineering` skill
