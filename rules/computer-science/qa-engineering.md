# QA Engineering Rules

When writing tests or implementing quality assurance:

## Test-Driven Development (TDD)

1. **Write test first** - Design by testing before implementation
2. **Red → Green → Refactor** - Follow the TDD cycle strictly
3. **Minimal implementation** - Write only enough code to pass
4. **Tests guide design** - Let tests drive architecture decisions

## Testing Pyramid

```
         /\        E2E (Few)
        /  \       Integration (Some)
       /    \      Unit (Many)
      ────────
```

- Unit tests: Fast, isolated, test behavior not implementation
- Integration tests: Real dependencies where possible
- E2E tests: Critical paths only, expensive to maintain

## Mocking Strategy

- **Mock at boundaries** - External services, databases, APIs
- **Don't mock everything** - Leads to brittle tests
- **Prefer fakes over mocks** - Working simplified implementations

## Quality Principles

- Tests must be deterministic and hermetic
- No shared state between tests
- Test behavior, not implementation details
- Flaky tests are worse than no tests

## Validation

- Cross-validation for ML models
- Nested CV for hyperparameter tuning
- Never test on training data

**For detailed practices:** Use `/qa-engineering` skill
