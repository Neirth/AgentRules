# Graphics Design Rules

When creating visual designs or design systems:

## Core Principles

1. **Clarity** - Interfaces must be legible and easy to understand
2. **Deference** - UI serves content, never competes with it
3. **Consistency** - Same patterns for same problems
4. **Accessibility** - Design for everyone, not just the majority

## Typography

- Use established type scale (Display, Headline, Title, Body, Label)
- Maximum 60-75 characters per line for readability
- Minimum 4.5:1 contrast ratio (WCAG AA)
- Support Dynamic Type / scalable fonts
- Avoid light font weights for body text

## Color

- Define semantic color roles (primary, secondary, error, surface)
- Use design tokens, not hardcoded values
- Never use color alone to convey meaning
- Test with colorblind simulation tools
- Support light/dark themes

## Visual Hierarchy

- Size, weight, color, position, spacing indicate importance
- Content-first: minimize UI chrome
- Use elevation/shadows for depth and focus
- Maintain consistent spacing (8px grid)

## Accessibility (WCAG 2.1 AA)

- 4.5:1 contrast for normal text, 3:1 for large text
- Visible focus indicators (2px minimum)
- Keyboard navigable (no mouse required)
- Respect `prefers-reduced-motion`
- Provide text alternatives for images

## Motion

- Purpose: guide attention, provide feedback, show relationships
- Duration: 100-200ms micro, 200-300ms simple, 300-500ms complex
- Easing: ease-out (enter), ease-in (exit), ease-in-out (move)
- No flashing content (max 3/second)

## Design Tokens

```
Global   → color.blue.500: #0066CC
Alias    → color.primary: {color.blue.500}
Component → button.background: {color.primary}
```

## Cross-Platform

- Shared: visual design, tokens, icons, accessibility
- Platform-specific: navigation, gestures, system icons

**For detailed guidelines:** Use `/graphics-design` skill
