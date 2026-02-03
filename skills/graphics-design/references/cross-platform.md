## Cross-Platform Design

### Platform-Agnostic Approach (Airbnb)

```
┌─────────────────────────────────────────────────────────────────┐
│              CROSS-PLATFORM STRATEGY                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  AIRBNB'S APPROACH ─────────────────────────────────────────    │
│  │                                                              │
│  │ "Most components work and look exactly the same on iOS       │
│  │  and Android. We look for design solutions that feel at      │
│  │  home across platforms."                                     │
│  │                                                              │
│  │ SHARED:                                                      │
│  │ ├── Visual design (colors, typography, spacing)              │
│  │ ├── Component behavior                                       │
│  │ ├── Information architecture                                 │
│  │ └── Responsive layouts                                       │
│  │                                                              │
│  │ PLATFORM-SPECIFIC:                                           │
│  │ ├── Navigation patterns                                      │
│  │ ├── System iconography                                       │
│  │ ├── Contextual actions                                       │
│  │ └── Gesture interactions                                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  NETFLIX HAWKINS MULTI-PLATFORM ────────────────────────────    │
│  │                                                              │
│  │ Core team builds components for:                             │
│  │ ├── Web                                                      │
│  │ ├── iOS                                                      │
│  │ ├── Android                                                  │
│  │ └── TV                                                       │
│  │                                                              │
│  │ Shared across platforms:                                     │
│  │ ├── Design tokens                                            │
│  │ ├── Icons and illustrations                                  │
│  │ ├── Brand identity                                           │
│  │ └── Accessibility foundations                                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  RESPONSIVE DESIGN ─────────────────────────────────────────    │
│  │                                                              │
│  │ Breakpoints (Material Design 3):                             │
│  │ ├── Compact:  < 600dp   (Phones)                             │
│  │ ├── Medium:   600-840dp (Tablets portrait, foldables)        │
│  │ ├── Expanded: > 840dp   (Tablets landscape, desktop)         │
│  │                                                              │
│  │ Layout Grid:                                                 │
│  │ ├── 4 columns (compact)                                      │
│  │ ├── 8 columns (medium)                                       │
│  │ └── 12 columns (expanded)                                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---
