# Spec: Upgrade Solution from .NET 8 to .NET 10

## 1. Overview

Upgrade the `MyCorner` Blazor WebAssembly app (and supporting CI/docs) from .NET 8 to .NET 10, so the site continues to build, run, and pass the existing Playwright E2E suite.

- **App:** `MyCorner` (Blazor WebAssembly)
- **Current target:** `net8.0`
- **Target:** `net10.0`

## 2. Scope

### In scope

- Update target framework and package references to .NET 10.
- Update build/publish paths and .NET SDK versions in CI workflows and Lighthouse config.
- Update documentation references (`AGENTS.md`).
- Keep Playwright E2E tests passing.

### Out of scope

- New features or game content.
- Changes to command logic, locations, or styling.

## 3. Changes

| Area | Change |
|---|---|
| `MyCorner/MyCorner.csproj` | `TargetFramework` `net8.0` -> `net10.0`; package versions `8.0.16` -> `10.0.15`. |
| `.github/workflows/*.yml` | SDK `8.0` -> `10.0`; publish paths `net8.0` -> `net10.0`. |
| `lighthouserc.json` | Published output path `net8.0` -> `net10.0`. |
| `AGENTS.md` | .NET 8 -> .NET 10 references. |
| `tests/e2e/playwright.config.ts` | Run web server in Release configuration to avoid dev-only hot-reload console noise. |

## 4. Acceptance criteria

- [ ] Site builds (`dotnet build MyCorner/MyCorner.csproj`).
- [ ] Site runs (`dotnet run --project MyCorner`).
- [ ] Playwright E2E tests pass (`npx playwright test`).

## 5. Definition of Done

- Build passes.
- Playwright tests pass.
- Lighthouse CI thresholds remain met.