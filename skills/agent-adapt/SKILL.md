---
name: adapt
description: Dedicated multi-screen transformation action skill for final-frontend. Transforms any website or app to EVERY screen size and device context (Mobile 320-767px, Tablet 768-1023px, Desktop 1024-1440px, Ultrawide/4K), with notch safe-areas, thumb-zone ergonomics, 100dvh, and touch hardening.
argument-hint: "[target-file-or-page]"
metadata:
  version: "1.0.0"
  part_of: "final-frontend"
  alias: "final-frontend-adapt"
---

# Adapt: Universal Multi-Screen Transformation

`adapt` transforms websites and web applications across every viewport and device category. **Adaptation is rethinking the experience for the new context, not scaling pixels.**

---

## Breakpoint Matrix

| Viewport | Range | Ergonomic Priority | Navigation Pattern | Layout Reflow |
| :--- | :--- | :--- | :--- | :--- |
| **Mobile** | `320px – 767px` | 44px tap targets, thumb-zone | Bottom nav / drawer sheet | 1-column stack, cards full-width |
| **Tablet** | `768px – 1023px` | Touch + pointer hybrid | Collapsible drawer / top bar | 2-column adaptive, master-detail |
| **Desktop** | `1024px – 1439px`| Mouse & keyboard density | Persistent sidebar / top bar | Multi-panel, max-w-7xl bounded |
| **Ultrawide** | `1440px – 4K` | Reading line length limits | Centered container, split-screen | Fluid container, max-w-prose |

---

## The 6 Adaptation Passes

### 1. Layout Reflow & Stacking
- Convert horizontal multi-column grids to single-column reflow (`grid-template-columns: 1fr`).
- Data tables reflow into stacked cards using `data-label` pseudo-elements.
- Margins and paddings shift from desktop scale (`p-8`, `p-12`) to mobile scale (`p-4`, `p-5`).

### 2. Thumb-Zone Ergonomics
- Top-heavy navigation transforms into a bottom navigation bar or bottom sheet drawer for easy one-handed operation.
- Primary CTA buttons anchored within comfortable thumb reach (bottom third of screen).
- Bottom sheets replace dropdown menus with smooth swipe-to-dismiss gestures.

### 3. Touch Target Hardening
- **Strict 44×44px Touch Floor:** Every button, tab, link, and interactive icon must have at least 44×44px hit-box area (`min-h-[44px] min-w-[44px]`).
- Generous touch spacing: Minimum 8px gap between adjacent interactive targets to prevent mis-clicks.

### 4. Mobile Browser Quirks & Viewport Fixes
- **Dynamic Viewport Height (`100dvh`):** Always replace `100vh` with `100dvh` on full-screen containers to prevent jumpy layout shifts when the mobile browser URL bar expands/collapses.
- **Notch & Safe Areas:**
  Ensure the viewport meta tag is present:
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  ```
  Apply safe area padding in CSS:
  ```css
  padding-bottom: max(1rem, env(safe-area-inset-bottom));
  padding-top: env(safe-area-inset-top);
  ```
- **iOS Font-Zoom Prevention:** Form inputs must have `font-size: 16px` (or `1rem`) minimum to stop Safari from forcefully zooming in on focus.

### 5. Hover Trap Elimination
Never hide critical actions behind hover on touch devices:
```css
/* Fine pointer (Mouse / Trackpad) */
@media (hover: hover) and (pointer: fine) {
  .card:hover { transform: translateY(-2px); }
  .card .hidden-action { opacity: 0; }
  .card:hover .hidden-action { opacity: 1; }
}

/* Touch devices (Phones / Tablets) */
@media (hover: none) {
  .card:active { transform: scale(0.98); }
  .card .hidden-action { opacity: 1; display: block; }
}
```

### 6. Fluid Spacing & Typography via `clamp()`
Replace discrete media-query font jumps with smooth fluid interpolation:
```css
/* Fluid headline from 2rem (mobile) to 3.5rem (desktop) */
font-size: clamp(2rem, 1.45rem + 2.35vw, 3.5rem);

/* Fluid section padding */
padding-block: clamp(2rem, 1.2rem + 3.4vw, 6rem);
```
