# Agent Rules Repository

This repository contains skills and rules for Claude Code agents, providing expertise in computer science and mathematical domains.

## Structure

```
.claude/
├── skills/                          # Detailed methodologies (invoke with /skill-name)
│   ├── reverse-engineering/         # Clean room reverse engineering
│   ├── qa-engineering/              # Testing and QA practices
│   ├── software-engineering/        # Design patterns and architecture
│   ├── machine-learning-engineering/ # ML/DL with PyTorch + ONNX
│   └── classical-mathematical/      # Mathematical modeling
│
└── rules/                           # Concise guidelines (auto-loaded)
    ├── computer-science/
    │   ├── reverse-engineering.md
    │   ├── qa-engineering.md
    │   └── software-engineering.md
    └── mathematical/
        ├── machine-learning.md
        └── classical-math.md
```

## Usage

### Skills (Detailed Methodologies)

Invoke skills for comprehensive guidance:

- `/reverse-engineering` - Clean room methodology for legal reimplementation
- `/qa-engineering` - TDD, mocking, chaos engineering practices
- `/software-engineering` - SOLID, DDD, design patterns
- `/machine-learning-engineering` - ML/DL with mandatory ONNX export
- `/classical-mathematical` - Numerical methods, optimization, simulation

### Rules (Auto-Loaded Guidelines)

Rules in `.claude/rules/` are automatically applied based on context:

- `computer-science/` - Software development guidelines
- `mathematical/` - Mathematical modeling guidelines

## Sources

Skills are based on research from:

- **Computer Science**: IBM BIOS reverse engineering, WINE Project, Netflix, Google, AWS, Microsoft
- **Mathematical**: MIT, Harvard, Oxford, Berkeley, Peking University, UPV Valencia
- **ML/DL**: Hinton, LeCun, Bengio (Turing Award), Andrew Ng, Andrej Karpathy
