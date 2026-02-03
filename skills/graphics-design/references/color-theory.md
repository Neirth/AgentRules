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

## Pantone Matching System (PMS)

### The Industry Standard for Color

```
┌─────────────────────────────────────────────────────────────────┐
│              PANTONE COLOR SYSTEM                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  "Since 1963, the Pantone Matching System has become the        │
│   industry standard for designers, agencies, and printing       │
│   companies worldwide."                                         │
│                                                                 │
│  WHAT IS PANTONE ──────────────────────────────────────────    │
│  │                                                              │
│  │ The Pantone Matching System (PMS) is a standardized color    │
│  │ reproduction system with nearly 5,000 color variations.      │
│  │                                                              │
│  │ Key Benefits:                                                │
│  │ ├── Universal standard across industries                     │
│  │ ├── Exact color reproduction regardless of equipment         │
│  │ ├── Cross-manufacturer consistency                           │
│  │ └── Physical color swatches for accurate matching            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COLOR NAMING CONVENTION ──────────────────────────────────    │
│  │                                                              │
│  │ Format: PMS [Number] [Suffix]                                │
│  │                                                              │
│  │ Suffixes:                                                    │
│  │ ├── C = Coated paper (glossy, vibrant)                       │
│  │ ├── U = Uncoated paper (matte, muted)                        │
│  │ ├── M = Matte paper                                          │
│  │ ├── CP = Coated Process (CMYK simulation)                    │
│  │ └── TPX/TCX = Textile (fabric colors)                        │
│  │                                                              │
│  │ Examples:                                                    │
│  │ ├── PMS 186 C (Coated red)                                   │
│  │ ├── PMS 286 U (Uncoated blue)                                │
│  │ └── PMS 1837 (Tiffany Blue - custom)                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  THE 14 BASE COLORS ───────────────────────────────────────    │
│  │                                                              │
│  │ All 1,114+ Pantone colors are created by mixing              │
│  │ these 14 base colors in different formulas:                  │
│  │                                                              │
│  │ PANTONE Yellow          PANTONE Warm Red                     │
│  │ PANTONE Yellow 012      PANTONE Rubine Red                   │
│  │ PANTONE Orange 021      PANTONE Rhodamine Red                │
│  │ PANTONE Bright Red      PANTONE Purple                       │
│  │ PANTONE Red 032         PANTONE Violet                       │
│  │ PANTONE Process Blue    PANTONE Blue 072                     │
│  │ PANTONE Green           PANTONE Reflex Blue                  │
│  │ PANTONE Black           PANTONE Trans. White                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Famous Brand Pantone Colors

```
┌─────────────────────────────────────────────────────────────────┐
│              ICONIC BRAND COLORS                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  TRADEMARKED PANTONE COLORS ───────────────────────────────    │
│  │                                                              │
│  │ Brand           │ PMS Code    │ Notes                        │
│  │ ────────────────┼─────────────┼────────────────────────────  │
│  │ Tiffany & Co.   │ PMS 1837    │ Custom color, trademarked    │
│  │ Coca-Cola       │ PMS 484 C   │ "Coca-Cola Red"              │
│  │ McDonald's      │ PMS 123 C   │ Golden Arches yellow         │
│  │ McDonald's      │ PMS 485 C   │ McDonald's red               │
│  │ Starbucks       │ PMS 3425 C  │ "Starbucks Green"            │
│  │ Target          │ PMS 186 C   │ "Target Red"                 │
│  │ UPS             │ PMS 476 C   │ "Pullman Brown"              │
│  │ Home Depot      │ PMS 165 C   │ Orange                       │
│  │ T-Mobile        │ PMS 676 C   │ Magenta                      │
│  │ Barbie          │ PMS 219 C   │ "Barbie Pink"                │
│  │ John Deere      │ PMS 364 C   │ Green (trademarked combo)    │
│  │ Cadbury         │ PMS 2685 C  │ Purple                       │
│  │ Minions         │ PMS 123 C   │ "Minion Yellow" (Universal)  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  GOVERNMENT & OFFICIAL USE ────────────────────────────────    │
│  │                                                              │
│  │ PMS colors are used in legislation and standards:            │
│  │ ├── US state flags (e.g., Texas)                             │
│  │ ├── National flags (Canada, South Korea)                     │
│  │ ├── FIA racing standards                                     │
│  │ └── Military standards                                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PANTONE COLOR OF THE YEAR ────────────────────────────────    │
│  │                                                              │
│  │ Annual color trend announcement (since 2000):                │
│  │                                                              │
│  │ 2026: Cloud Dancer (White)     17-1101                       │
│  │ 2025: Mocha Mousse (Brown)     17-1230                       │
│  │ 2024: Peach Fuzz               13-1023                       │
│  │ 2023: Viva Magenta             18-1750                       │
│  │ 2022: Very Peri (Periwinkle)   17-3938                       │
│  │                                                              │
│  │ "Trademarked colors are not owning a color—they allow        │
│  │  a brand to use specific shades within their industry        │
│  │  to prevent consumer confusion."                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### PMS vs Digital Colors

```
┌─────────────────────────────────────────────────────────────────┐
│              COLOR SPACE CONVERSIONS                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  COLOR SPACES OVERVIEW ────────────────────────────────────    │
│  │                                                              │
│  │ PANTONE (PMS)   → Physical ink mixing, spot colors           │
│  │ CMYK            → Print (Cyan, Magenta, Yellow, Black)       │
│  │ RGB             → Screen (Red, Green, Blue)                  │
│  │ HEX             → Web (Hexadecimal RGB)                      │
│  │ HSL/HSB         → Design tools (Hue, Saturation, Lightness)  │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  PMS vs CMYK ──────────────────────────────────────────────    │
│  │                                                              │
│  │ PANTONE (Spot Color):                                        │
│  │ ├── Pre-mixed ink, exact color every time                    │
│  │ ├── Vibrant colors impossible in CMYK (neons, metallics)     │
│  │ ├── More expensive (separate plate per color)                │
│  │ └── Best for: Brand colors, packaging, logos                 │
│  │                                                              │
│  │ CMYK (Process Color):                                        │
│  │ ├── Four inks combined to create colors                      │
│  │ ├── Color may vary between print runs                        │
│  │ ├── More economical for full-color printing                  │
│  │ └── Best for: Photos, complex graphics, large runs           │
│  │                                                              │
│  │ "With PMS, each design can be reproduced with reliability    │
│  │  of consistency in color that is not possible with CMYK."    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONVERSION LIMITATIONS ───────────────────────────────────    │
│  │                                                              │
│  │ ⚠️  Pantone → RGB/HEX is APPROXIMATE, not exact              │
│  │ ⚠️  Some PMS colors have no RGB/CMYK equivalent              │
│  │ ⚠️  Metallics, neons cannot be shown on screen               │
│  │ ⚠️  Always verify with physical Pantone swatch               │
│  │                                                              │
│  │ Conversion Example:                                          │
│  │ PMS 186 C (Coca-Cola Red)                                    │
│  │ ├── HEX: #C8102E                                             │
│  │ ├── RGB: 200, 16, 46                                         │
│  │ └── CMYK: 2, 100, 85, 6                                      │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  WHEN TO USE PANTONE ──────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Brand identity (logos, corporate colors)                   │
│  │ ✓ Packaging and product design                               │
│  │ ✓ Signage and environmental graphics                         │
│  │ ✓ Merchandise and promotional items                          │
│  │ ✓ When exact color match is critical                         │
│  │ ✓ Textile and fashion design                                 │
│  │                                                              │
│  │ ✗ Digital-only projects (use HEX/RGB)                        │
│  │ ✗ Full-color photography (use CMYK)                          │
│  │ ✗ Low-budget print jobs (CMYK is cheaper)                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Pantone Tools & Resources

```
┌─────────────────────────────────────────────────────────────────┐
│              PANTONE TOOLS                                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PHYSICAL TOOLS ───────────────────────────────────────────    │
│  │                                                              │
│  │ PANTONE FORMULA GUIDE:                                       │
│  │ Fan deck with color swatches and ink formulas                │
│  │ ├── Coated (C) edition                                       │
│  │ └── Uncoated (U) edition                                     │
│  │                                                              │
│  │ PANTONE COLOR BRIDGE:                                        │
│  │ Shows PMS colors with closest CMYK/RGB equivalents           │
│  │                                                              │
│  │ PANTONE SOLID CHIPS:                                         │
│  │ Tear-out chips for client approval                           │
│  │                                                              │
│  │ PANTONE FASHION + HOME:                                      │
│  │ TPX/TCX colors for textiles and interiors                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DIGITAL TOOLS ────────────────────────────────────────────    │
│  │                                                              │
│  │ PANTONE CONNECT:                                             │
│  │ ├── Digital color library (subscription)                     │
│  │ ├── Integrations: Adobe, Figma, Sketch                       │
│  │ ├── Color matching from photos                               │
│  │ └── Palette creation tools                                   │
│  │                                                              │
│  │ PANTONE COLOR FINDER:                                        │
│  │ pantone.com/color-finder                                     │
│  │ ├── Search by number or name                                 │
│  │ ├── View RGB/HEX/CMYK conversions                            │
│  │ └── Find similar colors                                      │
│  │                                                              │
│  │ Design Software Libraries:                                   │
│  │ ├── Adobe CC: Built-in Pantone libraries                     │
│  │ ├── Figma: Pantone Connect plugin                            │
│  │ └── Sketch: Pantone plugin available                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMMON REFERENCE COLORS ──────────────────────────────────    │
│  │                                                              │
│  │ RED FAMILY:                                                  │
│  │ PMS 186 C  │ #C8102E │ Bright red (Target, Texas Flag)       │
│  │ PMS 485 C  │ #DA291C │ Warm red (McDonald's)                 │
│  │ PMS 1788 C │ #E4002B │ Scarlet (Ferrari-like)                │
│  │                                                              │
│  │ BLUE FAMILY:                                                 │
│  │ PMS 286 C  │ #0032A0 │ Royal blue (classic corporate)        │
│  │ PMS 300 C  │ #0057B8 │ Process blue                          │
│  │ PMS 072 C  │ #10069F │ Reflex blue (deep)                    │
│  │                                                              │
│  │ GREEN FAMILY:                                                │
│  │ PMS 349 C  │ #007A33 │ Forest green                          │
│  │ PMS 3425 C │ #006241 │ Starbucks green                       │
│  │ PMS 355 C  │ #009639 │ Bright green                          │
│  │                                                              │
│  │ YELLOW/ORANGE FAMILY:                                        │
│  │ PMS 123 C  │ #FFC72C │ Golden yellow (McDonald's, Minions)   │
│  │ PMS 116 C  │ #FFCD00 │ Bright yellow                         │
│  │ PMS 165 C  │ #FF6900 │ Orange (Home Depot)                   │
│  │                                                              │
│  │ NEUTRAL FAMILY:                                              │
│  │ PMS Black C│ #2D2926 │ Rich black                            │
│  │ PMS Cool Gray 11 C │ #53565A │ Dark gray                     │
│  │ PMS 877 C  │ Metallic │ Silver                               │
│  │ PMS 871 C  │ Metallic │ Gold                                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Brand Color Specification

```
┌─────────────────────────────────────────────────────────────────┐
│              DOCUMENTING BRAND COLORS                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BRAND COLOR SPECIFICATION TEMPLATE ───────────────────────    │
│  │                                                              │
│  │ For each brand color, document:                              │
│  │                                                              │
│  │ ┌─────────────────────────────────────────────────────────┐  │
│  │ │ COLOR NAME: Primary Blue                                │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │ PANTONE:    PMS 286 C (Coated)                          │  │
│  │ │             PMS 286 U (Uncoated)                        │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │ PRINT:      CMYK 100/75/0/0                             │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │ DIGITAL:    HEX #0032A0                                 │  │
│  │ │             RGB 0/50/160                                │  │
│  │ │             HSL 221°/100%/31%                           │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │ USAGE:      Primary CTAs, headers, logo                 │  │
│  │ ├─────────────────────────────────────────────────────────┤  │
│  │ │ CONTRAST:   Use with white text (12.6:1 ratio)          │  │
│  │ └─────────────────────────────────────────────────────────┘  │
│  │                                                              │
│  │ Design Token Format:                                         │
│  │ {                                                            │
│  │   "color.brand.primary": {                                   │
│  │     "value": "#0032A0",                                      │
│  │     "pantone": "PMS 286 C",                                  │
│  │     "cmyk": [100, 75, 0, 0],                                 │
│  │     "description": "Primary brand blue"                      │
│  │   }                                                          │
│  │ }                                                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  BEST PRACTICES ───────────────────────────────────────────    │
│  │                                                              │
│  │ ✓ Always start with Pantone for brand colors                 │
│  │ ✓ Document conversions for all color spaces                  │
│  │ ✓ Specify coated AND uncoated Pantone references             │
│  │ ✓ Include accessibility contrast ratios                      │
│  │ ✓ Provide physical Pantone chips for critical approvals      │
│  │ ✓ Note which colors cannot be reproduced in CMYK             │
│  │ ✓ Update design tokens with Pantone references               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---
