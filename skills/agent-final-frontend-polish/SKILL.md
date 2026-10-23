---
name: final-frontend-polish
description: Action skill for final-frontend. Runs an anti-slop craft-floor audit, WCAG contrast verification, horizontal overflow check, and dual-viewport visual inspection.
argument-hint: "[target-page-or-url]"
metadata:
  version: "1.0.0"
  part_of: "final-frontend"
---

# Final Frontend: Craft-Floor Polish & Verification (`final-frontend-polish`)

`final-frontend-polish` is the final verification gate before code is merged or shipped. It audits interfaces against the **Anti-Slop Craft Floor**, checks WCAG contrast, verifies mobile overflow, and ensures every detail feels human-crafted.

---

## The 6-Point Audit Checklist

### 1. The Anti-Slop Directive Audit
- [ ] **No Cliché 3-Card Feature Rows:** Verify feature presentations have varied hierarchy and deliberate visual weight (hero spotlights, bento arrangements, interactive previews).
- [ ] **No Gradient Heading Crutch:** Verify headings use typographic weight and editorial scale for punch, not generic purple-pink gradient text.
- [ ] **No Pill Eyebrow Badges:** Strip any unnecessary kicker tags like `"AI-POWERED"` above headings.
- [ ] **No Hallucinated SVGs:** Verify all icons are canonical Lucide, Heroicons, or Phosphor symbols with consistent stroke weights.
- [ ] **No Directionless Glow Halos:** Verify all shadows have directional offsets (`y-offset`, `x-offset`) and soft natural diffusion.

### 2. Dual-Viewport Layout Inspection
Inspect the interface across two anchor viewports:
- **Mobile Viewport (375px width):**
  - Verify zero horizontal scrolling (`scrollWidth <= innerWidth`).
  - Verify all touch targets meet the **44×44px** minimum.
  - Verify no clipped modals or overflowing text.
- **Desktop Viewport (1440px width):**
  - Verify layout content is anchored inside reasonable max-width constraints (e.g., `max-w-7xl` or `max-w-6xl`).
  - Verify typography measure remains within `65–75ch`.

### 3. WCAG Contrast Compliance
Measure computed contrast against immediate surface colors:
- **Body & Paragraph Text:** Must be ≥ **4.5:1** (WCAG AA).
- **Large Headlines (≥18pt or bold ≥14pt):** Must be ≥ **3:1**.
- **Secondary / Muted Text:** Must be tinted from the ambient surface hue; never use flat low-contrast gray that washes out.

### 4. Browser Surfaces Customization
Ensure the elements not drawn by standard components still reflect the brand:
- **Text Selection:** Custom `::selection` background and foreground colors matching palette.
- **Scrollbars:** Subtle themed scrollbars or `scrollbar-gutter: stable` to eliminate page jank.
- **Focus Rings:** Distinct, accessible focus-visible outlines on all interactive elements.

### 5. Typography Craft Verification
- Headings must have `text-wrap: balance` to prevent orphan words.
- Letter spacing (tracking) on display headlines must not exceed `-0.04em` (optimal is `-0.02em` to `-0.03em`).
- Numeric tables, timers, and metrics must use `font-variant-numeric: tabular-nums` to prevent column shifting.

### 6. State Completeness Audit
Verify every interactive element has visible, polished states for:
- Rest, Hover, Active, Focus, Loading Skeleton, Disabled, and Empty/Error recovery.

---

## Output Report

Generate a concise **Audit Scoreboard**:
```markdown
### Final-Frontend Polish Scoreboard
- [x] Anti-Slop Directive: PASS (Zero cliché grids, no fake pill eyebrows)
- [x] Mobile Viewport (375px): PASS (Zero horizontal overflow, 44px touch targets)
- [x] Desktop Viewport (1440px): PASS (65ch line measure, max-w bounded)
- [x] Contrast Floor: PASS (Body: 7.2:1, Headings: 11.4:1)
- [x] Themed Browser Surfaces: PASS (Selection, scrollbars, focus-visible)
- [x] Motion Physics: PASS (Composite-only GPU properties, spring physics)
```
