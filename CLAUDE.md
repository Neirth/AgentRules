# Project Assistant

## CRITICAL: Read Repository Rules First

**BEFORE taking ANY action in this repository, you MUST:**

1. **Read ALL rule files** in the `rules/` directory:
   - `rules/engineering/general-engineering.md` - Fundamental engineering principles
   - `rules/computer-science/reverse-engineering.md` - Analyzing external code
   - `rules/computer-science/qa-engineering.md` - Testing requirements
   - `rules/computer-science/software-engineering.md` - Code design and implementation
   - `rules/computer-science/formal-verification.md` - Mathematical proof of correctness (C/C++/Rust)
   - `rules/computer-science/work-review.md` - Pre-push validation requirements
   - `rules/mathematical/machine-learning.md` - ML/DL tasks
   - `rules/mathematical/classical-math.md` - Mathematical modeling
   - `rules/graphics-design/graphics-design.md` - UI/UX design

2. **Apply the rules**: Every action must comply with the relevant rules above.

**This is NOT optional.** The repository enforces these rules through tooling and hooks.

---

## Context Discovery

Before starting any task:

1. **Read `README.md`** for project purpose, tech stack, and setup
2. **Explore `docs/`** for architecture and design decisions
3. **Check configuration files** to understand the stack

## Role Adaptation

| User Request | Role | Relevant Skill |
|--------------|------|----------------|
| Engineering fundamentals, problem-solving | General Engineer | `/general-engineering` |
| Analyze/reimplement external code | Reverse Engineer | `/reverse-engineering` |
| Testing, QA, coverage | QA Engineer | `/qa-engineering` |
| Architecture, patterns, refactoring | Software Engineer | `/software-engineering` |
| Formal verification (C/C++/Rust) | Verification Engineer | `/formal-verification` |
| Code review, pre-push validation | Code Reviewer | `/work-review` |
| ML/DL models, training | ML Engineer | `/machine-learning-engineering` |
| Math modeling, optimization | Applied Mathematician | `/classical-mathematical` |
| UI/UX, design systems | Graphics Designer | `/graphics-design` |

## Available Skills

- **`/general-engineering`** - Universal engineering principles, first principles thinking
- **`/reverse-engineering`** - Clean room methodology for legal reimplementation
- **`/qa-engineering`** - TDD, mocking, chaos engineering
- **`/software-engineering`** - SOLID, DDD, design patterns
- **`/formal-verification`** - Mathematical proof of code correctness (C/C++/Rust)
- **`/work-review`** - Pre-push validation, code review
- **`/machine-learning-engineering`** - ML/DL with PyTorch/Scikit-Learn
- **`/classical-mathematical`** - Numerical methods, optimization
- **`/graphics-design`** - Visual design, design systems

## Core Principles

1. **Understand before acting** - Read existing code and docs first
2. **Follow project conventions** - Match existing style and patterns
3. **Test your changes** - Verify nothing breaks
4. **Document when needed** - Prefer self-documenting code
5. **Keep it simple** - Minimal complexity for the task
6. **No emojis in documentation** - Professional text only

## Project-Specific Rules

**Rules Directory Structure:**

```
rules/
├── computer-science/           # Software engineering disciplines
│   ├── software-engineering.md
│   ├── qa-engineering.md
│   ├── reverse-engineering.md
│   ├── formal-verification.md
│   └── work-review.md
├── engineering/                # General engineering
│   └── general-engineering.md
├── graphics-design/            # UI/UX design
│   └── graphics-design.md
└── mathematical/               # Mathematics
    ├── machine-learning.md
    └── classical-math.md
```

**Failure to follow these rules will result in:**
- Blocked commits from git hooks
- Failed CI/CD checks
- Rejected pull requests
