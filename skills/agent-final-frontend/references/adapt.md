# Adapt: Multi-Screen Responsive Transformation

> **Core Philosophy**: Adaptation is rethinking the experience for the target screen and device, not scaling pixels.

---

## 1. Context Assessment Matrix

| Device Class | Breakpoint Range | Primary Input | Ergonomic Priority | Navigation Pattern |
| :--- | :--- | :--- | :--- | :--- |
| **Mobile** | `320px – 767px` | Coarse touch, thumb-reach | 44px tap targets, single column | Bottom nav, bottom drawer sheet |
| **Tablet** | `768px – 1023px` | Touch + pointer | 2-column split, master-detail | Collapsible side-drawer |
| **Desktop** | `1024px – 1439px`| Fine mouse, keyboard | High data density, shortcuts | Persistent sidebar / top bar |
| **Ultrawide/4K** | `1440px – 3840px`| Fine pointer | Max-width content reading limits | Centered container, multi-panel |

---

## 2. Mobile Adaptation Strategy (Desktop → Mobile)

### Layout Reflow
- Convert all multi-column CSS grids to `grid-template-columns: 1fr` or flex-col.
- Cards take full width with consistent horizontal padding (`px-4` or `16px`).
- Complex data tables transform into vertical card stacks:
  ```css
  @media (max-width: 767px) {
    table, thead, tbody, th, td, tr { display: block; }
    thead tr { position: absolute; top: -9999px; left: -9999px; }
    td { position: relative; padding-left: 50%; }
    td:before {
      content: attr(data-label);
      position: absolute;
      left: 1rem;
      font-weight: 600;
    }
  }
  ```

### Thumb-Zone Ergonomics
- Position primary actions and navigation in the bottom third of the viewport.
- Modals become bottom sheets (`drawer`) with drag handles and velocity-aware dismiss gestures.
- Sticky headers stay compact (`h-14` / `56px`), leaving screen real estate for content.

### Touch & Safe Area Hardening
- **Minimum Tap Size:** `min-h-[44px] min-w-[44px]` on all buttons, links, and form controls.
- **Viewport Height:** Always use `100dvh` instead of `100vh` to avoid the browser address bar jump.
- **Notch & Safe Areas:**
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
  ```
  ```css
  body {
    padding-top: env(safe-area-inset-top);
    padding-bottom: env(safe-area-inset-bottom);
    padding-left: env(safe-area-inset-left);
    padding-right: env(safe-area-inset-right);
  }
  ```
- **Input Zoom Prevention:** `font-size: 16px` (or `1rem`) minimum on `<input>` and `<select>` to stop iOS Safari auto-zooming.

---

## 3. Desktop & Large Screen Adaptation (Mobile → Desktop)

- **Max-Width Anchors:** Wrap main containers in `max-w-7xl mx-auto` or `max-w-6xl` to prevent unreadable horizontal spans.
- **Data Density:** Show secondary metadata inline; introduce multi-pane inspection and split views.
- **Keyboard Accelerators:** Expose shortcuts (`cmd+k` search, `j/k` list traversal, `esc` dismiss).
- **Hover Micro-Interactions:** Guard all hover styles with `@media (hover: hover)` so touch screens don't get stuck in active states.

---

## 4. Fluid Sizing Formula

Use CSS `clamp()` for fluid typography and spacing that scales smoothly without jagged breakpoint jumps:
```css
/* Fluid headline: 2rem (32px) at 375px viewport up to 3.5rem (56px) at 1280px */
font-size: clamp(2rem, 1.45rem + 2.35vw, 3.5rem);

/* Fluid section padding: 2rem up to 6rem */
padding-block: clamp(2rem, 1.2rem + 3.4vw, 6rem);
```
