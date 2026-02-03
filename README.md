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
│   ├── engineering/            # All engineering disciplines unified
│   │   ├── fundamentals/
│   │   │   └── general-engineering.md
│   │   ├── software/
│   │   │   ├── software-engineering.md
│   │   │   ├── qa-engineering.md
│   │   │   ├── reverse-engineering.md
│   │   │   ├── formal-verification.md
│   │   │   └── work-review.md
│   │   ├── machine-learning/
│   │   │   └── machine-learning.md
│   │   └── graphics/
│   │       └── graphics-design.md
│   └── mathematical/           # Pure mathematics (non-engineering)
│       └── classical-math.md
└── skills/                     # Detailed methodologies and workflows
    ├── computer-science/       # Computer science and software engineering
    │   ├── SKILL.md
    │   └── capabilities/
    │       ├── machine-learning-engineering.md
    │       ├── qa-engineering.md
    │       ├── reverse-engineering.md
    │       ├── software-engineering.md
    │       └── work-review.md
    ├── general-engineering/    # Universal engineering principles
    │   ├── SKILL.md
    │   └── capabilities/
    │       ├── classical-mathematical.md
    │       ├── formal-verification.md
    │       └── qa-engineering.md
    └── graphics-design/        # Visual design and design systems
        └── SKILL.md
```

**Note**: When integrated into your project, this repository becomes your `.claude/` directory, making all rules and skills available to Claude.

### Skills Organization

Skills are organized into three main categories:

- **computer-science** - Computer science and software engineering capabilities (machine learning, QA, reverse engineering, software engineering, code review)
- **general-engineering** - Universal engineering principles and foundational methodologies (classical mathematics, formal verification, QA)
- **graphics-design** - Visual design and design systems following industry best practices

Each skill category contains a main SKILL.md and a `capabilities/` directory with detailed capability documentation.

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
mkdir -p .claude/rules/engineering/software
cp path/to/AgentRules/rules/engineering/software/software-engineering.md .claude/rules/engineering/software/
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

AgentRules includes MCP (Model Context Protocol) server configurations in `.mcp.json` for enhanced capabilities:

#### Currently Configured MCPs

| MCP Server | Type | Purpose | Configuration |
| --- | --- | --- | --- |
| **maestro_testing** | Local (STDIO) | Mobile app testing automation | `command: maestro` with `mcp` args |
| **docker_infrastructure** | Local (Docker) | Container management, logs, service control | Docker daemon socket mounted at `/var/run/docker.sock` |
| **stitch_graphics** | Remote (HTTP + mcp-remote) | Google Stitch graphics & design services | OAuth-enabled via `mcp-remote` bridge |

#### Setup Instructions

##### Docker Infrastructure

The Docker MCP requires access to your Docker daemon:

```bash
# Ensure Docker socket is accessible
ls -la /var/run/docker.sock

# If permission denied, add your user to docker group
sudo usermod -aG docker $USER
newgrp docker
```

##### Stitch Graphics (Remote Server)

Set your API key as an environment variable:

```bash
export STITCH_API_KEY="your-api-key-here"

# Or add to ~/.zshrc for persistence
echo 'export STITCH_API_KEY="your-api-key-here"' >> ~/.zshrc
source ~/.zshrc
```

The `mcp-remote` wrapper automatically:

- Manages OAuth flows and token storage in `~/.mcp-auth/`
- Handles credential refresh
- Provides secure header injection (`X-Goog-Api-Key`)

Then set required environment variables before launching Claude/Cursor.

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
