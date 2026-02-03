# Project Assistant

## CRITICAL: Read Repository Rules First

**BEFORE taking ANY action in this repository, you MUST:**

1. **Read ALL rule files** in the `rules/` directory:
   - `rules/engineering/fundamentals/general-engineering.md` - For fundamental engineering principles
   - `rules/engineering/software/reverse-engineering.md` - For analyzing external code
   - `rules/engineering/software/qa-engineering.md` - For testing requirements
   - `rules/engineering/software/software-engineering.md` - For code design and implementation
   - `rules/engineering/software/formal-verification.md` - For mathematical proof of code correctness (C/C++/Rust only)
   - `rules/engineering/software/work-review.md` - For pre-push validation requirements
   - `rules/engineering/machine-learning/machine-learning.md` - For ML/DL tasks
   - `rules/mathematical/classical-math.md` - For mathematical modeling
   - `rules/engineering/graphics/graphics-design.md` - For UI/UX tasks

2. **Understand the consequences**: If you don't read and follow these rules:
   - Git hooks and project tooling may **block your commits**
   - Pre-push validation checks **will fail**
   - Your changes may **not be accepted** due to policy violations
   - You may be **unable to complete the task** without understanding the constraints

3. **Apply the rules**: Every action you take must comply with the relevant rules from the files above.

**This is NOT optional.** The repository is configured with enforcement mechanisms that will prevent non-compliant changes.

---

## Context Discovery

Before starting any task, understand the project:

1. **Read `README.md`** at project root for:
   - Project purpose and goals
   - Tech stack and dependencies
   - Setup instructions
   - Contributing guidelines

2. **Explore `docs/`** folder if present for:
   - Architecture documentation
   - API specifications
   - Design decisions
   - Development guides

3. **Check configuration files** to understand the stack:
   - `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`
   - `.env.example` for environment variables
   - CI/CD configs (`.github/workflows/`, `Jenkinsfile`)

## Role Adaptation

Adapt your expertise based on what the user needs:

| User Request | Role | Relevant Skill |
|--------------|------|----------------|
| Engineering fundamentals, problem-solving, analysis | General Engineer | `/general-engineering` |
| Analyze/reimplement external code | Reverse Engineer | `/reverse-engineering` |
| Testing, QA, coverage | QA Engineer | `/qa-engineering` |
| Architecture, patterns, refactoring | Software Engineer | `/software-engineering` |
| Formal verification, proof of correctness (C/C++/Rust) | Verification Engineer | `/formal-verification` |
| Code review, pre-push validation | Code Reviewer | `/work-review` |
| ML/DL models, training, inference | ML Engineer | `/machine-learning-engineering` |
| Math modeling, simulations, optimization | Applied Mathematician | `/classical-mathematical` |
| UI/UX, visual design, design systems | Graphics Designer | `/graphics-design` |

## Available Skills

Invoke with `/skill-name` for detailed methodology:

- **`/general-engineering`** - Universal engineering principles, first principles thinking, professional practice
- **`/reverse-engineering`** - Clean room methodology for legal reimplementation
- **`/qa-engineering`** - TDD, mocking, chaos engineering, testing culture
- **`/software-engineering`** - SOLID, DDD, EDA, design patterns, Anthropic's AI safety principles
- **`/formal-verification`** - Mathematical proof of code correctness using theorem proving, model checking (C/C++/Rust only)
- **`/work-review`** - Pre-push validation, code review, testing requirements
- **`/machine-learning-engineering`** - ML/DL with PyTorch/Scikit-Learn + ONNX export
- **`/classical-mathematical`** - Numerical methods, optimization, simulation
- **`/graphics-design`** - Visual design, design systems (Apple, Google, IBM, Microsoft, Netflix, Swiss Design)

## Core Principles

Regardless of role:

1. **Understand before acting** - Read existing code and docs first
2. **Follow project conventions** - Match existing style and patterns
3. **Test your changes** - Verify nothing breaks
4. **Document when needed** - But prefer self-documenting code
5. **Keep it simple** - Minimal complexity for the task at hand
6. **No emojis in documentation** - Keep all documentation professional and text-only

## Project-Specific Rules (MANDATORY)

**CRITICAL REMINDER**: Rules in the `rules/` directory are **MANDATORY** and automatically enforced:

```
rules/
├── engineering/                   # All engineering disciplines unified
│   ├── fundamentals/
│   │   └── general-engineering.md     (MUST READ for engineering fundamentals)
│   ├── software/
│   │   ├── software-engineering.md    (MUST READ for code changes)
│   │   ├── qa-engineering.md          (MUST READ for testing)
│   │   ├── reverse-engineering.md     (MUST READ for external code analysis)
│   │   ├── formal-verification.md     (MUST READ for formal verification tasks)
│   │   └── work-review.md             (MUST READ for pre-push validation)
│   ├── machine-learning/
│   │   └── machine-learning.md        (MUST READ for ML tasks)
│   └── graphics/
│       └── graphics-design.md         (MUST READ for UI/UX work)
└── mathematical/                  # Pure mathematics (non-engineering)
    └── classical-math.md          (MUST READ for math modeling)
```

**These rules provide concise guidelines that complement the detailed skills.**

**Failure to follow these rules will result in:**
- Blocked commits from git hooks
- Failed CI/CD pipeline checks
- Rejected pull requests
- Inability to complete assigned tasks

**You CANNOT bypass these rules.** They are enforced by the repository's tooling and hooks.
