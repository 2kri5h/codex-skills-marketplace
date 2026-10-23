---
name: final-frontend
description: Master all-in-one frontend UI engineering and architecture skill. Fuses impeccable, ponytail, frontend-ui-engineering, adapt (multi-screen responsive transformation), emil-design-eng, transitions.dev, and browser visual inspection. Takes a research doc, brief, or specification for a website and executes the complete lifecycle — from planning and full component architecture to production-grade engineering, fluid responsive adaptation, tactile spring motion, and anti-slop verification.
argument-hint: "<research-doc-or-brief> [--plan|--build|--adapt|--motion|--polish]"
metadata:
  version: "1.0.0"
  author: "Antigravity Engineering"
  tags: ["frontend", "ui-engineering", "architecture", "design-system", "responsive", "motion", "anti-slop"]
---

# Final Frontend (Master UI Engineering Pipeline)

`final-frontend` is the definitive frontend engineering workflow. It solves the core flaw of AI-generated websites: **the statistical median of internet boilerplate (AI Slop)**. By fusing strict design systems (`impeccable`), senior developer restraint (`ponytail`), production component architecture (`frontend-ui-engineering`), universal screen adaptation (`adapt`), and physics-based motion (`emil-design-eng`), it produces interfaces that rival Linear, Vercel, Apple, and Stripe.

Whenever the user provides a **research doc**, **website brief**, or asks to **build/architect a frontend**, execute this exact 6-stage lifecycle without skipping steps.

---

## The 6-Stage Master Lifecycle

```
┌──────────────────────────────────────────────────────────────────────────────┐
│ STAGE 1: INGESTION & TASTE BRIEFING                                          │
│ Deconstruct research doc, determine Surface Mode, enforce anti-slop bans      │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
┌──────────────────────────────────────▼───────────────────────────────────────┐
│ STAGE 2: ARCHITECTURE & COMPONENT PLANNING                                    │
│ IA, Route tree, Atomic component hierarchy, Data contracts, Ponytail Ladder   │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
┌──────────────────────────────────────▼───────────────────────────────────────┐
│ STAGE 3: PRODUCTION COMPONENT & PAGE ENGINEERING                             │
│ Composition-over-configuration, TypeScript contracts, Lucide icons, Semantics│
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
┌──────────────────────────────────────▼───────────────────────────────────────┐
│ STAGE 4: UNIVERSAL MULTI-SCREEN ADAPTATION (ADAPT)                           │
│ Mobile (320-767px) + Tablet (768-1023px) + Desktop/4K, Thumb-zones, dvh, env│
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
┌──────────────────────────────────────▼───────────────────────────────────────┐
│ STAGE 5: TACTILE MOTION & MICRO-INTERACTIONS                                 │
│ Emil Kowalski spring physics, transitions.dev, composite-only GPU properties  │
└──────────────────────────────────────┬───────────────────────────────────────┘
                                       │
┌──────────────────────────────────────▼───────────────────────────────────────┐
│ STAGE 6: VISUAL QA & CRAFT-FLOOR VERIFICATION                                │
│ Dual-viewport inspection (375px + 1440px), contrast ratios, zero-leak audit  │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Stage 1: Ingestion & Taste Briefing

Before writing a single line of code, parse the research document or brief through the **Taste Filter**:

### 1. Identify the Surface Mode
Select one of four primary modes (from `impeccable`):
- **Persuade:** Landing pages, marketing sites, product launches. Goal: Earn attention, communicate value, drive action. High visual punch, hero art direction.
- **Operate:** Web apps, dashboards, control panels, SaaS tools. Goal: Speed, clarity, high information density, scanability, reliable keyboard/mouse workflows.
- **Read:** Documentation, blogs, knowledge bases. Goal: Typographic comfort, measure (65–75ch), distraction-free reading, scannable hierarchies.
- **Experience:** Interactive portfolios, creative showcases, experimental labs. Goal: The medium is the message; immersive storytelling.

### 2. Establish the Design World (Zero-Slop Tokens)
- **Color Palette (OKLCH):** Never use raw hex generic grays or saturated RGB primitives. Define semantic tokens:
  - Background surface, Elevated surface, Overlay surface.
  - Foreground primary, secondary (tinted from hue, never plain gray), muted.
  - Accent / Brand tone with proper contrast ratios (≥4.5:1 for body text, ≥3:1 for large text).
- **Typography Pairings:** Never rely on default system sans. Pair a distinct display/headline font with a hyper-readable text face.
- **Spatial Rhythm:** Strict 4px/8px baseline grid (`4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px`).

### 3. Absolute Bans (Anti-Slop Craft Floor)
- ❌ **No cliché AI hero cards:** Do not wrap everything in identical 3-column bordered cards with an icon + title + short paragraph.
- ❌ **No gradient text everywhere:** Weight, scale, and typographic contrast drive emphasis; gradient text is amateurish decoration.
- ❌ **No hallucinated SVGs or emojis:** Use canonical icons (Lucide, Heroicons, Phosphor) in consistent stroke width (1.5px or 2px).
- ❌ **No fake kickers/eyebrows:** Eliminate meaningless pill badges above headings like `"AI-POWERED PLATFORM"`. Let the headline speak.
- ❌ **No zero-offset colored glow halos:** Shadows must have directional light offsets (`x`, `y`) and soft blurs.

---

## Stage 2: Architecture & Component Planning

Produce the **Architecture Blueprint** first. Share this planning breakdown with the user before flooding the codebase with files:

### 1. Information Architecture & Route Tree
- Complete URL routing structure (e.g. `/`, `/dashboard`, `/projects/[id]`, `/settings`).
- Modal, drawer, and overlay hierarchy.
- Layout shells (persistent TopNav, collapsible Sidebar, sticky command bar).

### 2. Component Decomposition Matrix
Deconstruct every screen into a strict modular hierarchy:
```
src/
├── components/
│   ├── ui/               # Atoms & Base primitives (Button, Input, Badge, Dialog)
│   ├── molecules/        # Composed widgets (FormField, SearchBar, UserMenu, StatCard)
│   ├── organisms/        # Major sections (AppHeader, Sidebar, HeroSection, DataTable)
│   └── layouts/          # Screen wrappers (DashboardLayout, MarketingLayout)
├── hooks/                # Custom hooks (useMediaQuery, useDisclosure, useDebounce)
├── lib/                  # Utilities, tokens, styling helpers (cn, formatters)
└── types/                # Strict TypeScript contracts & domain models
```

### 3. State & Data Flow Plan
- **Server State vs Client State:** Determine what is fetched/cached vs local UI state (open drawers, active filters, form inputs).
- **Data Contracts:** Explicit TypeScript interfaces for all mock data or API schemas.

### 4. The Ponytail Restraint Ladder (Anti-Bloat Gate)
Climb the senior developer ladder before approving any component or dependency:
1. *Does this feature need to exist at all?* (YAGNI).
2. *Can native browser features do it?* Use `<dialog>` over heavy modal libs, CSS Grid over complex column math, native `<input type="date">` where appropriate.
3. *Already in the codebase?* Reuse existing tokens and helpers; never duplicate utilities.
4. *Can it be one line?* Write the one line. Zero boilerplate factories for a single use-case.

---

## Stage 3: Production Component Engineering

When executing components and pages, adhere to the `frontend-ui-engineering` standard:

### 1. Composition Over Configuration
Build modular compound components rather than monolithic components burdened with 25 optional props:
```tsx
// ✅ Correct: Flexible, composable
<Card>
  <CardHeader>
    <CardTitle>Resource Allocation</CardTitle>
    <Badge variant="outline">Live</Badge>
  </CardHeader>
  <CardContent>
    <AllocationChart data={data} />
  </CardContent>
</Card>

// ❌ Incorrect: Inflexible prop-heavy monolith
<Card title="Resource Allocation" showBadge badgeText="Live" chartData={data} />
```

### 2. Complete State Coverage
Every interactive element must handle all 6 UI states:
1. **Default / Rest**
2. **Hover** (guarded with `@media (hover: hover)`)
3. **Active / Pressed**
4. **Focus-Visible** (accessible focus rings matching palette)
5. **Loading / Skeleton** (content-preserving layout)
6. **Disabled / Read-only** (proper aria-disabled, reduced opacity, cursor not-allowed)

### 3. Typography & CSS Craft
- Headings: Always apply `text-wrap: balance` to prevent orphan words.
- Body Copy: Constrain reading line lengths to `65–75ch`.
- Scrollbars: Set `scrollbar-gutter: stable` to avoid layout shifts when scrollbars appear.

---

## Stage 4: Universal Multi-Screen Adaptation (Adapt)

Transform the interface so it feels purposefully designed for **every** screen size, not just shrunk down:

### 1. Mobile (320px – 767px)
- **Vertical Reflow:** Multi-column grids reflow to single-column stacked hierarchy.
- **Thumb-Zone Navigation:** Top navigation collapses into a bottom navigation bar or bottom sheet drawer for one-handed operation.
- **Touch Target Floor:** All tap targets must be at least **44×44px** with generous touch padding.
- **Safe Area Insets:** Support notched phones and home indicator bars:
  ```css
  padding-bottom: max(1rem, env(safe-area-inset-bottom));
  padding-top: env(safe-area-inset-top);
  ```
- **Viewport Height Fix:** Use `100dvh` (dynamic viewport height) instead of `100vh` to prevent mobile address bar jumping.
- **Input Zoom Prevention:** Form inputs must be at least `16px` font-size on mobile so iOS Safari does not zoom the viewport on focus.

### 2. Tablet (768px – 1023px)
- Two-column adaptive layouts.
- Master-detail views (collapsible left list + right detail panel).
- Dual support for touch and pointer interactions.

### 3. Desktop & Ultrawide (1024px – 2560px+)
- Max-width content boundaries (`max-w-7xl` or fluid container) to prevent content stretching on 4K monitors.
- High information density, persistent sidebars, and keyboard shortcut triggers (`cmd+k`, `/`).

### 4. Pointer & Hover Detection
Never bind critical functionality to hover:
```css
/* Mouse / Trackpad */
@media (hover: hover) and (pointer: fine) {
  .interactive-card:hover { transform: translateY(-2px); }
}

/* Touch devices (phones / tablets) */
@media (hover: none) {
  .interactive-card:active { transform: scale(0.98); }
}
```

---

## Stage 5: Tactile Motion & Micro-Interactions

Incorporate Emil Kowalski's motion engineering principles (`emil-design-eng` + `transitions.dev`):

### 1. Spring Physics Over Linear Easing
Real physical objects don't move with linear or generic `ease-in-out` curves; they have mass, stiffness, and damping:
- **Snappy Popovers / Tooltips:** High stiffness, critical damping (no oscillations). `stiffness: 400, damping: 30`.
- **Sheet Drawers / Dialogs:** Balanced weight with smooth deceleration. `stiffness: 300, damping: 28`.
- **Micro-Toggles:** Instant tactile response. `stiffness: 500, damping: 35`.

### 2. Composite-Only GPU Properties
- **Animate ONLY `transform` and `opacity`.**
- **NEVER** animate `height`, `width`, `top`, `left`, `margin`, or `padding` directly (which trigger full layout recalculation and cause jank).
- For expanding cards, use `framer-motion` layout animations (`layoutId`) or the FLIP technique (First, Last, Invert, Play).

### 3. The One-Authored-Moment Rule
Avoid chaotic entrance animations where 15 cards slide in from different directions simultaneously. Pick **one** hero transition (e.g. a smooth staged cascade or a focal element expansion), and keep the rest instant or subtly faded.

### 4. Accessibility
Always respect user motion preferences:
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

## Stage 6: Visual QA & Craft-Floor Verification

Run the inspection round before handing off work:

1. **Dual-Viewport Check:** Inspect the layout at **375px** (mobile) and **1440px** (desktop).
2. **Horizontal Leak Test:** Run `document.documentElement.scrollWidth > window.innerWidth` to verify zero horizontal scrolling on mobile.
3. **Contrast Audit:** Verify body copy meets ≥4.5:1 contrast against its immediate background.
4. **Browser Surfaces Themed:** Custom selection highlight (`::selection`), caret color, and focus rings must use the design system palette rather than browser defaults.
5. **No AI Tells:** Verify absence of generic pill labels, ungrounded gradients, and template cards.

---

## Command Flags

When invoking `/final-frontend`, optional flags target specific phases:

| Command / Flag | Action |
| :--- | :--- |
| `/final-frontend <doc>` | Runs the complete 6-stage lifecycle from architecture to production code |
| `/final-frontend --plan <doc>` | Deconstructs the brief into information architecture, routes, component matrix & tokens |
| `/final-frontend --build <doc>` | Executes the full component and page implementation |
| `/final-frontend --adapt` | Audits and transforms existing UI across mobile, tablet, desktop, and notch safe-areas |
| `/final-frontend --motion` | Upgrades UI animations with Emil Kowalski spring physics and micro-interactions |
| `/final-frontend --polish` | Executes an anti-slop craft-floor audit and visual regression check |
