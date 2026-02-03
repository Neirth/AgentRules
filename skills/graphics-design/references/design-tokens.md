## Design System Architecture

### Airbnb's Living Organism Model

```
┌─────────────────────────────────────────────────────────────────┐
│              DESIGN SYSTEM LAYERS                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  AIRBNB DLS STRUCTURE ──────────────────────────────────────    │
│  │                                                              │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │  PRIMITIVES (Foundation)                                │  │
│  │ │  Color, Typography, Spacing, Shapes, Icons              │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                      │                                       │
│  │                      ▼                                       │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │  ELEMENTS (Atoms)                                       │  │
│  │ │  Buttons, Inputs, Labels, Icons                         │  │
│  │ │  Cannot be further broken down                          │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                      │                                       │
│  │                      ▼                                       │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │  COMPONENTS (Molecules)                                 │  │
│  │ │  Cards, Forms, Navigation, Modals                       │  │
│  │ │  Containers of system patterns                          │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                      │                                       │
│  │                      ▼                                       │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │  PATTERNS (Organisms)                                   │  │
│  │ │  Layouts, Page Templates, Flows                         │  │
│  │ │  Reusable solutions to common problems                  │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                                                              │
│  │ "Components are elements of a living organism. They have     │
│  │  a function and personality, can co-exist with others,       │
│  │  and can evolve (or die) independently."                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Design Tokens

```
┌─────────────────────────────────────────────────────────────────┐
│              DESIGN TOKENS                                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  "Design tokens are the visual design atoms of the design       │
│   system — specifically, they are named entities that store     │
│   visual design attributes."  — Salesforce                      │
│                                                                 │
│  TOKEN HIERARCHY ───────────────────────────────────────────    │
│  │                                                              │
│  │ GLOBAL TOKENS (Primitives)                                   │
│  │ ├── color.blue.500: #0066CC                                  │
│  │ ├── font.size.md: 16px                                       │
│  │ └── spacing.4: 16px                                          │
│  │                                                              │
│  │ ALIAS TOKENS (Semantic)                                      │
│  │ ├── color.primary: {color.blue.500}                          │
│  │ ├── color.error: {color.red.500}                             │
│  │ └── font.body: {font.size.md}                                │
│  │                                                              │
│  │ COMPONENT TOKENS (Specific)                                  │
│  │ ├── button.primary.background: {color.primary}               │
│  │ ├── button.primary.text: {color.on-primary}                  │
│  │ └── button.border-radius: {radius.md}                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  BENEFITS ──────────────────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Single source of truth                                     │
│  │ ✓ Easy theme switching (light/dark)                          │
│  │ ✓ Platform-agnostic (generate CSS, iOS, Android)             │
│  │ ✓ Consistent updates across entire system                    │
│  │ ✓ Design-development handoff clarity                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FORMAT EXAMPLE (JSON) ─────────────────────────────────────    │
│  │                                                              │
│  │ {                                                            │
│  │   "color": {                                                 │
│  │     "primary": {                                             │
│  │       "value": "#0066CC",                                    │
│  │       "type": "color",                                       │
│  │       "description": "Primary brand color"                   │
│  │     }                                                        │
│  │   }                                                          │
│  │ }                                                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---
