# Phase 1: Hyper-Granular Mission Log (Foundations)

This document provides absolute-clarity directives for AI agents. **Do not deviate from these architectural constraints.**

---

## 🟢 Mission 1: Environment & Scaffolding

*Goal: Establish a production-ready, multi-arch Rust workspace.*

### [x] Checkpoint 1.1: Cargo Workspace Scaffold

- **Task**: Initialize a Rust workspace to separate the CLI frontend from the logic backend.
- **Directives**:
  - `cargo new lumina` (The binary/CLI gatekeeper).
  - `cargo new lumina-core --lib` (All business logic: registry, pathing, symlinking).
  - Use `[workspace]` in a top-level `Cargo.toml`.
- **Architectural Guardrail**:
  - Do NOT put logic in `main.rs`. Keep the CLI layer thin.
- **Verification**: `cargo build` must succeed with zero warnings.

### [ ] Checkpoint 1.2: Multi-Arch CI (AARCH64)

- **Task**: Implement GitHub Actions that verify ARM cross-compilation.
- **Directives**:
  - Use `actions-rs/cargo@v1` with the `cross` tool.
  - Targets: `x86_64-unknown-linux-gnu` AND `aarch64-unknown-linux-gnu`.
- **Architectural Guardrail**:
  - If a crate does not support `aarch64`, it must be replaced at this stage.
- **Verification**: Check GitHub Actions tab for successful builds on both architectures.

### [ ] Checkpoint 1.3: CLI Anatomy (Clap v4)

- **Task**: Implement the base CLI structure with subcommands.
- **Directives**:
  - Crates: `clap` (with `derive` and `string` features).
  - Commands: `init` (flags for hardware), `sync` (dry-run flag), `status` (JSON output flag).
- **Verification**: Run `cargo run -- --help` and verify all commands and flags are documented correctly.

---

## 🟡 Mission 2: Registry & State Engine

*Goal: The "Soul" of the OS—safe, declarative, and stateless.*

### [ ] Checkpoint 2.1: Semantic Schema (Serde)

- **Task**: Map `lumina.yaml` to Rust structs with strict type safety.
- **Directives**:
  - Crates: `serde`, `serde_yaml`, `schemars` (for JSON schema generation).
  - Support `Optional` fields and defaults (e.g., `enabled: true` if missing).
- **Verification**: Create `tests/schema_validation.rs` that fails if a malformed YAML is passed.

### [ ] Checkpoint 2.2: Virtual Root resolution (XDG/Paths)

- **Task**: Logic to compute absolute paths correctly across machines.
- **Directives**:
  - Crates: `dirs`, `camino` (for UTF-8 path safety).
  - Logic: Defaults to `~/.config/lumina/` but respects `LUMINA_HOME` env var.
- **Verification**: Unit test that mock-resolves a path in a temporary directory.

### [ ] Checkpoint 2.3: Integrity Pre-Flight

- **Task**: A function that checks if every `source` path in the YAML exists.
- **Directives**:
  - Return a grouped error report (don't fail on the first error).
- **Verification**: `lumina sync --dry-run` must report missing files as "WARNING" or "ERROR" without stopping the parse.

---

## 🟠 Mission 3: The Shadow Linker

*Goal: Atomic, non-destructive symlinking logic.*

### [ ] Checkpoint 3.1: Staging Operations

- **Task**: Create a "Staging Area" in `~/.lumina/staging`.
- **Directives**:
  - Logic: Copy registry files into staging to verify content before linking.
- **Architectural Guardrail**:
  - Never link directly from a Git repo to a system path; always go through staging to allow for "Pre-Link" transformation services.
- **Verification**: Verify files appear in `~/.lumina/staging` after `lumina sync --stage-only`.

### [ ] Checkpoint 3.2: Collision & Backup Logic

- **Task**: Implement "Safe-Replace" via `.bak`.
- **Directives**:
  - Logic: If file `~/.zshrc` exists and is NOT a symlink, rename to `~/.zshrc.bak_<timestamp>`.
  - If it IS a symlink to a Lumina path, overwrite it.
- **Verification**: Run sync on a machine with existing configs and verify `.bak` files are created.

### [ ] Checkpoint 3.3: Atomic Link Execution

- **Task**: Perform the final `ln -s` equivalent in Rust code.
- **Directives**:
  - Use relative symlinks where possible to preserve portability.
- **Verification**: `ls -l ~/.config/hypr` must point to the Lumina staging area.

---

## 🔴 Mission 4: Hardware Intelligence (Framework)

*Goal: Machine-specific profile injection.*

### [ ] Checkpoint 4.1: DMI Probing

- **Task**: Read the system's hardware ID.
- **Directives**:
  - Read `/sys/class/dmi/id/product_name` directly (no external shell-out).
- **Verification**: CLI prints "Hardware Detected: Framework Laptop 13 (AMD)" on boot.

### [ ] Checkpoint 4.2: Profile Overlays

- **Task**: Merge hardware-specific YAML snippets into the main config.
- **Directives**:
  - Logic: `base.yaml` + `framework_amd.yaml`.
- **Verification**: `lumina status` shows which hardware-specific modules are active.

---

## 🟣 Mission 5: The Native Bootstrap (Welcome Flow)

*Goal: The first 5 minutes.*

### [ ] Checkpoint 5.1: Interactive Wizard

- **Task**: A CLI-based setup wizard for new users.
- **Directives**:
  - Crates: `dialoguer` or `inquire`.
  - Steps: Git URL -> Identity Name -> Hardware Confirmation.
- **Verification**: Run `lumina welcome` and verify a valid `lumina.yaml` is generated at the end.

### [ ] Checkpoint 5.2: Matugen Initializer

- **Task**: Trigger the first color-generation on a raw system.
- **Directives**:
  - Logic: Pick a primary color from the Lumina brand book if no wallpaper is set.
- **Verification**: System colors shift to "Lumina Gold" after the first `sync`.
