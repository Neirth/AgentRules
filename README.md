# AgentRules

**Professional-grade instructions and methodologies for Claude AI assistants**

AgentRules is a curated collection of domain-specific rules and skills designed to enhance Claude's capabilities across software engineering, mathematics, and design disciplines. Think of it as the `.claude` configuration for any project that wants to leverage specialized AI assistance.

## Philosophy

### Context-Aware Intelligence

AgentRules is built on the principle that AI assistants should **adapt their expertise** to the task at hand. Rather than being a generalist, Claude becomes a specialized expert by:

1. **Understanding First** - Reading project documentation and conventions before making changes
2. **Role Adaptation** - Switching between reverse engineer, QA engineer, software architect, ML engineer, mathematician, or designer based on what's needed
3. **Following Conventions** - Matching existing project patterns and style guides
4. **Minimal Intervention** - Making the smallest, most surgical changes necessary
5. **Verification-First** - Testing changes before considering them complete

### Quality Through Specialization

Each skill and rule set in this repository represents distilled knowledge from:

- **Industry Leaders**: Netflix, Spotify, Uber, AWS engineering practices
- **Academic Excellence**: MIT, Harvard, UPV research and methodologies
- **Foundational Works**: Gang of Four (Design Patterns), Robert C. Martin (Clean Code/SOLID), Eric Evans (Domain-Driven Design)
- **Modern Standards**: TDD, Event-Driven Architecture, Machine Learning best practices

## Repository Structure

```
AgentRules/
├── CLAUDE.md                   # Main instruction file for Claude
├── .mcp.json                   # MCP server configurations
├── rules/                      # Concise, actionable guidelines
│   ├── engineering/
│   │   └── general-engineering.md
│   ├── computer-science/
│   │   ├── reverse-engineering.md
│   │   ├── qa-engineering.md
│   │   ├── software-engineering.md
│   │   ├── formal-verification.md
│   │   └── work-review.md
│   ├── mathematical/
│   │   ├── machine-learning.md
│   │   └── classical-math.md
│   └── graphics-design/
│       └── graphics-design.md
└── skills/                     # Detailed methodologies and workflows
    ├── general-engineering/
    ├── reverse-engineering/
    ├── qa-engineering/
    ├── software-engineering/
    ├── formal-verification/
    ├── work-review/
    ├── machine-learning-engineering/
    ├── classical-mathematical/
    └── graphics-design/
```

**Note**: When integrated into your project, this repository becomes your `.claude/` directory, making all rules and skills available to Claude.

### Rules vs Skills

- **Rules** (`rules/`): Quick-reference guidelines automatically loaded for every task. Concise, practical, immediately applicable.
- **Skills** (`skills/`): Deep-dive methodologies invoked on-demand with `/skill-name`. Comprehensive workflows, patterns, and best practices.

## How to Use

### Option 1: Git Submodule (Recommended)

Add AgentRules as a submodule in your project's `.claude` directory:

```bash
# In your project root
git submodule add https://github.com/Neirth/AgentRules.git .claude
git submodule update --init --recursive
```

This makes the rules and skills available to Claude when working on your project.

### Option 2: Direct Clone

Clone AgentRules and rename to `.claude`:

```bash
# In your project root
git clone https://github.com/Neirth/AgentRules.git .claude
```

### Option 3: Template Integration

Copy specific rules and skills you need into your project's `.claude/` directory:

```bash
# Copy only what you need
mkdir -p .claude/rules/computer-science
cp path/to/AgentRules/rules/computer-science/software-engineering.md .claude/rules/computer-science/
```

### Using Skills

Once integrated, invoke skills by referencing them in your conversation with Claude using the `/skill-name` syntax. This instructs Claude to load the detailed methodology for that domain:

```
"Use /general-engineering to apply first principles analysis to this design"
"Apply /software-engineering to refactor this code following SOLID principles"
"Apply /qa-engineering to add comprehensive tests for this module"
"Use /reverse-engineering to analyze and reimplement this external library"
```

Skills can also be invoked through natural language that clearly indicates the need for that expertise (e.g., "review my code before pushing" will engage `/work-review`).

## Available Expertise

### Engineering Fundamentals

| Skill | Invocation | Use Case |
|-------|-----------|----------|
| **General Engineering** | `/general-engineering` | Universal engineering principles, first principles thinking, problem-solving methodology, professional practice (applicable to all engineering disciplines) |

### Computer Science

| Skill | Invocation | Use Case |
|-------|-----------|----------|
| **Reverse Engineering** | `/reverse-engineering` | Clean-room reimplementation, protocol analysis, legacy code understanding |
| **QA Engineering** | `/qa-engineering` | TDD, test coverage, mocking, chaos engineering, testing culture |
| **Software Engineering** | `/software-engineering` | SOLID principles, design patterns, DDD, clean architecture |
| **Formal Verification** | `/formal-verification` | Mathematical proof of code correctness, theorem proving, model checking (C/C++/Rust only) |
| **Work Review** | `/work-review` | Pre-push validation, code review, quality gates |

### Mathematical Sciences

| Skill | Invocation | Use Case |
|-------|-----------|----------|
| **Machine Learning Engineering** | `/machine-learning-engineering` | ML/DL with PyTorch/Scikit-Learn, model training, ONNX export |
| **Classical Mathematics** | `/classical-mathematical` | Numerical methods, optimization, simulation, mathematical modeling |

### Design

| Skill | Invocation | Use Case |
|-------|-----------|----------|
| **Graphics Design** | `/graphics-design` | UI/UX, design systems (Apple, Google, IBM, Microsoft, Netflix) |

## Configuration

### MCP Servers

AgentRules includes optional MCP (Model Context Protocol) server configurations in `.mcp.json` for enhanced capabilities:

- **chrome-devtools**: Browser automation and testing
- **docker**: Container management
- **expo**: React Native development

These are optional and can be customized based on your project needs.

## Contributing

AgentRules is designed to be a living repository of best practices. Contributions are welcome for:

- New domain-specific rules and skills
- Updates to existing methodologies
- Corrections and clarifications

Please ensure contributions:
- Follow the existing structure (rules/ vs skills/)
- Include clear, actionable guidance
- Reference authoritative sources where applicable
- Are tested with real-world Claude interactions

## Why AgentRules?

Traditional AI assistants provide general-purpose help. AgentRules transforms Claude into a **specialist on-demand**:

- **Consistency**: Same high-quality approaches across all your projects
- **Best Practices**: Distilled knowledge from industry and academia
- **Adaptability**: Right expertise for the right task
- **Efficiency**: Less explanation needed, better results faster
- **Quality**: Built-in review processes and verification steps
