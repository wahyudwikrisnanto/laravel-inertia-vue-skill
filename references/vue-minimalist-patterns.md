# Vue Minimalist Patterns

## Table of Contents
- Tailwind setup and consistency
- TypeScript and Vue best practices
- Vue security baseline
- UX-first baseline
- Design tokens
- Layout patterns
- Informative UI patterns
- Typography rules
- Interaction and motion
- Accessibility checks
- Refactor checklist

## Tailwind setup and consistency

Install (Vue 3 + Vite):

```bash
pnpm add -D tailwindcss @tailwindcss/vite
```

```ts
// vite.config.ts
import tailwindcss from '@tailwindcss/vite'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [tailwindcss()]
})
```

```css
/* src/style.css */
@import "tailwindcss";
```

Install (Nuxt):

```bash
pnpm dlx nuxi@latest module add @nuxtjs/tailwindcss
```

Consistency rules:
- Configure semantic palette roles and reuse them: `primary`, `secondary`, `warning`, `danger`, `neutral`.
- Keep spacing/radius scale centralized; do not mix arbitrary pixel values throughout components.
- Prefer component reuse over repeating long utility strings.
- When utility strings repeat, create shared Vue UI components instead of copy-pasting markup.
- Keep one interaction pattern per component family (for example, same focus ring and hover behavior for all primary buttons).
- Always review existing components before creating new ones.
- Do not use inline styles.
- Do not use arbitrary hex colors in templates.
- Do not duplicate class blocks across files.
- If a class group repeats across files, extract a reusable component or composable.

## TypeScript and Vue best practices

- Use `<script setup lang="ts">` for all new Vue SFCs.
- Type `defineProps`, `defineEmits`, and shared component interfaces explicitly.
- Prefer typed composables for shared logic and avoid duplicating stateful behavior in components.
- Avoid `any`; use safe narrowing, union types, and generics where applicable.
- Keep computed state derived and pure; keep watchers focused on explicit side effects.
- Keep prop flow one-way and emit typed events for upward communication.

## Vue security baseline

- Treat backend as the source of truth for authorization; never rely on hidden UI controls alone.
- Avoid `v-html` for untrusted content; if HTML rendering is required, sanitize server-side and allowlist tags.
- Keep CSRF protection enabled and use framework defaults for cookie/session handling.
- Avoid storing long-lived sensitive tokens in local storage; prefer secure, httpOnly cookies with backend session auth when possible.
- Do not log secrets, tokens, or PII in browser console or analytics events.
- Use strict input validation on both client (UX) and server (enforcement), with server validation mandatory.
- Keep dependency installs and scripts on `pnpm` for lockfile consistency.

## UX-first baseline

Apply UX best practices before visual polish.

- Prioritize task completion speed, error prevention, and clarity over decorative styling.
- Keep navigation predictable with stable placements, clear labels, and obvious back/exit paths.
- Keep flows short: minimize steps, prefill sensible defaults, and reduce required input fields.
- Provide immediate and explicit feedback for loading, success, warning, and error states.
- Use actionable error messages that explain cause and recovery, not generic failure text.
- Design forgiving forms: preserve user input after validation errors and highlight exact fields to fix.
- Keep interaction targets clear and consistent across desktop and mobile.
- Avoid hidden critical actions behind ambiguous icons or hover-only affordances.
- Support progressive disclosure for advanced options while keeping primary actions obvious.
- Validate usability on primary user journeys before visual refinements.

## Design tokens

Define tokens once and reuse them:

```css
:root {
  --bg: #f7f7f5;
  --surface: #ffffff;
  --text: #1c1c1a;
  --muted: #6d6d68;
  --line: #dfdfd8;
  --accent: #1f6f5f;

  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --radius-1: 0.375rem;
}
```

Rules:
- Keep one accent color by default.
- Use border and spacing before shadow.
- Keep corner radii subtle and consistent.

## Layout patterns

Use these safe structures:
- Landing: centered hero, single primary CTA, concise feature grid.
- Dashboard: fixed or sticky top bar, clear content sections, restrained card styles.
- App shell: sidebar + content with generous gutters and low-contrast separators.

Implementation guidance:
- Prefer CSS grid/flex with `gap` tokens.
- Use max-width containers for readability (`64rem`-`80rem`).
- Scale from mobile first and avoid shrinking dense desktop layouts.

## Informative UI patterns

Use when the user asks for maximum clarity, richer data visibility, or dashboard-style pages.

Information hierarchy:
- Surface top KPIs first with clear labels, units, and trend direction.
- Put segmentation controls (date range, status, owner, category) near the KPIs.
- Keep primary table/list directly below summary metrics so overview and detail stay connected.
- Add concise context text when metrics can be misread (for example, data freshness or calculation scope).

Data-heavy components:
- Prefer typed table schemas and column configs for consistency and reuse.
- Include sortable columns, server-backed filtering, search, and pagination for large datasets.
- Use status chips with text plus color; never rely on color only.
- Provide empty, loading, and error states with actionable recovery guidance.

Density and readability:
- Use compact spacing modes only where scan speed improves comprehension.
- Align numbers by decimal/place value and use monospaced numerals when helpful.
- Keep labels short and explicit; avoid unexplained abbreviations.
- Group related actions and keep destructive actions visually distinct.

Interaction patterns:
- Preserve filter state in URL/query params for shareable, reproducible views.
- Use sticky headers for large tables when it improves scanning.
- Support keyboard navigation for table rows, controls, and pagination.
- Keep chart usage purposeful; pair visual trends with numeric values.

## Typography rules

- Use one primary font family unless brand constraints require alternatives.
- Keep heading scale tight to avoid loud hierarchy jumps.
- Use color and spacing for hierarchy; use uppercase sparingly.
- Keep line length near 45-75 characters for long text.

## Interaction and motion

- Keep transitions short (`120ms`-`220ms`) and purposeful.
- Animate opacity/transform; avoid layout-jank properties.
- Add visible focus states that fit the palette.
- Respect reduced motion preferences.

## Accessibility checks

- Preserve semantic structure and heading order.
- Ensure contrast meets WCAG targets for text and controls.
- Verify keyboard access for nav, forms, dialogs, and menus.
- Keep touch targets comfortably tappable.

## Refactor checklist

- Remove decorative wrappers not needed for layout or semantics.
- Collapse repetitive utility classes into component-level styles/tokens when clearer.
- Preserve props/events contracts while simplifying markup.
- Reduce one-off color/spacing values in favor of tokens.
- Confirm behavior parity before visual polish.
- For informative mode, confirm primary insights are visible without opening modals or secondary pages.
- Confirm key user tasks are easier and faster after refactor, not only visually cleaner.
