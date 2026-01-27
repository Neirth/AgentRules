# Quality Assurance Engineering Rules

> *"At Google, it's the product teams that own quality, not testers. Every developer is expected to do their own testing."*
> — Google Testing Philosophy

## Purpose

These rules establish the methodology for creating robust, maintainable, and reliable software through systematic quality assurance practices. Drawing from the engineering excellence of Netflix, AWS, Google, Microsoft, Airbnb, Discord, Red Hat, and other industry leaders, this guide covers Test-Driven Development (TDD), mocking strategies, chaos engineering, and comprehensive testing practices.

---

## Core Philosophy

### Quality is Everyone's Responsibility

```
┌─────────────────────────────────────────────────────────────────────┐
│                    THE TESTING PYRAMID                              │
│                                                                     │
│                          ▲                                          │
│                         /│\        E2E Tests (Few)                  │
│                        / │ \       - Full system validation         │
│                       /  │  \      - Expensive, slow                │
│                      /   │   \                                      │
│                     /────┼────\    Integration Tests (Some)         │
│                    /     │     \   - Component interaction          │
│                   /      │      \  - Real dependencies              │
│                  /───────┼───────\ Unit Tests (Many)                │
│                 /        │        \- Fast, isolated                 │
│                /─────────┴─────────\- Business logic                │
│               ──────────────────────                                │
└─────────────────────────────────────────────────────────────────────┘
```

**Google's Approach:** Invest heavily in Unit and Integration Testing; use end-to-end testing sparingly. Small, focused tests provide faster feedback and are easier to maintain.

**Airbnb's Evolution:** Went from brittle tests to a resilient suite by reducing build times from 1 hour+ to ~6 minutes while handling many times the number of builds.

---

## Test-Driven Development (TDD)

### The TDD Cycle

```
        ┌─────────────────┐
        │   1. RED        │
        │   Write a       │
        │   failing test  │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │   2. GREEN      │
        │   Write minimal │
        │   code to pass  │
        └────────┬────────┘
                 │
                 ▼
        ┌─────────────────┐
        │   3. REFACTOR   │
        │   Improve code  │
        │   quality       │
        └────────┬────────┘
                 │
                 └──────────────▶ Repeat
```

### TDD Principles

1. **Write Test First:** Design the component by writing a test that invokes it before implementation exists
2. **Minimal Implementation:** Write only enough code to make the test pass
3. **Refactor with Confidence:** Tests provide safety net for code improvements
4. **Tests Guide Design:** Code naturally becomes modular and testable

**AWS Guidance:** TDD works best at a unit test level. The developer designs a software component by writing a test first, using test fixtures with mock objects to simulate external dependencies.

### Test Structure: Arrange/Act/Assert

```
┌─────────────────────────────────────────────────────────────────┐
│  ARRANGE                                                        │
│  - Set up test fixtures                                         │
│  - Initialize mocks and stubs                                   │
│  - Prepare input data                                           │
├─────────────────────────────────────────────────────────────────┤
│  ACT                                                            │
│  - Execute the system under test                                │
│  - Call the method or function being tested                     │
├─────────────────────────────────────────────────────────────────┤
│  ASSERT                                                         │
│  - Verify expected outcomes                                     │
│  - Check state changes                                          │
│  - Validate return values                                       │
└─────────────────────────────────────────────────────────────────┘
```

**Microsoft's Standard:** This pattern (also known as AAA) is the organizing structure for unit tests across Microsoft engineering.

---

## Mocking Strategy

### Understanding Test Doubles

```
┌──────────────────────────────────────────────────────────────────┐
│                      TEST DOUBLES                                │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  STUB ─────────────────────────────────────────────────────────  │
│  │ • Provides canned responses                                   │
│  │ • No behavior verification                                    │
│  │ • State verification only                                     │
│  └──────────────────────────────────────────────────────────────  │
│                                                                  │
│  MOCK ─────────────────────────────────────────────────────────  │
│  │ • Verifies interactions                                       │
│  │ • Behavioral verification                                     │
│  │ • Expects specific calls                                      │
│  └──────────────────────────────────────────────────────────────  │
│                                                                  │
│  FAKE ─────────────────────────────────────────────────────────  │
│  │ • Working implementation                                      │
│  │ • Simplified for testing                                      │
│  │ • In-memory databases, etc.                                   │
│  └──────────────────────────────────────────────────────────────  │
│                                                                  │
│  SPY ──────────────────────────────────────────────────────────  │
│  │ • Records interactions                                        │
│  │ • Allows inspection after test                                │
│  │ • Real implementation wrapper                                 │
│  └──────────────────────────────────────────────────────────────  │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### When to Mock

**Do Mock:**
- External services (APIs, databases, file systems)
- Non-deterministic behavior (time, random numbers)
- Slow dependencies (network calls)
- Third-party libraries at boundaries

**Don't Mock:**
- Internal implementation details
- Value objects and pure functions
- Things you don't own (mock the adapter instead)
- Everything (leads to brittle tests)

**Microsoft Warning:** Avoid writing tests that rely on actual infrastructure where possible, but beware of over-mocking which can lead to tests that pass but don't validate real-world scenarios.

### The Mock Boundary Pattern

```
┌─────────────────────────────────────────────────────────────────┐
│                    YOUR CODE                                    │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │              Business Logic                              │    │
│  │         (No mocking needed here)                        │    │
│  └─────────────────────────┬───────────────────────────────┘    │
│                            │                                    │
│  ┌─────────────────────────▼───────────────────────────────┐    │
│  │              Adapter / Port Layer                        │    │
│  │         (Mock at this boundary)                         │    │
│  └─────────────────────────┬───────────────────────────────┘    │
└────────────────────────────┼────────────────────────────────────┘
                             │
┌────────────────────────────▼────────────────────────────────────┐
│                  EXTERNAL SYSTEMS                               │
│     (Databases, APIs, File Systems, Message Queues)             │
└─────────────────────────────────────────────────────────────────┘
```

---

## Testing Levels

### Unit Tests

**Characteristics:**
- Test single units of behavior in isolation
- Fast execution (milliseconds)
- No external dependencies
- High code coverage target

**Best Practices (Google):**
- Tests should be deterministic
- Tests should be hermetic (self-contained)
- Tests should test behavior, not implementation
- Keep tests focused and small

```markdown
## Unit Test Guidelines

1. One logical assertion per test
2. Descriptive test names (describe behavior)
3. Independent tests (no shared state)
4. Fast execution (< 100ms per test)
5. Comprehensive edge case coverage
```

### Integration Tests

**Characteristics:**
- Test component interactions
- May use real or simulated dependencies
- Slower than unit tests
- Verify contracts between components

**AWS Recommendation:** In the context of integration tests, calls to databases should happen using realistic databases without mocking. The benefit of mocks is reduced for integration tests because the level of effort to implement mocks increases with the number of connection points.

### End-to-End Tests

**Characteristics:**
- Full system validation
- Real infrastructure (when possible)
- Expensive to maintain
- Few but critical paths

**AWS Cloud Testing:** Although testing in the cloud can create developer latency and increase costs, this technique provides the most reliable, accurate, and complete test coverage.

---

## Chaos Engineering

### The Netflix Philosophy

> *"The only way to be comfortable handling failure is to constantly practice failing."*

Netflix pioneered chaos engineering with the Simian Army:

```
┌─────────────────────────────────────────────────────────────────┐
│                    THE SIMIAN ARMY                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  CHAOS MONKEY ──────────────────────────────────────────────    │
│  │ Randomly terminates VM instances in production               │
│  │ Tests: Can the system survive instance failures?             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CHAOS KONG ────────────────────────────────────────────────    │
│  │ Simulates entire data center failures                        │
│  │ Tests: Can the system survive regional outages?              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  LATENCY MONKEY ────────────────────────────────────────────    │
│  │ Introduces artificial delays in RESTful calls                │
│  │ Tests: Can the system handle degraded performance?           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Result:** Netflix's system handled the 9/25/14 reboot of 10% of AWS servers without issue.

### Chaos Engineering Principles

1. **Start with a Hypothesis:** Define normal system behavior
2. **Vary Real-World Events:** Inject failures that could happen
3. **Run Experiments in Production:** Test where it matters
4. **Automate Experiments:** Make chaos continuous
5. **Minimize Blast Radius:** Start small, expand gradually

### Implementing Chaos Testing

```markdown
## Chaos Experiment Template

### Hypothesis
"When [failure condition], the system will [expected behavior]"

### Steady State
- Define normal metrics (latency, error rate, throughput)
- Establish baseline measurements

### Experiment
- Inject: [type of failure]
- Scope: [affected components]
- Duration: [time window]
- Rollback: [recovery mechanism]

### Observations
- Actual vs expected behavior
- Impact on user experience
- Recovery time

### Learning
- Document findings
- Create remediation plan
- Update system design
```

---

## Flaky Test Management

### Google's Approach

**Problem:** At Google's scale, spurious breakages that affect even a small percentage of tests can waste huge amounts of engineering time.

**Solution:**
1. **Automated Monitoring:** Tools monitor test flakiness
2. **Automatic Quarantine:** High-flakiness tests removed from critical path
3. **Bug Filing:** Automatic issues created for developers
4. **Change Detection:** Identify commits that introduce flakiness

### Preventing Flaky Tests

```markdown
## Flaky Test Checklist

[ ] No reliance on timing (use explicit waits/conditions)
[ ] No shared state between tests
[ ] No dependency on test execution order
[ ] No external service dependencies without mocks
[ ] Deterministic data generation
[ ] Proper cleanup/teardown
[ ] Avoid race conditions in async code
[ ] Use stable selectors (not positional)
```

---

## Testing Microservices

### Service-Level Testing Strategy

```
┌─────────────────────────────────────────────────────────────────┐
│                 MICROSERVICE TESTING STRATEGY                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  CONTRACT TESTS ────────────────────────────────────────────    │
│  │ Verify API contracts between services                        │
│  │ Consumer-driven contract testing                             │
│  │ Prevents breaking changes                                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMPONENT TESTS ───────────────────────────────────────────    │
│  │ Test service in isolation                                    │
│  │ Mock external dependencies                                   │
│  │ Verify internal behavior                                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  INTEGRATION TESTS ─────────────────────────────────────────    │
│  │ Test service interactions                                    │
│  │ Real dependencies when possible                              │
│  │ Verify data flow                                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Discord's Testing Practices

**Load Testing at Scale:**
- Cloud infrastructure simulates millions of concurrent users
- Real-time dashboards track latency, error rates, throughput
- Regular security audits and penetration testing
- Autoscaling validation under stress

**Architecture Decisions:**
- Stateless gateway servers for resilience
- Asynchronous communication between services
- Event-driven architecture for decoupling

---

## Testing Culture

### Airbnb's Transformation

**Before:**
- Most commits pushed directly to master
- No code review requirement
- Most new code shipped without tests
- Brittle, slow test suite

**After:**
- Pull request requirement for all changes
- CI status integrated in PRs (yellow/red/green)
- Test coverage surfaced at review time
- Engineers call out untested changes

### Building Testing Culture

```markdown
## Testing Culture Principles

1. **Ownership:** You build it, you test it
2. **Visibility:** Surface coverage at code review
3. **Speed:** Fast feedback loops (< 10 min CI)
4. **Reliability:** No flaky tests in critical path
5. **Accountability:** On-call for code you ship
```

**Netflix Practice:** "If you were writing code, and you ship the code that day, you were on-call to fix it if it broke that night. That caused developers to be much more careful about the code they deployed."

---

## Red Hat's Linux Kernel Testing

### System-Level Testing

For low-level systems like kernels, Red Hat employs:

**Linux Test Project (LTP):**
- Mission: "Testing Linux, one syscall at a time"
- Joint project: SUSE, Red Hat, Fujitsu, IBM, Cisco, Oracle
- Comprehensive syscall coverage
- Reliability validation

**Static Analysis:**
- Sparse: Type-checking, lock checking, value range checking
- Smatch: Logic mistakes, integer overflows, null pointer dereferences
- Continuous analysis in CI pipeline

### Testing Approaches

```markdown
## System Testing Methodology

1. **Userspace Testing**
   - System calls testing
   - Virtual filesystem inspection (procfs, sysfs)
   - Log analysis
   - Bash script automation

2. **Static Analysis**
   - Compile-time checking
   - Source code analysis
   - Pattern matching for common bugs

3. **Integration Testing**
   - Beaker test system (full stack)
   - Hardware integration validation
   - Multi-version compatibility
```

---

## Test Maintainability

### Google's Focus

> *"Maintainable tests are ones that 'just work': after writing them, engineers don't need to think about them again until they fail, and those failures indicate real bugs with clear causes."*

### Characteristics of Maintainable Tests

1. **Clear Intent:** Test name describes behavior
2. **Single Responsibility:** One reason to fail
3. **Independent:** No test ordering dependencies
4. **Deterministic:** Same result every time
5. **Fast:** Quick feedback for developers
6. **Self-Documenting:** Code explains itself

### Test Smell Detection

```markdown
## Common Test Smells

❌ Tests that test implementation details
❌ Tests with multiple assertions on unrelated behaviors
❌ Tests with complex setup/teardown
❌ Tests that require specific execution order
❌ Tests with hardcoded timeouts
❌ Tests that mock everything
❌ Tests with unclear failure messages
```

---

## Continuous Integration

### CI Pipeline Structure

```
┌─────────────────────────────────────────────────────────────────┐
│                    CI PIPELINE                                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  STAGE 1: FAST FEEDBACK ────────────────────────────────────    │
│  │ Lint, Format, Static Analysis                                │
│  │ Target: < 2 minutes                                          │
│  └──────────────────────────────────────────────────────────    │
│                           │                                     │
│                           ▼                                     │
│  STAGE 2: UNIT TESTS ───────────────────────────────────────    │
│  │ All unit tests in parallel                                   │
│  │ Target: < 5 minutes                                          │
│  └──────────────────────────────────────────────────────────    │
│                           │                                     │
│                           ▼                                     │
│  STAGE 3: INTEGRATION ──────────────────────────────────────    │
│  │ Service integration tests                                    │
│  │ Target: < 15 minutes                                         │
│  └──────────────────────────────────────────────────────────    │
│                           │                                     │
│                           ▼                                     │
│  STAGE 4: E2E (Optional) ───────────────────────────────────    │
│  │ Critical path validation                                     │
│  │ Run on merge to main                                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Coverage as Quality Signal

**Google's Finding:** Surfacing coverage information during code review had a statistically significant impact—it increased coverage by 10% averaged across all commits.

---

## Checklist

### Before Writing Code
- [ ] Requirements understood and documented
- [ ] Test cases identified
- [ ] Test data prepared
- [ ] Mocking strategy defined

### During Development
- [ ] Write test first (TDD)
- [ ] Run tests frequently
- [ ] Maintain fast feedback loop
- [ ] Refactor with test coverage

### Before Merge
- [ ] All tests passing
- [ ] Coverage meets threshold
- [ ] No flaky tests introduced
- [ ] Integration tests verified
- [ ] Code reviewed

### Production Readiness
- [ ] Chaos experiments run
- [ ] Load testing completed
- [ ] Monitoring in place
- [ ] Runbooks updated
- [ ] On-call rotation defined

---

## Remember

> *"Quality is not an afterthought. It is built into every line of code, every test case, every deployment. The teams that own the code own the quality."*

Testing is not about finding bugs—it's about preventing them. The best code is code that works correctly the first time because it was designed with testing in mind from the beginning.

**The Golden Rules:**
1. Test behavior, not implementation
2. Fast tests run often
3. Flaky tests are worse than no tests
4. Coverage is a signal, not a target
5. You build it, you break it, you fix it
