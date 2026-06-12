# CLAUDE.md — LogosForge Shared Contracts (`fopearcano/logosforge-ui-contracts`)

> Canonical template:
> `fopearcano/logosforge-architecture` → `repo-templates/logosforge-ui-contracts/CLAUDE.md`.
> If this file ever disagrees with the architecture repo, the architecture
> repo wins.

> **Status: FUTURE SCAFFOLD — no real application code lives here yet.**
> Do not scaffold, build, or integrate this package until the roadmap in
> `fopearcano/logosforge-architecture` (`docs/ROADMAP.md`) explicitly reaches
> **Phase 3** — and only if the Phase 2 decision chose extracting a shared
> UI. Today the only real LogosForge code is `storyplanner` (Python core +
> app) and `logosforge-desktop` (Free Whiteboard Electron alpha).

## Repo identity

This repo will be the **shared language** of the LogosForge ecosystem: the
TypeScript contracts package that will mirror the `storyplanner` API so
every frontend — Free and Pro, desktop and web — speaks the same types,
command names, and event names. Nothing is built here yet, and nothing
consumes this package today.

## What this repo owns

- TypeScript types
- API contracts (request/response types for the `storyplanner` API)
- Project/document models
- Scene/outline/PSYKE types
- Command names (and their payload types)
- Event names (and their payload types)

## What this repo must NOT own

- Runtime application logic of any kind
- UI components, styling, or visual identity
- Python code — behavior lives in `storyplanner`
- Platform-specific code (no Electron, no browser APIs, no network clients)
- App-specific types that only one app uses (those live in that app)

This package is **types and declarative constants only**. If a change here
needs runtime behavior, it is routed to the wrong repo.

## Dependencies

- **Allowed:** development tooling only (TypeScript, build, lint, test).
  Zero runtime dependencies.
- **Forbidden:** importing anything from app repos or shared UI packages.
  Rule: `contracts importing app code` is banned — every frontend in the
  ecosystem will depend on this package, so anything it imports, they all
  inherit.

## Update rules

- This package **mirrors the `storyplanner` API** — it never leads it. Update
  here when (and only when) the core's API surface, document models,
  commands, or events change. Do not invent contract shapes the core does not
  implement.
- Order in the cascade: `storyplanner → THIS REPO → shared UI → apps`.
  Downstream consumers (`logosforge-whiteboard-shared-ui`,
  `logosforge-pro-shared-ui`, and the apps, as each becomes real) update
  after this repo releases.
- Breaking type changes should be explicit and versioned so consumers can
  migrate deliberately.

## Forbidden actions

- Adding React components, hooks with behavior, or any UI code
- Adding network clients, storage, or other runtime logic
- Adding runtime dependencies to `package.json`
- Importing from any other LogosForge repo
- Duplicating a type that already exists here under a new name — extend or
  version instead
- Defining Free-only or Pro-only *visual* concepts; this package serves both
  product lines neutrally

## Architecture source of truth

Ecosystem rules live in **`fopearcano/logosforge-architecture`**. Before any
cross-repo work, read there: `docs/REPO_MAP.md`, `docs/OWNERSHIP_RULES.md`,
`docs/CHANGE_PROTOCOL.md`, `docs/DEPENDENCY_POLICY.md`. Answer the change
protocol questions before editing.
