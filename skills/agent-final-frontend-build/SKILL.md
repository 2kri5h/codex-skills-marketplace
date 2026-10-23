---
name: final-frontend-build
description: Action skill for final-frontend. Executes full production-grade components, layouts, and pages based on an architectural spec, design tokens, and frontend-ui-engineering standards.
argument-hint: "<architecture-spec-or-feature>"
metadata:
  version: "1.0.0"
  part_of: "final-frontend"
---

# Final Frontend: Production Engineering (`final-frontend-build`)

This is the implementation action for `/final-frontend`. It takes the architectural blueprint and turns it into clean, production-grade, accessible code.

---

## The 5-Step Build Protocol

### Step 1: Design System & Token Foundation
1. Establish design tokens in `index.css` or Tailwind config:
   - Root OKLCH custom properties (`--bg-surface`, `--fg-primary`, `--accent`, etc.).
   - Dark mode tokens and automatic theme variables.
   - Font family definitions and base typography resets.

### Step 2: Atoms & Base Primitives (Composition-First)
Build primitives using composition over configuration:
- Compound component structure (`<Card><CardHeader><CardTitle>...`).
- Canonical icon integration (Lucide, Heroicons, Phosphor) with consistent 1.5px/2px stroke width. **Strictly zero hallucinated SVG bezier paths.**
- Full keyboard focus-visible rings using the project accent color.

### Step 3: Complete State Coverage
Every interactive component must implement all essential UI states:
1. **Default / Rest State**
2. **Hover State** (guarded with `@media (hover: hover)`)
3. **Active / Pressed State**
4. **Focus-Visible State**
5. **Loading / Skeleton State** (matching layout geometry)
6. **Disabled / Read-only State** (`aria-disabled`, reduced opacity, `cursor-not-allowed`)
7. **Empty & Error States** (helpful recovery actions, never blank screens)

### Step 4: Organisms, Layouts & Pages
- Assemble molecules and organisms into page templates.
- Strict semantic HTML5 (`<main>`, `<header>`, `<nav>`, `<aside>`, `<section>`, `<article>`).
- Heading hierarchy (exactly one `<h1>` per page, sequential `<h2>` and `<h3>`).
- Apply `text-wrap: balance` to headlines and `scrollbar-gutter: stable` to scrollable containers.

### Step 5: Type Contracts & Component Colocation
Colocate component assets cleanly:
```
src/components/
  FeatureSection/
    FeatureSection.tsx     # Implementation
    FeatureSection.types.ts# Strict TypeScript interface
    useFeatureSection.ts   # State hook (if needed)
```
Verify zero TypeScript compilation errors and zero console warnings.
