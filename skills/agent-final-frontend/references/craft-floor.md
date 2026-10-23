# The Anti-Slop Craft Floor

The craft floor establishes non-negotiable design thresholds and categorical bans. If an interface violates any item here, it fails the engineering review.

---

## 1. Absolute Bans (The Anti-Slop Directive)

- ❌ **No Cliché 3-Card Grids:** Do not use identical square cards with icon-top + title + 2-line description as the primary layout for features. Vary hierarchy: feature spotlights, interactive demos, list-detail layouts, bento grids with asymmetric visual weight.
- ❌ **No Gradient Headings as Crutch:** Never use `bg-gradient-to-r from-purple-500 to-pink-500 bg-clip-text text-transparent` on every heading. Emphasis comes from typographic weight, deliberate scale, or distinct editorial lettering.
- ❌ **No Pill Badges as Eyebrows:** Ban phrases like `"✨ AI-POWERED PLATFORM"` or `"THE FUTURE OF SOFTWARE"` enclosed in rounded-full pill tags above every heading. Let the headline stand on its own.
- ❌ **No Hallucinated Vector Shapes:** Never let an AI write random SVG paths for icons or logos. Use verified icon libraries: Lucide, Heroicons, or Phosphor.
- ❌ **No Monospace as Costume:** Do not apply `font-mono` to random headings or labels just to look "technical" or "developer-focused". Monospace is strictly reserved for code blocks, terminal outputs, hashes, and tabular numerals (`font-variant-numeric: tabular-nums`).
- ❌ **No Zero-Offset Glow Rings:** `box-shadow: 0 0 25px rgba(120, 0, 255, 0.5)` is amateurish slop. Real depth uses directional offset (`box-shadow: 0 4px 12px -2px rgba(0,0,0,0.08), 0 2px 6px -1px rgba(0,0,0,0.04)`).

---

## 2. Mandatory Craft Standards

- **Contrast Ratios:** Body text must meet ≥4.5:1 contrast against its background. Secondary and muted text must be tinted from the ambient surface hue, never flat dead gray.
- **Headings Balance:** Always include `text-wrap: balance` on headlines to eliminate dangling words.
- **Line Length:** Body paragraphs must have a max-width of `65ch` to `75ch` (`max-w-prose`) for optimal reading rhythm.
- **Elevation System:** Declare elevation once per component: either a subtle border (`border border-neutral-200/80 dark:border-neutral-800`) OR a soft shadow, never a thick border combined with heavy glow.
- **State Completeness:** Every interactive control must have distinct, designed states for:
  - Default
  - Hover (`@media (hover: hover)`)
  - Active / Pressed
  - Focus-visible (explicit focus ring with offset, visible in high contrast)
  - Loading / Disabled
- **Custom Browser Surfaces:** Text selection (`::selection`), scrollbars (`scrollbar-color`), and input carets must be explicitly themed from the project palette.
