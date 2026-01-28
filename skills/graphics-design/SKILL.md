---
name: graphics-design
description: Apply world-class graphic design principles following Apple HIG, Google Material Design, IBM Carbon, Airbnb DLS, Microsoft Fluent, and Netflix Hawkins design systems
user-invocable: true
---

# Graphics Design Engineering Rules

> *"Design is not just what it looks like and feels like. Design is how it works."*
> — Steve Jobs

## Purpose

These rules establish the methodology for creating world-class visual designs and design systems. Drawing from the design excellence of **Apple** (Human Interface Guidelines), **Google** (Material Design), **IBM** (Carbon Design System), **Airbnb** (Design Language System), **Microsoft** (Fluent Design), and **Netflix** (Hawkins), this guide covers visual hierarchy, typography, color theory, motion design, accessibility, and design system architecture.

---

## The Design System Pioneers

### Industry Leaders Comparison

```
┌─────────────────────────────────────────────────────────────────┐
│              DESIGN SYSTEM LANDSCAPE                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  APPLE (Human Interface Guidelines) ────────────────────────    │
│  │ Philosophy: "Clarity, Deference, Depth"                      │
│  │ Typeface: San Francisco                                      │
│  │ Key Feature: Dynamic Type, SF Symbols                        │
│  │ Platforms: iOS, macOS, watchOS, tvOS, visionOS               │
│  │ URL: developer.apple.com/design/human-interface-guidelines   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  GOOGLE (Material Design 3) ────────────────────────────────    │
│  │ Philosophy: "Material is the metaphor"                       │
│  │ Typeface: Roboto, Google Sans                                │
│  │ Key Feature: Dynamic Color, Design Tokens                    │
│  │ Platforms: Android, Web, Flutter, iOS                        │
│  │ URL: m3.material.io                                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  IBM (Carbon Design System) ────────────────────────────────    │
│  │ Philosophy: "Consistency, Scalability, Accessibility"        │
│  │ Typeface: IBM Plex                                           │
│  │ Key Feature: Design Tokens, WCAG AA Compliance               │
│  │ Platforms: Web (React, Angular, Vue, Svelte)                 │
│  │ URL: carbondesignsystem.com                                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  AIRBNB (Design Language System) ───────────────────────────    │
│  │ Philosophy: "Living Organism, not Atomic Design"             │
│  │ Typeface: Cereal                                             │
│  │ Key Feature: Platform-Agnostic Components                    │
│  │ Platforms: iOS, Android, Web                                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MICROSOFT (Fluent Design System) ──────────────────────────    │
│  │ Philosophy: "Light, Depth, Motion, Material, Scale"          │
│  │ Typeface: Segoe UI                                           │
│  │ Key Feature: Acrylic Material, Reveal Highlight              │
│  │ Platforms: Windows, Web, Mobile, Mixed Reality               │
│  │ URL: fluent2.microsoft.design                                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  NETFLIX (Hawkins) ─────────────────────────────────────────    │
│  │ Philosophy: "Content-First, Brand Consistency"               │
│  │ Typeface: Netflix Sans                                       │
│  │ Key Feature: Design Tokens across Web/iOS/Android/TV         │
│  │ Platforms: Web, iOS, Android, TV                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

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

## Typography

### The Type Scale

```
┌─────────────────────────────────────────────────────────────────┐
│              TYPOGRAPHY HIERARCHY                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  MATERIAL DESIGN 3 TYPE SCALE ──────────────────────────────    │
│  │                                                              │
│  │  DISPLAY    Large   57sp                                     │
│  │             Medium  45sp    Headlines, hero text             │
│  │             Small   36sp                                     │
│  │                                                              │
│  │  HEADLINE   Large   32sp                                     │
│  │             Medium  28sp    Section headers                  │
│  │             Small   24sp                                     │
│  │                                                              │
│  │  TITLE      Large   22sp                                     │
│  │             Medium  16sp    Card titles, dialogs             │
│  │             Small   14sp                                     │
│  │                                                              │
│  │  BODY       Large   16sp                                     │
│  │             Medium  14sp    Primary content                  │
│  │             Small   12sp                                     │
│  │                                                              │
│  │  LABEL      Large   14sp                                     │
│  │             Medium  12sp    Buttons, tabs, captions          │
│  │             Small   11sp                                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  APPLE TYPOGRAPHY BEST PRACTICES ───────────────────────────    │
│  │                                                              │
│  │ • Avoid light font weights for body text                     │
│  │ • Use medium, semibold, or bold for readability              │
│  │ • Support Dynamic Type for accessibility                     │
│  │ • Maintain hierarchy when users adjust text size             │
│  │ • Minimize number of typefaces                               │
│  │ • San Francisco is optimized for Apple displays              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  IBM PLEX PRINCIPLES ───────────────────────────────────────    │
│  │                                                              │
│  │ • Type tokens define consistent typography                   │
│  │ • Pre-set styles: font size, weight, line height             │
│  │ • Calibrated for readability across platforms                │
│  │ • Open-source, freely available                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Typography Rules

```markdown
## Typography Checklist

HIERARCHY
[ ] Clear visual distinction between heading levels
[ ] Body text optimized for reading (14-16px/sp)
[ ] Sufficient contrast between text and background
[ ] Line height: 1.4-1.6 for body text

READABILITY
[ ] Maximum 60-75 characters per line
[ ] Adequate paragraph spacing
[ ] Left-aligned for LTR languages (easier to read)
[ ] Avoid justified text on narrow columns

ACCESSIBILITY
[ ] Support for Dynamic Type / scalable fonts
[ ] Minimum 4.5:1 contrast ratio (WCAG AA)
[ ] 3:1 for large text (18pt+ or 14pt bold+)
[ ] Don't rely on font style alone to convey meaning

CONSISTENCY
[ ] Use design tokens for typography
[ ] Limited number of type sizes
[ ] Consistent font weights across platform
[ ] Unified type scale (display, headline, body, label)
```

---

## Color Theory

### Color Roles (Material Design 3)

```
┌─────────────────────────────────────────────────────────────────┐
│              COLOR SYSTEM ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  COLOR ROLES ───────────────────────────────────────────────    │
│  │                                                              │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │  PRIMARY          Main brand color, key actions         │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  ON PRIMARY       Text/icons on primary surfaces        │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  PRIMARY CONTAINER  Standout containers                 │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  SECONDARY        Less prominent components             │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  TERTIARY         Contrasting accents                   │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  ERROR            Error states and destructive actions  │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  SURFACE          Background surfaces                   │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  ON SURFACE       Text/icons on surface                 │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │  OUTLINE          Borders and dividers                  │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                                                              │
│  │ "Color roles are like the 'numbers' in paint-by-number.     │
│  │  They're the connective tissue between UI elements          │
│  │  and what color goes where."  — Material Design 3           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DYNAMIC COLOR (Material You) ──────────────────────────────    │
│  │                                                              │
│  │ • Colors adapt based on user's wallpaper                     │
│  │ • Personalized experiences with accessibility                │
│  │ • Tonal palettes ensure contrast compliance                  │
│  │ • Material Theme Builder generates palettes                  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Apple's Color Guidelines

```
┌─────────────────────────────────────────────────────────────────┐
│              APPLE COLOR PRINCIPLES                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SEMANTIC COLORS ───────────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Blue    → Primary actions (Save, Continue, Submit)         │
│  │ ✓ Red     → Destructive actions (Delete, Remove)             │
│  │ ✓ Green   → Success, positive confirmation                   │
│  │ ✓ Yellow  → Warnings, caution                                │
│  │ ✓ Gray    → Neutral, disabled states                         │
│  │                                                              │
│  │ "Avoid using the same color to indicate different things.    │
│  │  This makes your interface more intuitive and accessible."   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ACCESSIBILITY ─────────────────────────────────────────────    │
│  │                                                              │
│  │ • Test for colorblind users (protanopia, deuteranopia)       │
│  │ • Never rely on color alone to convey information            │
│  │ • Support Dark Mode and Increased Contrast modes             │
│  │ • System colors automatically adapt to appearance            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### IBM Carbon Color Tokens

```
┌─────────────────────────────────────────────────────────────────┐
│              IBM CARBON COLOR TOKENS                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TOKEN-BASED COLOR SYSTEM ──────────────────────────────────    │
│  │                                                              │
│  │ "Tokens are a method of abstracting color by role or         │
│  │  usage, independent of the actual color values."             │
│  │                                                              │
│  │ Benefits:                                                    │
│  │ • Efficient color updates within a theme                     │
│  │ • Easy switching between light/dark themes                   │
│  │ • Consistent application across UI                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONTRAST COMPLIANCE (WCAG 2.1 AA) ─────────────────────────    │
│  │                                                              │
│  │ Gray Scale:                                                  │
│  │ ├── Black text accessible on: Gray 10-50                     │
│  │ └── White text accessible on: Gray 60-100                    │
│  │                                                              │
│  │ Minimum Ratios:                                              │
│  │ ├── Normal text: 4.5:1                                       │
│  │ ├── Large text: 3:1                                          │
│  │ └── UI components: 3:1                                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Visual Hierarchy

### Netflix's Content-First Approach

```
┌─────────────────────────────────────────────────────────────────┐
│              VISUAL HIERARCHY PRINCIPLES                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  NETFLIX APPROACH ──────────────────────────────────────────    │
│  │                                                              │
│  │ Content-First Design:                                        │
│  │ ├── Large, vibrant images draw attention                     │
│  │ ├── Minimal text, content is the hero                        │
│  │ ├── Size, contrast, spacing guide navigation                 │
│  │ └── Dark interface keeps focus on colorful content           │
│  │                                                              │
│  │ Color Strategy:                                              │
│  │ ├── Black + White dominate (content focus)                   │
│  │ ├── Red for brand accents only (used sparingly)              │
│  │ └── Netflix Sans for brand consistency                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HIERARCHY TOOLS ───────────────────────────────────────────    │
│  │                                                              │
│  │ SIZE        Larger = More important                          │
│  │ WEIGHT      Bolder = More important                          │
│  │ COLOR       Higher contrast = More important                 │
│  │ POSITION    Top/Left (LTR) = Primary                         │
│  │ SPACING     More whitespace = More prominence                │
│  │ DEPTH       Elevated = More immediate                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  Z-INDEX LAYERING ──────────────────────────────────────────    │
│  │                                                              │
│  │ Layer 5: Modals, Dialogs           ████████████  (Highest)   │
│  │ Layer 4: Popups, Tooltips          ████████████              │
│  │ Layer 3: Navigation, Headers       ████████████              │
│  │ Layer 2: Cards, Elevated Content   ████████████              │
│  │ Layer 1: Content                   ████████████              │
│  │ Layer 0: Background Canvas         ████████████  (Lowest)    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

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

## Accessibility

### WCAG Compliance (IBM Carbon Standards)

```
┌─────────────────────────────────────────────────────────────────┐
│              ACCESSIBILITY REQUIREMENTS                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  "Accessible design not only helps users with disabilities;     │
│   it provides better user experiences for everyone."            │
│                                    — IBM Carbon Design System   │
│                                                                 │
│  WCAG 2.1 AA CHECKLIST ─────────────────────────────────────    │
│  │                                                              │
│  │ PERCEIVABLE                                                  │
│  │ [ ] Text alternatives for non-text content                   │
│  │ [ ] Captions for video/audio                                 │
│  │ [ ] Content adaptable (responsive, reflow)                   │
│  │ [ ] Sufficient color contrast (4.5:1 / 3:1)                  │
│  │                                                              │
│  │ OPERABLE                                                     │
│  │ [ ] Keyboard accessible (no mouse required)                  │
│  │ [ ] Enough time to read and interact                         │
│  │ [ ] No seizure-inducing content                              │
│  │ [ ] Clear navigation and wayfinding                          │
│  │ [ ] Visible focus indicators                                 │
│  │                                                              │
│  │ UNDERSTANDABLE                                               │
│  │ [ ] Readable text (language, abbreviations)                  │
│  │ [ ] Predictable navigation and behavior                      │
│  │ [ ] Input assistance (error prevention, suggestions)         │
│  │                                                              │
│  │ ROBUST                                                       │
│  │ [ ] Compatible with assistive technologies                   │
│  │ [ ] Valid HTML/semantic markup                               │
│  │ [ ] ARIA labels where needed                                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COLOR ACCESSIBILITY ───────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Never use color alone to convey information                │
│  │ ✓ Test with colorblind simulation tools                      │
│  │ ✓ Provide sufficient contrast in all themes                  │
│  │ ✓ Support system high-contrast modes                         │
│  │ ✓ Include patterns/icons alongside color coding              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FOCUS STATES ──────────────────────────────────────────────    │
│  │                                                              │
│  │ • Visible focus ring (2px minimum)                           │
│  │ • High contrast against background                           │
│  │ • Consistent across all interactive elements                 │
│  │ • Don't remove :focus-visible styles                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Motion Design

### Animation Principles

```
┌─────────────────────────────────────────────────────────────────┐
│              MOTION DESIGN                                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PURPOSE OF MOTION ─────────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Guide attention                                            │
│  │ ✓ Provide feedback                                           │
│  │ ✓ Show relationships                                         │
│  │ ✓ Create continuity                                          │
│  │ ✓ Delight (used sparingly)                                   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  MICROSOFT FLUENT MOTION ───────────────────────────────────    │
│  │                                                              │
│  │ PARALLAX:                                                    │
│  │ Background moves slower than foreground content              │
│  │ Creates depth perception                                     │
│  │                                                              │
│  │ CONNECTED ANIMATIONS:                                        │
│  │ Elements appear to fly across during transitions             │
│  │ Provides continuity between states                           │
│  │                                                              │
│  │ REVEAL:                                                      │
│  │ Light follows cursor, illuminating borders                   │
│  │ Creates responsive, alive feel                               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  TIMING & EASING ───────────────────────────────────────────    │
│  │                                                              │
│  │ DURATION                                                     │
│  │ ├── Micro interactions: 100-200ms                            │
│  │ ├── Simple transitions: 200-300ms                            │
│  │ ├── Complex animations: 300-500ms                            │
│  │ └── Page transitions: 300-500ms                              │
│  │                                                              │
│  │ EASING CURVES                                                │
│  │ ├── ease-out: Entering elements (fast start, slow end)       │
│  │ ├── ease-in: Exiting elements (slow start, fast end)         │
│  │ ├── ease-in-out: Moving elements (smooth both ends)          │
│  │ └── linear: Progress indicators only                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ACCESSIBILITY ─────────────────────────────────────────────    │
│  │                                                              │
│  │ • Respect prefers-reduced-motion                             │
│  │ • No essential info conveyed only through motion             │
│  │ • Avoid flashing (3 flashes/second max)                      │
│  │ • Provide pause/stop for auto-playing content                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

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

## Design Tools & Resources

### Industry Standard Tools

```
┌─────────────────────────────────────────────────────────────────┐
│              DESIGN TOOLS                                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  DESIGN                                                         │
│  ├── Figma (Industry standard, collaborative)                   │
│  ├── Sketch (macOS, established ecosystem)                      │
│  ├── Adobe XD (Adobe integration)                               │
│  └── Framer (Advanced prototyping)                              │
│                                                                 │
│  PROTOTYPING                                                    │
│  ├── Figma Prototyping                                          │
│  ├── Principle (macOS, micro-interactions)                      │
│  ├── ProtoPie (Complex interactions)                            │
│  └── Framer (Code-based prototypes)                             │
│                                                                 │
│  DEVELOPMENT                                                    │
│  ├── Storybook (Component documentation)                        │
│  ├── Zeroheight (Design system documentation)                   │
│  └── Supernova (Design-to-code)                                 │
│                                                                 │
│  HANDOFF                                                        │
│  ├── Figma Dev Mode                                             │
│  ├── Zeplin                                                     │
│  └── Avocode                                                    │
│                                                                 │
│  RESOURCES FROM LEADERS ────────────────────────────────────    │
│  │                                                              │
│  │ Apple:    SF Symbols, Design Resources (Sketch, Figma)       │
│  │ Google:   Material Theme Builder, Figma UI Kit               │
│  │ IBM:      Carbon Figma Kit, Carbon React                     │
│  │ Microsoft: Fluent UI, Fluent 2 Figma Kit                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Checklist

### Before Designing
- [ ] Understand brand guidelines
- [ ] Define design tokens (colors, typography, spacing)
- [ ] Establish visual hierarchy principles
- [ ] Set accessibility requirements (WCAG level)
- [ ] Choose platform approach (native vs cross-platform)

### During Design
- [ ] Use consistent spacing (8px grid)
- [ ] Apply typography scale correctly
- [ ] Check color contrast ratios
- [ ] Design all states (default, hover, active, disabled, error)
- [ ] Include focus states for keyboard navigation

### Before Handoff
- [ ] Test with accessibility tools
- [ ] Verify responsive behavior
- [ ] Document component specifications
- [ ] Create design tokens file
- [ ] Test with prefers-reduced-motion

---

## Remember

> *"Good design is obvious. Great design is transparent."*
> — Joe Sparano

> *"Accessible design not only helps users with disabilities; it provides better user experiences for everyone."*
> — IBM Carbon Design System

> *"The UI helps users focus on their content and tasks by minimizing unnecessary visual clutter."*
> — Apple Human Interface Guidelines

**The Golden Rules:**
1. Content first, chrome second
2. Consistency builds trust
3. Accessibility is not optional
4. Motion should inform, not distract
5. Design tokens are your single source of truth
6. Test on real devices, not just simulators
