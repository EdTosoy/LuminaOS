# Developer Experience (DX) Specification

Lumina OS is built by professionals, for professionals. Our internal bar for code quality and contributor flow must reflect our product's "Zero-Drag" promise. We operate under a **"Human-led, Agent-executed"** model.

---

## 1. The "Chief Editor" Workflow

While AI agents (like Antigravity) handle the heavy lifting of code generation and documentation structure, the human user maintains the role of **Chief Editor**.

- **Architectural Veto**: The Human Editor must approve any architectural shift before implementation.
- **Taste Verification**: AI produces logic; the Human provides **Taste**. All UI/UX changes must be visually verified for "WOW factor."
- **ADR Enforcement**: No significant technical fork is taken without a physical Architectural Decision Record (ADR) file being created first.

---

## 2. The 10-Minute Contributor Rule

A new developer should be able to clone the repo and have a working development environment in under 10 minutes.

- **Pre-requisites**: Docker/Podman, Rust (stable).
- **Tooling**: A single `just` or `make` file for all common tasks.
- **Multi-Arch Readiness**: Contributor environments should ideally support ARM cross-compilation as a primary target.

---

## 3. Commit & Review Standards

We follow **Conventional Commits** to ensure a clean, machine-readable history.

- `feat:`: New features.
- `fix:`: Bug fixes.
- `docs:`: Documentation only.
- `chore:`: Maintenance/Infrastructure.

**Pull Request Requirements**:

- All linting must pass in CI.
- Documented proof of testing on a Framework target (or VM equivalent).
- No direct pushes to `main` or `develop`.

---

## 4. The "Library of Truth"

Every significant code change must be accompanied by an update to the core `.md` library.

- If you change how themes work -> Update `UI_UX_SPEC.md`.
- If you change how phone sync works -> Update `INTEGRATION_BLUEPRINT.md`.

---

## 5. Testing Philosophy

- **Unit Tests**: Mandatory for all logic in the `lumina` Rust binary.
- **Integration Tests**: Mission-Aware environments must be tested for registry-consistency.
- **UI Tests**: Visual changes must be accompanied by screenshots in the PR.
