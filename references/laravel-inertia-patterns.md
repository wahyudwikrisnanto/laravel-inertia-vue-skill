# Laravel Inertia Patterns

## Table of Contents
- Laravel and Inertia contract rules
- Laravel security baseline
- Modularization, traits, and helpers

## Laravel and Inertia contract rules

- Define page data shape in Laravel controller/resource output first, then mirror it in Vue TypeScript types.
- Keep validation and authorization in backend; keep rendering and interaction logic in frontend.
- When changing a field, update both sides in the same change set: backend payload + frontend typing/usage.
- Keep Inertia page props minimal and explicit; avoid passing unused data.
- Use `FormRequest` classes for request validation instead of inline controller validation.
- Use `ApiResource` classes to map backend response data consistently.
- Add `declare(strict_types=1);` to PHP classes and keep method signatures typed.
- Keep controllers orchestration-only; move business rules to service classes.
- Pass DTOs to services for stable, typed data contracts.
- Apply clean code principles: single responsibility, small methods, intention-revealing names, and low coupling.
- Do not repeat code across the codebase; centralize reusable behavior in components, composables, services, DTOs, traits, and shared helpers.

## Laravel security baseline

- Enforce authentication and authorization at route/controller boundaries using middleware, policies, and gates.
- Use `FormRequest` for validation and authorization; never trust raw client payloads.
- Prevent mass-assignment issues with explicit `$fillable`/`$guarded` rules and DTO mapping.
- Sanitize and normalize user input where needed before persistence or rendering.
- Escape output by default and only render HTML from trusted/sanitized sources.
- Apply rate limiting and throttling for sensitive endpoints (login, password reset, OTP, public forms).
- Keep CSRF protection enabled for state-changing requests and keep session/cookie settings secure (`http_only`, `secure`, `same_site`).
- Keep secrets in environment variables only; never hardcode tokens or credentials in code.

## Modularization, traits, and helpers

- Prefer modular feature/domain structure over large mixed folders.
- Use traits for cross-cutting class behavior that is reused in multiple classes.
- Keep traits cohesive and small; avoid dumping unrelated methods into one trait.
- Use helper functions for pure reusable utilities, not for core business workflows.
- Keep business rules in services/actions and pass typed DTOs, with helpers/traits supporting those modules.

Recommended modular directory pattern:

```text
app/
  Modules/
    User/
      Actions/
      DTOs/
      Http/
        Controllers/
        Requests/
        Resources/
      Models/
      Policies/
      Services/
      Traits/
    Billing/
      Actions/
      DTOs/
      Http/
        Controllers/
        Requests/
        Resources/
      Models/
      Services/
      Traits/
  Support/
    Helpers/

resources/
  js/
    modules/
      user/
        pages/
        components/
        composables/
        types/
      billing/
        pages/
        components/
        composables/
        types/
    shared/
      components/
      composables/
      types/
      utils/
```

Pattern rules:
- Group by feature/domain first, then by layer.
- Keep request/response classes close to their module (`Requests`, `Resources`).
- Keep DTOs, services, and traits inside their module unless truly cross-module.
- Put cross-cutting helpers in `app/Support/Helpers` and frontend utilities in `resources/js/shared/utils`.
- Avoid creating generic catch-all folders that mix unrelated modules.
