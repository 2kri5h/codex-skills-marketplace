---
name: final-frontend-plan
description: Action skill for final-frontend. Deconstructs website research docs, PRDs, and briefs into comprehensive architecture, route maps, atomic component matrices, and design tokens without writing code yet.
argument-hint: "<research-doc-or-brief>"
metadata:
  version: "1.0.0"
  part_of: "final-frontend"
---

# Final Frontend: Architecture & Planning (`final-frontend-plan`)

This is the planning phase action for `/final-frontend`. It takes any research document, PRD, or website specification and produces a complete, production-grade architectural blueprint **before any code is written**.

---

## The 5-Step Planning Workflow

### Step 1: Deconstruct the Brief & Surface Mode
1. **Extract Core Objectives:** Value proposition, user personas, primary conversion actions, and key user flows.
2. **Determine Surface Mode:**
   - **Persuade:** Landing pages, product launches, marketing. High visual authority, editorial typography, brand punch.
   - **Operate:** Dashboards, SaaS portals, tools. High data density, scanability, clear keyboard navigation, low cognitive friction.
   - **Read:** Documentation, blogs, knowledge bases. 65–75ch line measure, distraction-free reading, scannable anchors.
   - **Experience:** Creative showcases, interactive portfolios. Immersive spatial storytelling.

### Step 2: Formulate the Design System Tokens
Define the concrete token architecture:
- **OKLCH Color World:**
  - `surface-base`, `surface-raised`, `surface-overlay`
  - `foreground-primary`, `foreground-secondary` (tinted from ambient hue, never dead gray), `foreground-muted`
  - `accent` / `brand` with certified WCAG AA contrast (≥4.5:1 body, ≥3:1 large headers)
  - `border-subtle`, `border-strong`
- **Typographic Scale:** Font pairings (Display font + Sans text font), modular scale (`xs`, `sm`, `base`, `lg`, `xl`, `2xl`, `3xl`, `4xl`), line-heights, letter-spacing.
- **Spatial Rhythm:** Strict 4px/8px baseline grid (`4, 8, 12, 16, 24, 32, 48, 64px`).

### Step 3: Information Architecture & Route Hierarchy
Map every route and layout container:
- Route tree (e.g. `/`, `/dashboard`, `/projects/[id]`, `/settings`).
- App Shells: Header, TopNav, Collapsible Sidebar, Mobile Bottom Bar.
- Overlay Hierarchy: Modals, Drawers, Floating Command Palettes (`cmd+k`), Tooltips.

### Step 4: Atomic Component Decomposition Matrix
Break down every screen into a rigorous component matrix:
- **Atoms:** Buttons, Inputs, Checkboxes, Switches, Badges, Tooltips, Lucide/Heroicons icons.
- **Molecules:** SearchBar, FilterBar, StatCard, NavItem, FormField with validation message.
- **Organisms:** HeroSection, DataTable, FeatureGrid, NavigationBar, UserProfileMenu.
- **Templates:** DashboardLayout, MarketingLayout, DocumentLayout.

### Step 5: The Ponytail Anti-Bloat Reality Check
Run every planned element through the senior developer ladder:
1. *Does this component/feature need to exist at all?* (YAGNI).
2. *Can native browser features handle it?* (`<dialog>`, `<details>`, `text-wrap: balance`, `scrollbar-gutter: stable`, native CSS grid).
3. *Does it add unnecessary external dependencies?* Reject premature npm packages.

---

## Deliverable Format

Output the complete architecture plan as a structured document or artifact (`architecture_spec.md`) including:
1. **Product & Surface Mode Summary**
2. **Design Tokens & Theme Contract** (OKLCH values, typography pairings)
3. **Route & Layout Blueprint**
4. **Component Hierarchy Matrix** (Atoms, Molecules, Organisms)
5. **Data & State Contracts** (TypeScript types for props and mock data)
6. **Ponytail Pruning Summary** (what was excluded and why)
