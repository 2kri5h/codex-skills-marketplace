---
name: lenis-smooth-scroll
description: Integrate, configure, tune, and debug Lenis smooth scrolling (darkroomengineering/lenis) for high-end web applications and websites. Covers ReactLenis (lenis/react), Next.js App Router, Vue (lenis/vue), GSAP ScrollTrigger sync, WebGL/Three.js scroll syncing, parallax, anchor navigation, nested scroll prevention (data-lenis-prevent), modal lockouts, and accessibility (prefers-reduced-motion). Use when asked for smooth scrolling, inertial scrolling, Lenis setup, scroll animation performance, or resolving scroll conflicts.
---

# Lenis Smooth Scroll

Lenis is the lightweight, robust, and performant smooth scrolling library designed by [darkroom.engineering](https://github.com/darkroomengineering/lenis). It runs on native browser scroll, preserving native semantics, accessibility, anchor links, and `position: sticky`.

Use Lenis as the scroll transport layer, not as the animation system itself. Pair it with GSAP ScrollTrigger, Motion, or WebGL/Three.js render loops.

## Primary References
- **Repository:** https://github.com/darkroomengineering/lenis
- **Documentation & Showcase:** https://www.lenis.dev
- **NPM Package:** `npm i lenis`

---

## 1. Quick Installation & CSS

```bash
npm install lenis
# or
pnpm add lenis
# or
yarn add lenis
```

### Essential CSS
Always import or include the official Lenis CSS to avoid layout shifting or incorrect height calculations:

```js
import 'lenis/dist/lenis.css'
```

Or vanilla CSS equivalent:
```css
html.lenis, html.lenis body {
  height: auto;
}

.lenis.lenis-smooth {
  scroll-behavior: auto !important;
}

.lenis.lenis-smooth [data-lenis-prevent] {
  overscroll-behavior: contain;
}

.lenis.lenis-stopped {
  overflow: hidden;
}

.lenis.lenis-smooth iframe {
  pointer-events: none;
}
```

---

## 2. Core Integration Patterns

### A. Next.js (App Router) & React

Using `lenis/react`:

```tsx
// components/providers/smooth-scroll.tsx
'use client'

import { ReactLenis } from 'lenis/react'
import 'lenis/dist/lenis.css'

export function SmoothScrollProvider({ children }: { children: React.ReactNode }) {
  return (
    <ReactLenis
      root
      options={{
        lerp: 0.1,
        duration: 1.2,
        smoothWheel: true,
        respectReducedMotion: true,
      }}
    >
      {children}
    </ReactLenis>
  )
}
```

Wrap in `app/layout.tsx`:
```tsx
import { SmoothScrollProvider } from '@/components/providers/smooth-scroll'

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <SmoothScrollProvider>
          {children}
        </SmoothScrollProvider>
      </body>
    </html>
  )
}
```

#### Accessing Lenis in Child Components
```tsx
'use client'

import { useLenis } from 'lenis/react'

export function ScrollProgress() {
  const lenis = useLenis((lenis) => {
    // Scroll callback
    console.log('Scroll progress:', lenis.progress, 'Scroll Y:', lenis.scroll)
  })

  return (
    <button onClick={() => lenis?.scrollTo('#target-section', { offset: -80, duration: 1.5 })}>
      Scroll to section
    </button>
  )
}
```

---

### B. Vanilla JS / Standalone

```js
import Lenis from 'lenis'
import 'lenis/dist/lenis.css'

const lenis = new Lenis({
  autoRaf: true,
  anchors: true,
  duration: 1.2,
  easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
  respectReducedMotion: true,
})

// Listen to scroll events
lenis.on('scroll', (e) => {
  // e.scroll, e.velocity, e.progress, e.direction
})
```

---

### C. GSAP ScrollTrigger Integration

When pairing with GSAP, disable `autoRaf` in Lenis and allow GSAP's ticker to drive Lenis updates. This ensures frame synchronization with zero visual jitter or lag.

```js
import Lenis from 'lenis'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import 'lenis/dist/lenis.css'

gsap.registerPlugin(ScrollTrigger)

// Initialize Lenis with manual RAF
const lenis = new Lenis({
  autoRaf: false,
  anchors: true,
  respectReducedMotion: true,
})

// Synchronize ScrollTrigger on Lenis scroll
lenis.on('scroll', ScrollTrigger.update)

// Add Lenis to GSAP ticker
gsap.ticker.add((time) => {
  lenis.raf(time * 1000)
})

// Turn off lag smoothing to prevent visual jumps on frame drops
gsap.ticker.lagSmoothing(0)
```

---

### D. WebGL / Three.js / Canvas Synchronization

When rendering 3D WebGL scenes that track DOM elements (e.g., Three.js planes matching image positions):

```js
import Lenis from 'lenis'

const lenis = new Lenis({ autoRaf: false })

function renderLoop(time) {
  lenis.raf(time)
  
  // Update 3D scene camera or object positions directly from lenis.scroll
  camera.position.y = -lenis.scroll * scaleFactor
  renderer.render(scene, camera)

  requestAnimationFrame(renderLoop)
}
requestAnimationFrame(renderLoop)
```

---

## 3. Configuration & Options Reference

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `duration` | `number` | `1.2` | Duration in seconds (ignored if `lerp` is set). |
| `lerp` | `number` | `0.1` | Linear interpolation intensity (0.0 to 1.0). Smaller = smoother/slower. |
| `easing` | `function` | `custom` | Easing equation `(t) => Math.min(1, 1.001 - Math.pow(2, -10 * t))`. |
| `smoothWheel` | `boolean` | `true` | Enable smooth scrolling for mouse wheel input. |
| `syncTouch` | `boolean` | `false` | Enable smooth scrolling on touch devices (often best left `false` for native mobile feel). |
| `touchMultiplier` | `number` | `1` | Touch movement multiplier. |
| `wheelMultiplier` | `number` | `1` | Mouse wheel scroll speed multiplier. |
| `anchors` | `boolean` | `false` | Enable smooth scrolling to internal anchor links (`#section`). |
| `respectReducedMotion`| `boolean` | `true` | Disable smoothing when `prefers-reduced-motion: reduce` is active. |
| `prevent` | `function` | `undefined` | Custom filter predicate `(node) => boolean` to bypass smoothing. |

---

## 4. API Methods

### `lenis.scrollTo(target, options)`
Scroll smoothly or immediately to an element, coordinate, or keyword:
```js
// Scroll to top
lenis.scrollTo(0)

// Scroll to CSS selector with offset & callback
lenis.scrollTo('#contact', {
  offset: -60,
  duration: 1.5,
  immediate: false,
  lock: true, // prevent user scrolling while in transit
  onComplete: () => console.log('Arrived at contact'),
})
```

### `lenis.stop()` and `lenis.start()`
Crucial for interactive overlays, dialogs, drawers, and mobile hamburger menus:
```js
// Modal opens: lock smooth scroll
function openModal() {
  lenis.stop()
  document.body.classList.add('modal-open')
}

// Modal closes: restore scroll
function closeModal() {
  lenis.start()
  document.body.classList.remove('modal-open')
}
```

### `lenis.destroy()`
Cleanup instance on component unmount or route transition.

---

## 5. Nested & Preventable Scrolling

When an element inside the page needs its own native scroll bar (e.g., code snippets, side navigation, nested cards):

### HTML Attributes
```html
<!-- Prevent smooth scroll entirely for this container -->
<div data-lenis-prevent style="overflow-y: auto; max-height: 300px;">
  ...
</div>

<!-- Selective prevention -->
<div data-lenis-prevent-wheel>...</div>
<div data-lenis-prevent-touch>...</div>
```

---

## 6. Implementation & Debug Checklist

1. **Native scroll check:** Does the page scroll properly natively without Lenis enabled?
2. **Single RAF driver:** Ensure only one ticker/RAF loop updates Lenis. Never call `requestAnimationFrame` and `autoRaf: true` simultaneously.
3. **CSS included:** Is `lenis/dist/lenis.css` imported?
4. **ScrollTrigger Refresh:** Run `ScrollTrigger.refresh()` after dynamic content, font loads, or window resizes.
5. **Fixed Elements:** Never put fixed-position navbars inside elements with `transform`, `filter`, or `perspective` (which resets the containing block).
6. **Mobile ergonomics:** On touch devices, native momentum scrolling is often preferred over synthetic touch inertia unless explicit WebGL synchronization is needed.
7. **Accessibility:** Confirm `respectReducedMotion: true` is enabled.
