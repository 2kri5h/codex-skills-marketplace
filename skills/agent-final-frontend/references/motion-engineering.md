# Motion Engineering & Spring Physics

> *"Good motion is not decorative; it provides spatial awareness, continuity, and tactile confidence."* — Emil Kowalski

---

## 1. The Core Motion Hierarchy

Before adding any transition, ask in this order:
1. **Should it animate at all?** (If it distracts or slows down task completion, keep it instantaneous).
2. **What is the spatial relationship?** (Where does the element come from? Does the user know where it lives?).
3. **Is it interruptible?** (Can the user reverse the action mid-flight without glitching?).
4. **Is it composite-only?** (Does it strictly animate `transform` and `opacity`?).

---

## 2. Spring Physics Presets (Framer Motion / CSS Springs)

Avoid linear or generic cubic-bezier curves for interactive UI. Use spring physics defined by **stiffness**, **damping**, and **mass**:

### Snappy Micro-Interactions (Buttons, Badges, Icons)
- Instant response, zero bounce:
```typescript
export const snappySpring = {
  type: "spring",
  stiffness: 500,
  damping: 35,
  mass: 0.8
};
```

### Natural Content Transitions (Drawers, Sheets, Modals)
- Tactile weight with smooth deceleration:
```typescript
export const contentSpring = {
  type: "spring",
  stiffness: 300,
  damping: 30,
  mass: 1.0
};
```

### Playful Expansions (Card expansions, Toast notifications)
- Subtle, controlled overshoot (linear/vercel style):
```typescript
export const organicSpring = {
  type: "spring",
  stiffness: 260,
  damping: 22,
  mass: 1.0
};
```

---

## 3. High-Craft Micro-Interactions (transitions.dev Patterns)

### 1. Card Morph / Expansion (Shared Layout)
Use `layoutId` so the card morphs seamlessly from its small preview into the full detail view without unmounting/remounting jarringly:
```tsx
<motion.div layoutId={`card-${id}`} className="rounded-2xl bg-surface p-6 shadow-sm">
  <motion.h3 layout="position">{title}</motion.h3>
  <motion.p layout="position">{description}</motion.p>
</motion.div>
```

### 2. Number Pop-in / Animated Counter
Animate tabular digits vertically rather than jumping whole widths:
```css
.tabular-counter {
  font-variant-numeric: tabular-nums;
}
```

### 3. Staggered List Entrance
Stagger children by a tiny delta (15–30ms max) so the cascade is felt as a single fluid sweep rather than a laggy domino:
```typescript
export const containerVariants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: {
      staggerChildren: 0.025,
      delayChildren: 0.05
    }
  }
};

export const itemVariants = {
  hidden: { opacity: 0, y: 8 },
  visible: {
    opacity: 1,
    y: 0,
    transition: { type: "spring", stiffness: 400, damping: 28 }
  }
};
```

---

## 4. Performance Budget (60fps / 120fps Floor)

- **Strictly animate `transform` and `opacity`.**
- **Never animate `height: auto` directly.** Use `framer-motion`'s `layout` prop or CSS Grid interpolation (`grid-template-rows: 0fr` to `1fr`):
```css
.collapsible-drawer {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 250ms cubic-bezier(0.16, 1, 0.3, 1);
}
.collapsible-drawer.open {
  grid-template-rows: 1fr;
}
.collapsible-content {
  overflow: hidden;
}
```
- Wrap interactive elements in `will-change: transform` only during active interaction, not permanently across hundreds of DOM nodes.
