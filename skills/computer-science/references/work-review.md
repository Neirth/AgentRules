---
name: work-review
description: Systematic code review and pre-submission validation practices ensuring code quality, project integrity, and engineering excellence before pushing changes
user-invocable: true
---

# Work Review / Code Review Rules

> *"Code review is not just about finding bugs—it's about knowledge sharing, maintaining standards, and building better engineers."*
> — Engineering culture at Google, Microsoft, and Meta

## Purpose

These rules establish the methodology for conducting thorough work reviews and pre-submission validation. Before any code is pushed to a branch, it must undergo systematic validation to ensure the entire project works correctly, all warnings are addressed, and only necessary files are included. Drawing from practices at Google, Microsoft, Netflix, Airbnb, AWS, and Meta, this guide covers pre-commit validation, testing requirements, code review mechanics, and engineering accountability.

---

## Table of Contents

- [Purpose](#purpose)
- [Core Philosophy](#core-philosophy)
- [Pre-Commit Validation Pipeline](#pre-commit-validation-pipeline)
- [Tool Warning Management](#tool-warning-management)
- [File Management](#file-management)
- [Testing Requirements](#testing-requirements)
- [Before Requesting Review](#before-requesting-review)
- [Whole Project Validation](#whole-project-validation)
- [Code Review Mechanics](#code-review-mechanics)
- [Review Checklist](#review-checklist)
- [Ownership and Accountability](#ownership-and-accountability)
- [Automation and Tooling](#automation-and-tooling)
- [Change-Type-Specific Checklists](#change-type-specific-checklists)
- [Feature Change Checklist](#feature-change-checklist)
- [Bug Fix Checklist](#bug-fix-checklist)
- [Refactoring Checklist](#refactoring-checklist)
- [Performance Optimization Checklist](#performance-optimization-checklist)
- [Continuous Improvement](#continuous-improvement)
- [Post-Review Retrospective](#post-review-retrospective)
- [Remember](#remember)

---

## Core Philosophy

### The Pre-Push Validation Manifesto

```
┌─────────────────────────────────────────────────────────────────────┐
│                    WORK REVIEW PRINCIPLES                           │
│                                                                     │
│              "Ship with Confidence"                                 │
│                                                                     │
│   1. VALIDATE ──────────────────────────────────────────────────    │
│   │ • All tests pass before review request                         │
│   │ • Project builds successfully                                  │
│   │ • No tool warnings dismissed                                   │
│   └─────────────────────────────────────────────────────────────    │
│                                                                     │
│   2. VERIFY ────────────────────────────────────────────────────    │
│   │ • Whole project works after changes                            │
│   │ • No regressions introduced                                    │
│   │ • Integration points tested                                    │
│   └─────────────────────────────────────────────────────────────    │
│                                                                     │
│   3. CLEAN ─────────────────────────────────────────────────────    │
│   │ • Only necessary files included                                │
│   │ • No build artifacts or dependencies                           │
│   │ • No personal configuration files                              │
│   └─────────────────────────────────────────────────────────────    │
│                                                                     │
│   4. OWN ───────────────────────────────────────────────────────    │
│   │ • You build it, you test it                                    │
│   │ • You ship it, you support it                                  │
│   │ • Quality is your responsibility                               │
│   └─────────────────────────────────────────────────────────────    │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Pre-Commit Validation Pipeline

### The Fast Feedback Loop

**Google's Approach:** Fast feedback is essential. Engineers should know within minutes if their change breaks anything.

```
┌─────────────────────────────────────────────────────────────────────┐
│                 PRE-COMMIT VALIDATION STAGES                        │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  STAGE 1: IMMEDIATE (< 30 seconds) ─────────────────────────────    │
│  │ • Format checking (Prettier, Black, gofmt)                       │
│  │ • Linting (ESLint, Pylint, Clippy)                              │
│  │ • Basic syntax validation                                        │
│  │ • Secrets detection                                              │
│  └──────────────────────────────────────────────────────────────    │
│                           │                                         │
│                           ▼                                         │
│  STAGE 2: FAST (< 2 minutes) ───────────────────────────────────    │
│  │ • Static type checking (TypeScript, mypy)                        │
│  │ • Static analysis (Sonar, CodeQL)                                │
│  │ • Documentation generation check                                 │
│  │ • License header validation                                      │
│  └──────────────────────────────────────────────────────────────    │
│                           │                                         │
│                           ▼                                         │
│  STAGE 3: UNIT TESTS (< 5 minutes) ─────────────────────────────    │
│  │ • All unit tests for changed modules                             │
│  │ • Test coverage calculation                                      │
│  │ • Code coverage threshold check                                  │
│  └──────────────────────────────────────────────────────────────    │
│                           │                                         │
│                           ▼                                         │
│  STAGE 4: BUILD (< 10 minutes) ─────────────────────────────────    │
│  │ • Full project compilation                                       │
│  │ • Asset bundling and optimization                                │
│  │ • Dependency resolution                                          │
│  │ • Container image building (if applicable)                       │
│  └──────────────────────────────────────────────────────────────    │
│                           │                                         │
│                           ▼                                         │
│  STAGE 5: INTEGRATION (< 15 minutes) ───────────────────────────    │
│  │ • Integration tests with real dependencies                       │
│  │ • API contract validation                                        │
│  │ • Database migration tests                                       │
│  │ • End-to-end critical path tests                                 │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

**Airbnb's Transformation:** Reduced build times from 1+ hour to ~6 minutes while handling exponentially more builds through pipeline optimization.

---

## Tool Warning Management

### Never Dismiss Warnings

> *"Every warning is a signal. Ignoring signals leads to incidents."*
> — Site Reliability Engineering at Google

**Red Hat's Linux Kernel Approach:** Continuous static analysis using Sparse and Smatch catches potential bugs before code review.

### Warning Classification System

```
┌─────────────────────────────────────────────────────────────────────┐
│                   WARNING SEVERITY LEVELS                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  🔴 BLOCKING ERRORS ─────────────────────────────────────────────    │
│  │ • Compilation errors                                             │
│  │ • Type errors                                                    │
│  │ • Failed tests                                                   │
│  │ • Security vulnerabilities                                       │
│  │ • License violations                                             │
│  │                                                                  │
│  │ Action: MUST FIX before any commit                               │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  🟡 CRITICAL WARNINGS ───────────────────────────────────────────    │
│  │ • Linter errors                                                  │
│  │ • Code quality violations                                        │
│  │ • Performance anti-patterns                                      │
│  │ • Accessibility violations                                       │
│  │ • Deprecated API usage                                           │
│  │                                                                  │
│  │ Action: FIX or explicitly document suppression reason            │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  🟢 ADVISORY WARNINGS ───────────────────────────────────────────    │
│  │ • Code style suggestions                                         │
│  │ • Complexity metrics                                             │
│  │ • Documentation gaps                                             │
│  │ • Minor optimizations                                            │
│  │                                                                  │
│  │ Action: Address or create tech debt ticket                       │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Warning Suppression Rules

**When suppression is acceptable:**
1. **False Positive:** Tool incorrectly flagged valid code
   - Document why it's safe
   - Add suppression comment with explanation
   - Consider reporting to tool maintainers

2. **Intentional Pattern:** Specific case requires the pattern
   - Document the business/technical reason
   - Use narrowest possible suppression scope
   - Add issue for future refactoring if possible

**When suppression is NOT acceptable:**
- "I'll fix it later" (create a ticket instead)
- "It's only a warning" (warnings indicate real issues)
- "It works on my machine" (not on CI/production)
- "Legacy code does it too" (don't propagate bad patterns)

---

## File Management

### Keep Commits Clean

**Airbnb's Evolution:** Strict policies on what gets committed eliminated noise in code reviews and improved merge velocity.

### What to Include

```
┌─────────────────────────────────────────────────────────────────────┐
│                     COMMIT CONTENT POLICY                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ✅ INCLUDE ─────────────────────────────────────────────────────    │
│  │ • Source code files                                              │
│  │ • Test files                                                     │
│  │ • Configuration files (shared team config)                       │
│  │ • Documentation (README, API docs, architecture docs)            │
│  │ • Schema migrations                                              │
│  │ • Package manifests (package.json, requirements.txt, go.mod)     │
│  │ • CI/CD pipeline definitions                                     │
│  │ • License files                                                  │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  ❌ EXCLUDE (via .gitignore) ───────────────────────────────────    │
│  │ • Build artifacts (dist/, build/, target/, bin/, obj/)           │
│  │ • Dependencies (node_modules/, vendor/, .venv/)                  │
│  │ • IDE/editor configs (.vscode/, .idea/, *.swp)                   │
│  │ • OS files (.DS_Store, Thumbs.db)                                │
│  │ • Secrets and credentials (.env, *.key, *.pem)                   │
│  │ • Log files (*.log, logs/)                                       │
│  │ • Cache files (.cache/, *.pyc, __pycache__/)                     │
│  │ • Coverage reports (coverage/, htmlcov/, .coverage)              │
│  │ • Temporary files (tmp/, temp/, *.tmp)                           │
│  │ • Personal notes or scratch files                                │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### Documentation Policy

**Include only necessary documentation:**
- README updates for new features
- API documentation for public interfaces
- Architecture Decision Records (ADRs) for significant changes
- Migration guides for breaking changes

**Do NOT include:**
- Personal notes or TODO lists (use issue tracker)
- Meeting notes (use wiki or separate repo)
- Unrequested design documents
- Generated documentation (unless source of truth)

---

## Testing Requirements

### Comprehensive Testing Before Review

> *"At Google, product teams own quality, not testers. Every developer is expected to do their own testing."*
> — Google Testing Philosophy

### Pre-Review Testing Checklist

```markdown
## Before Requesting Review

### Unit Tests
- [ ] All unit tests pass locally
- [ ] New code has unit test coverage
- [ ] Coverage threshold met (typically 80%+)
- [ ] Edge cases covered
- [ ] Error paths tested

### Integration Tests
- [ ] Integration tests pass with real dependencies
- [ ] API contracts validated
- [ ] Database migrations tested
- [ ] External service integrations verified

### Build Verification
- [ ] Project builds successfully
- [ ] No compilation warnings
- [ ] All assets bundle correctly
- [ ] Dependencies resolve without conflicts

### Quality Gates
- [ ] Linter passes with no errors
- [ ] Type checking passes
- [ ] Static analysis clean
- [ ] Security scan passes
- [ ] Performance benchmarks within limits

### Regression Testing
- [ ] Existing functionality still works
- [ ] No breaking changes to public APIs
- [ ] Backward compatibility maintained (if required)
- [ ] Dependent services unaffected
```

**Microsoft's Standard:** Every code change must include tests. Untested code is considered incomplete.

---

## Whole Project Validation

### System-Level Verification

**The Netflix Model:** If you ship code today, you're on-call to fix it tonight. This drives thorough validation.

### Validation Strategy

```
┌─────────────────────────────────────────────────────────────────────┐
│              WHOLE PROJECT VALIDATION PROCESS                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  1. CLEAN BUILD ────────────────────────────────────────────────    │
│     │ • Delete all build artifacts                                  │
│     │ • Fresh dependency installation                               │
│     │ • Build from scratch                                          │
│     │ • Verify no errors or warnings                                │
│     └────────────────────────────────────────────────────────────   │
│                                                                     │
│  2. FULL TEST SUITE ────────────────────────────────────────────    │
│     │ • Run all unit tests                                          │
│     │ • Run all integration tests                                   │
│     │ • Run smoke tests for critical paths                          │
│     │ • Verify no test failures or flakiness                        │
│     └────────────────────────────────────────────────────────────   │
│                                                                     │
│  3. INTEGRATION VERIFICATION ───────────────────────────────────    │
│     │ • Test with dependent services                                │
│     │ • Validate API contracts                                      │
│     │ • Check backward compatibility                                │
│     │ • Verify data migrations                                      │
│     └────────────────────────────────────────────────────────────   │
│                                                                     │
│  4. RUNTIME VALIDATION ─────────────────────────────────────────    │
│     │ • Start application locally                                   │
│     │ • Exercise new functionality manually                         │
│     │ • Check logs for errors                                       │
│     │ • Verify performance characteristics                          │
│     └────────────────────────────────────────────────────────────   │
│                                                                     │
│  5. DEPLOYMENT SIMULATION ──────────────────────────────────────    │
│     │ • Build deployment artifacts                                  │
│     │ • Test in staging environment                                 │
│     │ • Run smoke tests against staging                             │
│     │ • Validate monitoring and alerts                              │
│     └────────────────────────────────────────────────────────────   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

**AWS Cloud Testing Guidance:** Testing in realistic environments provides the most reliable and complete test coverage.

---

## Code Review Mechanics

### Review Process

**Airbnb's Transformation:**

| Before | After |
|--------|-------|
| Direct master pushes | PR requirement for all changes |
| No code review | Mandatory peer review |
| No CI visibility | CI status integrated in PRs (🔴/🟡/🟢) |
| Untested code shipped | Coverage visible at review time |
| Brittle test suite | Reliable tests with coverage gates |

### Review Workflow

```
┌─────────────────────────────────────────────────────────────────────┐
│                    CODE REVIEW WORKFLOW                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  AUTHOR RESPONSIBILITIES                                            │
│  ────────────────────────────────────────────────────────────────   │
│  1. Self-review code before requesting review                       │
│  2. Ensure all CI checks pass                                       │
│  3. Write clear PR description with context                         │
│  4. Link related issues/tickets                                     │
│  5. Add screenshots for UI changes                                  │
│  6. Tag appropriate reviewers                                       │
│  7. Respond to feedback constructively                              │
│  8. Update based on review comments                                 │
│                                                                     │
│  REVIEWER RESPONSIBILITIES                                          │
│  ────────────────────────────────────────────────────────────────   │
│  1. Review within SLA (typically 24 hours)                          │
│  2. Focus on correctness, design, and maintainability               │
│  3. Check test coverage and quality                                 │
│  4. Verify documentation is adequate                                │
│  5. Ensure code follows team standards                              │
│  6. Ask questions, don't just critique                              │
│  7. Approve when satisfied, or request changes                      │
│  8. Re-review after changes                                         │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### What to Review

**Google's Code Review Guidelines:**

```markdown
## Review Checklist

### Design
- [ ] Code fits into overall system architecture
- [ ] Changes are appropriate for codebase complexity
- [ ] No over-engineering for current requirements

### Functionality
- [ ] Code does what author intended
- [ ] Behavior is good for users
- [ ] No subtle bugs or edge cases missed

### Complexity
- [ ] Code is understandable to other developers
- [ ] Functions/classes are appropriately sized
- [ ] No unnecessary complexity

### Tests
- [ ] Tests are correct, sensible, and useful
- [ ] Tests will fail if code is broken
- [ ] Coverage is adequate

### Naming
- [ ] Names are clear and descriptive
- [ ] Names follow team conventions
- [ ] No misleading names

### Comments
- [ ] Comments explain "why", not "what"
- [ ] Comments for unusual or non-obvious code
- [ ] No commented-out code

### Style
- [ ] Follows team style guide
- [ ] Consistent with existing code
- [ ] Automated formatting applied

### Documentation
- [ ] API documentation updated
- [ ] README updated if needed
- [ ] Migration guide if breaking changes
```

---

## Ownership and Accountability

### The Netflix Philosophy

> *"If you were writing code, and you ship the code that day, you were on-call to fix it if it broke that night. That caused developers to be much more careful about the code they deployed."*

### Ownership Model

```
┌─────────────────────────────────────────────────────────────────────┐
│                    OWNERSHIP PRINCIPLES                             │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  YOU BUILD IT ──────────────────────────────────────────────────    │
│  │ • Design the solution                                            │
│  │ • Write the code                                                 │
│  │ • Write comprehensive tests                                      │
│  │ • Document the functionality                                     │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  YOU TEST IT ───────────────────────────────────────────────────    │
│  │ • Unit tests for your code                                       │
│  │ • Integration tests for interactions                             │
│  │ • Manual verification of functionality                           │
│  │ • Performance and security testing                               │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  YOU SHIP IT ───────────────────────────────────────────────────    │
│  │ • Validate in staging                                            │
│  │ • Monitor deployment                                             │
│  │ • Verify in production                                           │
│  │ • Roll back if needed                                            │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
│  YOU SUPPORT IT ────────────────────────────────────────────────    │
│  │ • On-call for incidents                                          │
│  │ • Fix bugs in your code                                          │
│  │ • Performance optimization                                       │
│  │ • Knowledge transfer to team                                     │
│  └──────────────────────────────────────────────────────────────    │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

**Google's Approach:** Quality is everyone's responsibility. Product teams own quality, not separate QA teams.

---

## Automation and Tooling

### Pre-commit Hooks

**Recommended Setup:**

```bash
# Example pre-commit hook configuration
# Install: pre-commit install

hooks:
  # Fast checks (< 30s)
  - Trailing whitespace removal
  - File size limits
  - Secrets detection (gitleaks, detect-secrets)
  
  # Format checks (< 1m)
  - Code formatting (prettier, black, gofmt)
  - Import sorting (isort, goimports)
  
  # Linting (< 2m)
  - ESLint, Pylint, Clippy
  - Type checking (mypy, tsc --noEmit)
  
  # Optional: Fast tests
  - Unit tests for changed files only
```

### CI Pipeline Gates

**Must-pass checks before merge:**
1. ✅ All linters pass
2. ✅ All tests pass
3. ✅ Build succeeds
4. ✅ Coverage threshold met
5. ✅ No security vulnerabilities
6. ✅ Code review approved
7. ✅ No merge conflicts

**Google's Finding:** Surfacing coverage during code review increased coverage by 10% across all commits.

---

## Change-Type-Specific Checklists

### Feature Implementation

```markdown
## Feature Change Checklist

- [ ] Feature flag implemented (if applicable)
- [ ] Unit tests cover new functionality
- [ ] Integration tests verify feature works end-to-end
- [ ] Documentation updated (README, API docs)
- [ ] Accessibility tested (if UI)
- [ ] Performance impact measured
- [ ] Security review completed
- [ ] Backward compatibility maintained
- [ ] Migration path documented (if breaking)
- [ ] Monitoring/alerts configured
```

### Bug Fix

```markdown
## Bug Fix Checklist

- [ ] Root cause identified and documented
- [ ] Regression test added to prevent recurrence
- [ ] Fix verified in all affected environments
- [ ] Related bugs checked for same root cause
- [ ] Changelog updated
- [ ] Backport plan if needed
- [ ] Customer communication if user-facing
```

### Refactoring

```markdown
## Refactoring Checklist

- [ ] Behavior unchanged (proven by tests)
- [ ] All tests still pass
- [ ] No performance regression
- [ ] Code is more maintainable after change
- [ ] Documentation updated for new structure
- [ ] No functionality changes snuck in
- [ ] Team consensus on approach
```

### Performance Optimization

```markdown
## Performance Optimization Checklist

- [ ] Baseline metrics established
- [ ] Improvement measured and documented
- [ ] No correctness regressions
- [ ] Performance tests added
- [ ] Profiling results included
- [ ] Resource usage validated
- [ ] Scalability impact assessed
```

---

## Continuous Improvement

### Review Metrics

**Track and improve:**
- Time to first review
- Time to merge after approval
- Number of review iterations
- Defects found in review vs production
- Test coverage trends
- Build time trends

**Discord's Approach:** Regular review of metrics drives process improvements and faster iteration cycles.

### Learning from Reviews

```markdown
## Post-Review Retrospective

### What Went Well
- What processes helped catch issues?
- What made the review smooth?

### What Could Improve
- What slowed down the review?
- What issues were missed?
- What automation could help?

### Action Items
- Process improvements to implement
- Team discussions to schedule
- Documentation to create/update
```

---

## Navigation Tips

**Searching this document (640+ lines):**

```bash
# Find all major sections
grep -n "^## " work-review.md

# Find specific checklist types
grep -i "feature change" work-review.md
grep -i "bug fix" work-review.md
grep -i "refactoring" work-review.md

# Find all checklists
grep "^\[ \]" work-review.md

# Find validation pipeline steps
grep -i "validation" work-review.md

# Find tool-specific guidance
grep -i "warning" work-review.md
grep -i "linter" work-review.md
```

---

## Remember

> *"The cost of fixing a bug increases exponentially with each phase it survives: design, implementation, testing, production. Code review is your best defense."*

**The Golden Rules:**
1. **Validate before requesting review** - All tests pass, project builds, no warnings
2. **Clean commits** - Only necessary files, no build artifacts
3. **Own your code** - You ship it, you support it
4. **Never dismiss warnings** - Every signal matters
5. **Whole project validation** - Ensure nothing breaks
6. **Fast feedback loops** - CI < 10 minutes
7. **Constructive reviews** - Help each other improve

**Quality is not a phase—it's a practice integrated into every step of development.**
