<!-- Paste this section into this repo's README.md -->

## Architecture

This repository is part of the **LogosForge** ecosystem, governed by the
architecture/control repo
[`fopearcano/logosforge-architecture`](https://github.com/fopearcano/logosforge-architecture).

- **Product/layer:** LogosForge Shared Contracts
- **Status:** **future scaffold** — a placeholder. No real code lives here
  yet, and nothing consumes this package. Do not build it out before the
  roadmap reaches Phase 3 (architecture repo, `docs/ROADMAP.md`).
- **Role (future):** the shared language of the ecosystem — TypeScript
  types, API contracts, project/document models, scene/outline/PSYKE types,
  command names, and event names, mirroring the `storyplanner` API.
- **Will own:** every shape and name that frontends must agree on.
- **Must not own:** runtime app logic, UI components, Python code,
  platform-specific code. Types and declarative constants only.
- **Will be consumed by:** both shared UI packages and all apps.
- **Depends on:** nothing in the ecosystem (zero runtime dependencies).

Before changing anything here, read this repo's `CLAUDE.md` and the
architecture repo's `docs/REPO_MAP.md`, `docs/CHANGE_PROTOCOL.md`, and
`docs/ROADMAP.md`. This package will follow the core — never lead it.
