# tw:mf — Music Festival Website

A responsive, single-page marketing site for a fictional music festival, built as a Tailwind CSS 4 portfolio project. Demonstrates modern CSS techniques, semantic HTML, accessibility practices, and vanilla JavaScript interactivity — no frameworks, no build complexity beyond the Tailwind CLI.

Built following the [Tailwind CSS From Scratch | Learn Tailwind CSS Masterclass](https://www.udemy.com/share/107rCO3@VZszsso_9Mxgv6L13ZUaGfG9JX2lFJxZKQA5FrKlUDfz_XYoeH02cFBm0hW8TWKV7g==/) course on Udemy, with additional improvements applied independently (semantic HTML restructuring, ARIA accessibility, custom scrollbar theming, dark mode persistence).

## Project visualization
Visit site: https://ivankovalyoff.github.io/Learning-Tailwind-CSS/

## Features

- **Dark / light mode** — toggle with persistent `localStorage` preference
- **Responsive navigation** — hamburger menu on mobile (CSS-only via `<details>`/`<summary>`), hover dropdown on desktop
- **Horizontal carousel** — touch-friendly snap scrolling with previous/next controls and a custom-styled scrollbar that adapts to the active color scheme
- **Animated timeline** — alternating two-column lineup schedule with a live-updating sticky marker
- **Glassmorphism hero** — full-viewport background with a frosted-glass card, custom wave animation, and newsletter signup form
- **Accessible markup** — semantic landmarks (`<header>`, `<main>`, `<section>`), ARIA labels, `role="img"` on CSS background images, `sr-only` form labels, and `<th scope="col">` table headers

## Tech Stack

| Layer | Tool |
|---|---|
| CSS Framework | Tailwind CSS 4 |
| Icons | Font Awesome 6 (Solid) |
| Fonts | Google Fonts — Quicksand (body) |
| Dev server | Browser-Sync |
| Scripting | Vanilla JS (ES6) |

No framework, no bundler, no TypeScript — intentionally lean to focus on CSS fundamentals.

## Getting Started

```bash
# Install dependencies
npm install

# Start Tailwind compiler in watch mode + live-reload dev server
npm run tw:build
```

Then open `src/index.html` in a browser, or let Browser-Sync serve it automatically.

> **Output CSS** is compiled to `dist/output.css`. Never edit that file directly — edit `src/input.css` instead.

## Project Structure

```
tailwind/
├── src/
│   ├── index.html          # Single-page site
│   ├── input.css           # Tailwind source — theme, utilities, components
│   └── assets/
│       ├── images/         # Hero, band photos, logos
│       └── fontawesome/    # Self-hosted FA icon kit
├── dist/
│   └── output.css          # Compiled CSS (generated — do not edit)
└── package.json
```

## Notable Implementation Details

**Tailwind v4 dark mode** — configured with a custom `@variant` so the `dark:` prefix activates via a `.dark` class on `<html>` rather than the OS media query, enabling a user-controlled toggle:

```css
@variant dark (&:where(.dark, .dark *));
```

**CSS-only animated hamburger** — the three-bar icon animates entirely through Tailwind's `group-open:` variant on a `<details>` element — no JavaScript:

```html
<details class="group">
  <summary>
    <div class="group-open:rotate-45 ..."></div>
    <div class="group-open:opacity-0 ..."></div>
    <div class="group-open:-rotate-45 ..."></div>
  </summary>
</details>
```

**Custom scrollbar theming** — the carousel scrollbar is styled to match the pink brand color in both light and dark modes using CSS custom properties exposed by Tailwind v4:

```css
.styled-scrollbar { scrollbar-color: var(--color-pink-400) var(--color-zinc-300); }
.dark .styled-scrollbar { scrollbar-color: var(--color-pink-500) var(--color-zinc-800); }
```

**Custom animation utility** — the hero wave animation uses a `@keyframes` block defined inside `@theme` and a dynamic `animation-delay-*` utility built with `@utility`:

```css
@utility animation-delay-* {
  animation-delay: --value(--animation-delay-*);
  animation-delay: calc(--value(integer) * 1ms);
}
```

## Contact

- LinkedIn: https://linkedin.com/in/ivan-kovalov-197759348
- GitHub: https://github.com/IvanKovalyoff

## Skills Demonstrated

- Tailwind CSS 4 — `@theme`, `@variant`, `@utility`, `@layer`, container queries
- Semantic HTML5 and ARIA accessibility
- CSS custom properties and modern scrollbar APIs
- Responsive design (mobile-first, `md:` breakpoint, `@container`)
- Vanilla JS — DOM manipulation, event delegation, `localStorage`
- CSS animations and staggered timing
- Glassmorphism and gradient design patterns
