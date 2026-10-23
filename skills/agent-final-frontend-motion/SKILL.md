---
name: final-frontend-motion
description: Action skill for final-frontend. Upgrades UI transitions, gestures, and animations with Emil Kowalski spring physics, transitions.dev interaction patterns, and 60/120fps GPU performance budgets.
argument-hint: "[target-component-or-page]"
metadata:
  version: "1.0.0"
  part_of: "final-frontend"
---

# Final Frontend: Motion Engineering (`final-frontend-motion`)

`final-frontend-motion` injects tactile spring physics, seamless layout morphing, and micro-interactions into UI components. Good motion provides spatial continuity and physical feedback, not visual noise.

---

## The 4 Motion Principles (Emil Kowalski Standard)

1. **Animate With Purpose:** Every animation must answer: *Where did this element come from, and where does it return?* If a transition causes cognitive friction or slows down task completion, eliminate it.
2. **Spring Physics Over Linear Easing:** Real physical elements have mass, tension, and damping. Never use linear `ease` or sluggish 300ms transitions.
3. **Interruptibility:** Every animation must be interruptible mid-flight without snapping, jerking, or state desynchronization.
4. **Hardware Acceleration:** Animate **strictly** `transform` and `opacity`. Never animate `height`, `width`, `top`, `left`, `margin`, or `padding` directly.

---

## Spring Physics Presets

Use these calibrated spring configurations (Framer Motion / CSS spring approximations):

```typescript
// 1. Snappy Micro-Interactions (Buttons, Badges, Switch Toggles, Icon pops)
export const snappySpring = {
  type: "spring",
  stiffness: 500,
  damping: 35,
  mass: 0.8
};

// 2. Natural Surface Transitions (Drawers, Bottom Sheets, Modals, Popovers)
export const surfaceSpring = {
  type: "spring",
  stiffness: 320,
  damping: 30,
  mass: 1.0
};

// 3. Playful Fluid Expansions (Card morphing, Layout shifts, Toast notifications)
export const fluidSpring = {
  type: "spring",
  stiffness: 260,
  damping: 22,
  mass: 1.0
};
```

---

## High-Craft Interaction Patterns

### 1. Card Layout Morphing (`layoutId`)
When expanding a preview card into a full modal or detailed view, use Framer Motion's `layoutId` so the container, image, and text morph smoothly in continuous space:
```tsx
<motion.div layoutId={`card-${id}`} className="rounded-2xl bg-surface p-6 shadow-sm">
  <motion.h3 layout="position">{title}</motion.h3>
  <motion.p layout="position">{description}</motion.p>
</motion.div>
```

### 2. Tab Indicator Slide (Shared Layout)
Instead of individual active states on each tab, animate a single shared background pill:
```tsx
{tabs.map((tab) => (
  <button key={tab.id} onClick={() => setActive(tab.id)} className="relative px-4 py-2">
    {active === tab.id && (
      <motion.div
        layoutId="active-indicator"
        className="absolute inset-0 rounded-lg bg-accent/15"
        transition={snappySpring}
      />
    )}
    <span className="relative z-10">{tab.label}</span>
  </button>
))}
```

### 3. Staggered Content Sweeps
Stagger list or grid items by 20–30ms so content lands in a fluid, unified wave rather than slow cascading dominos:
```typescript
export const listContainer = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: { staggerChildren: 0.025, delayChildren: 0.05 }
  }
};
export const listItem = {
  hidden: { opacity: 0, y: 10 },
  visible: { opacity: 1, y: 0, transition: surfaceSpring }
};
```

---

## DialKit Workflow (Live Visual Tuning)

When adjusting motion curves, integrate `dialkit` (`npm install dialkit motion`):
1. Mount the DialKit floating tweak panel in your dev preview.
2. Wire spring sliders (`stiffness`, `damping`, `mass`) directly to your animation config.
3. Dial in the physical feel live in the browser, export JSON, and lock the parameters into code.

---

## Reduced Motion Floor
Always guarantee instant states when reduced motion is preferred:
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
