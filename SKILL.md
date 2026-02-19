---
name: laravel-inertia-vue-clean-minimalist
description: Build, redesign, and refactor Laravel + Inertia + Vue applications with TypeScript using either minimalist or highly informative UI direction, while enforcing backend/frontend clean architecture, pnpm package-management consistency, and Laravel/Vue security best practices. Always prioritize usability and UX best practices over visual decoration so systems are easy to use before they are beautiful. Use when requests involve Laravel-Inertia-Vue UI work, Tailwind consistency, reusable components, backend-frontend contract alignment, FormRequest validation, ApiResource mapping, strict PHP typing, service + DTO patterns, secure auth/authorization and input/output handling, clean reusable code standards, dashboards, data-heavy pages, dense table/filter/sort UX, or requests to make UI as informative as possible.
---

# Laravel Inertia Vue Clean Minimalist

Apply this skill in Laravel + Inertia + Vue projects to deliver either minimalist or information-dense interfaces while preserving backend/frontend contract integrity and prioritizing ease of use over visual flourish.

## Workflow

1. Identify context and constraints
- Determine framework details first: Laravel version, Inertia setup, Vue 3 + TypeScript structure, Tailwind/CSS approach, and existing component conventions.
- Check package-manager constraints and use `pnpm` for dependency management and project scripts.
- Preserve existing architectural patterns unless the user asks for structural changes.
- Extract non-negotiables: required content, brand colors, accessibility needs, and mobile breakpoints.
- Identify UI direction explicitly: `minimalist` (calm/restrained) or `informative` (maximum clarity and data visibility).
- Define core user tasks and success criteria first so layout and component choices optimize completion speed and error prevention.

2. Define backend and frontend boundaries
- Define backend responsibilities in Laravel (routes, controllers, validation, policies, and Inertia response payloads).
- Define frontend responsibilities in Vue (page components, shared UI components, composables, and client-side interactions).
- Keep a clear typed contract for Inertia props so backend payload shape and frontend expectations stay synchronized.
- Update both sides when fields change: Laravel controller/resource output and Vue TypeScript page/component types.
- Apply Laravel backend best practices: use `FormRequest` for validation, `ApiResource` for response mapping, and `declare(strict_types=1);` in PHP files.
- Keep controllers thin by delegating business logic to service classes.
- Pass structured DTO objects to service classes instead of raw request arrays.
- Use traits for cross-cutting reusable behavior shared by multiple classes.
- Use helper functions only for framework-agnostic utility logic that does not belong to a specific service/model.
- Organize code in a modular pattern (for example by domain/feature) so backend and frontend are easy to evolve independently.
- Follow a feature-first modular directory pattern for both Laravel and Inertia Vue (see `references/laravel-inertia-patterns.md`).
- Apply clean code principles: small focused methods, meaningful names, clear boundaries, and single responsibility per class.
- Implement Laravel security best practices by default: enforce auth/policy checks, server-side validation/sanitization, mass-assignment safety, rate limiting for sensitive endpoints, and secure headers/session/cookie configuration.

3. Standardize Tailwind when requested or missing
- If Tailwind is not installed and the task needs it, install with the official workflow for the project type (Vite Vue or Nuxt).
- Use `pnpm` commands for installs and scripts unless the user explicitly requests another package manager.
- Add shared Tailwind tokens in config (`colors`, `spacing`, `borderRadius`, and typography defaults) before writing many classes.
- Define semantic color roles in Tailwind (`primary`, `secondary`, `warning`, `danger`, plus neutral roles) and use those roles everywhere.
- Avoid arbitrary values unless there is a clear one-off requirement; prefer tokenized classes.
- Keep utility usage consistent across files and extract repeated class groups into reusable Vue components.

4. Enforce TypeScript and Vue best practices
- Default to TypeScript for all new Vue code (`<script setup lang="ts">`, typed composables, typed stores, typed emits/props).
- Prefer explicit interfaces/types for component contracts and shared domain models.
- Avoid `any`; use unions, generics, and utility types where needed.
- Keep side effects out of components when possible; move reusable logic into typed composables.
- Use Vue best practices for reactivity (`ref`/`computed`/`watch` deliberately), prop immutability, and clear one-way data flow.
- Implement Vue security best practices by default: avoid `v-html` for untrusted content, keep auth/authorization decisions server-backed, avoid token leaks in local storage/logs, and prefer CSP-compatible patterns.

5. Define minimalist direction before editing code
- Write a short direction statement in working notes: typography mood, spacing density, color restraint, and interaction tone.
- Keep visual hierarchy explicit with size, weight, spacing, and contrast. Do not rely on decoration.
- Limit palette and surface treatments; use whitespace as a primary layout tool.

6. Define informative direction when requested
- Prioritize information hierarchy over visual minimalism: show key metrics, context labels, status, trends, and actionable next steps on first view.
- Increase useful density without clutter: compact spacing, clear grouping, progressive disclosure for advanced details, and consistent scan patterns.
- Prefer explicit labels over ambiguous icons and surface units, timestamps, status meaning, and data freshness.
- Use tables/lists/charts only when each element adds decision value; remove decorative content that does not improve comprehension.
- Include filtering, sorting, search, and quick segmentation controls when the page is data-heavy.

7. Implement with Vue-first component discipline
- Keep templates readable and shallow; split complex blocks into focused child components.
- Use semantic HTML inside Vue templates (`main`, `section`, `nav`, `header`, `footer`, proper heading order).
- Keep state minimal and colocated; remove style-only state that can be replaced by CSS.
- Prefer design tokens through CSS variables for spacing, radii, borders, and colors.
- Always check existing components before writing new code.
- Build and reuse shared UI components (buttons, inputs, cards, alerts, badges) to keep styling consistent across the app.
- Avoid duplicating the same UI markup and styles in multiple pages; extract repeated patterns into components and shared style tokens.
- Use semantic color roles consistently (`primary`, `secondary`, `warning`, `danger`, plus neutral roles) instead of ad-hoc per-screen color choices.
- If a class group repeats across files, extract it into a reusable component or composable.
- Do not use inline styles.
- Do not use arbitrary hex colors directly in templates.
- Do not duplicate class blocks across files.
- Do not repeat code anywhere; extract shared logic into reusable components, composables, services, DTOs, and helpers.
- Prioritize UX best practices by default: clear information scent, predictable navigation, low cognitive load, explicit feedback, forgiving inputs, and strong error recovery.

8. Verify quality gates
- Check visual noise: eliminate unnecessary shadows, borders, gradients, and competing accent colors.
- Check density: ensure touch targets remain usable while spacing stays breathable.
- Check accessibility: keyboard navigation, focus visibility, contrast, and reduced-motion support.
- Check responsiveness: mobile-first layout with intentional scaling, not compressed desktop UI.
- Check information clarity: important metrics, statuses, and actions are understandable within one screen scan.
- Check usability-first outcomes: primary tasks are obvious, flows are short, errors are explainable/recoverable, and interaction cost stays low.

## Definition Of Done

- Responsive across target breakpoints.
- Keyboard accessible for all interactive controls.
- Contrast is acceptable for text and UI states.
- Shared components are reused instead of per-page duplication.
- Repeated utility/class blocks are extracted and centralized.
- Code is TypeScript-first and follows Vue + TypeScript best practices.
- Backend uses `FormRequest`, `ApiResource`, strict PHP typing, service pattern, and DTO-based service inputs.
- Backend and frontend follow Laravel/Vue security best practices (authorization, validation, sanitization, safe rendering, and secure auth flows).
- Traits/helpers are used intentionally for reuse, and code follows a modular pattern.
- No duplicated code remains; implementation is clean and reusable across backend and frontend.
- For informative mode, key metrics, states, and primary actions are visible and interpretable without drilling into secondary screens.
- UX best practices are applied by default, and usability is prioritized over purely visual enhancements.

## Output Expectations

- For Laravel + Inertia requests, provide both backend and frontend updates when needed.
- Backend output should include concrete route/controller/validation/response adjustments required by the UI change.
- Use `pnpm` for package-install and script commands in all implementation steps unless user constraints require otherwise.
- For new UI requests, deliver complete Vue component/page code with scoped styling strategy that matches the project conventions.
- For refactors, preserve behavior and data contracts while simplifying structure and visual language.
- Explain design decisions briefly in implementation notes tied to code changes.
- Include responsive behavior and accessibility adjustments by default.
- For informative-style requests, include explicit information hierarchy decisions (what is primary, secondary, and contextual).
- Include UX rationale for key interactions (navigation, forms, feedback states, and error handling), prioritizing ease of use over aesthetics.

## References

- For Vue, TypeScript, Tailwind, and UI consistency patterns, read `references/vue-minimalist-patterns.md`.
- For Laravel, Inertia contracts, services/DTOs, traits/helpers, and modular backend structure, read `references/laravel-inertia-patterns.md`.
