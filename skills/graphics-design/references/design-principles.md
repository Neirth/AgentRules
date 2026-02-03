## Core Design Principles

### Apple's Triad: Clarity, Deference, Depth

```
┌─────────────────────────────────────────────────────────────────┐
│              APPLE'S DESIGN PHILOSOPHY                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  CLARITY ───────────────────────────────────────────────────    │
│  │ • Text is legible at every size                              │
│  │ • Icons are precise and lucid                                │
│  │ • Adornments are subtle and appropriate                      │
│  │ • Focus on functionality drives the design                   │
│  │                                                              │
│  │ "Throughout the system, text is legible at every size,       │
│  │  icons are precise and lucid, adornments are subtle          │
│  │  and appropriate."                                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DEFERENCE ─────────────────────────────────────────────────    │
│  │ • Content is the interface                                   │
│  │ • UI helps people understand and interact with content       │
│  │ • Never compete with content                                 │
│  │ • Minimize visual clutter                                    │
│  │                                                              │
│  │ "The UI helps users focus on their content and tasks         │
│  │  by minimizing unnecessary visual clutter."                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DEPTH ─────────────────────────────────────────────────────    │
│  │ • Visual layers convey hierarchy                             │
│  │ • Realistic motion enhances understanding                    │
│  │ • Touch and discoverability heighten delight                 │
│  │ • Multi-dimensional experience guides users                  │
│  │                                                              │
│  │ "Depth is achieved through layering, shadows, and            │
│  │  visual effects, creating a sense of hierarchy."             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Microsoft Fluent: The Five Pillars

```
┌─────────────────────────────────────────────────────────────────┐
│              FLUENT DESIGN PILLARS                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌────────┐│
│  │  LIGHT  │  │  DEPTH  │  │ MOTION  │  │MATERIAL │  │ SCALE  ││
│  └────┬────┘  └────┬────┘  └────┬────┘  └────┬────┘  └───┬────┘│
│       │            │            │            │           │      │
│       ▼            ▼            ▼            ▼           ▼      │
│  Draws        Z-depth       Continuity   Translucent  Adapts   │
│  attention    layering      between      blurred      to form  │
│  illuminates  shadows       UI elements  surfaces     factors  │
│  information  elevation     transitions  (Acrylic)    & inputs │
│                                                                 │
│  REVEAL HIGHLIGHT:                                              │
│  Light follows cursor, illuminating nearby borders              │
│                                                                 │
│  ACRYLIC MATERIAL:                                              │
│  Translucent blur with noise effect for depth                   │
│                                                                 │
│  CONNECTED ANIMATIONS:                                          │
│  Elements appear to fly across app during transitions           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---
