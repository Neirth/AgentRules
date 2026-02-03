# Project Assistant

## CRITICAL: Read Repository Rules First

**BEFORE taking ANY action in this repository, you MUST:**

1. **Read ALL rule files** in the `rules/` directory:
   
   **Computer Science:**
   - `rules/computer-science/software-engineering.md` - Code design and implementation
   - `rules/computer-science/qa-engineering.md` - Testing requirements
   - `rules/computer-science/reverse-engineering.md` - Analyzing external code
   - `rules/computer-science/formal-verification.md` - Mathematical proof of correctness (C/C++/Rust)
   - `rules/computer-science/work-review.md` - Pre-push validation requirements
   
   **General Engineering:**
   - `rules/general-engineering/general-engineering.md` - Fundamental engineering principles
   - `rules/general-engineering/classical-math.md` - Mathematical modeling
   - `rules/general-engineering/machine-learning.md` - ML/DL tasks
   
   **Graphics Design:**
   - `rules/graphics-design/graphics-design.md` - UI/UX design

2. **Apply the rules**: Every action must comply with the relevant rules above.

**This is NOT optional.** The repository enforces these rules through tooling and hooks.

---

## Context Discovery

Before starting any task:

1. **Read `README.md`** for project purpose, tech stack, and setup
2. **Explore `docs/`** for architecture and design decisions
3. **Check configuration files** to understand the stack

## Available Skills

Invoke skills with `/skill-name` for specialized expertise:

- **`/computer-science`** - Software engineering, ML/DL, testing, reverse engineering, code review
- **`/general-engineering`** - Universal engineering principles, first principles thinking, analysis techniques
- **`/graphics-design`** - Visual design, typography, color theory, design systems

Each skill provides comprehensive guidance through its SKILL.md and detailed reference documentation.

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
├── general-engineering/        # Engineering & mathematics
│   ├── general-engineering.md
│   ├── classical-math.md
│   └── machine-learning.md
└── graphics-design/            # UI/UX design
    └── graphics-design.md
```

**Failure to follow these rules will result in:**
- Blocked commits from git hooks
- Failed CI/CD checks
- Rejected pull requests
