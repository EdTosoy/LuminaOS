# Phase 1: Implementation Checkpoints (Mission Log)

This document provides granular, "No-Vagueness" directives for AI agents executing Phase 1: **The Orchestrator Core**.

---

## 🟢 Mission 1: Environment & Scaffolding

*Goal: Establish a production-ready Rust environment with ARM multi-arch validation.*

- [ ] **Checkpoint 1.1: Cargo Scaffold**
  - Initialize a new Rust binary project.
  - Setup a workspace structure if needed (e.g., `lumina-core`, `lumina-cli`).
  - **Success**: `cargo build` passes locally.
- [ ] **Checkpoint 1.2: Multi-Arch CI**
  - Create `.github/workflows/ci.yml` with `cross-rs` or `cargo-zigbuild`.
  - Add job for `aarch64-unknown-linux-gnu` cross-compilation.
  - **Success**: GitHub Actions builds both x86 and ARM successfully.
- [ ] **Checkpoint 1.3: CLI Foundations**
  - Implement `clap` v4 with subcommands: `init`, `sync`, `add`, `status`.
  - Stub out the handlers for each subcommand.
  - **Success**: `lumina --help` shows correct subcommands.

---

## 🟡 Mission 2: Registry & State Parsing

*Goal: Implement the safe, declarative YAML engine.*

- [ ] **Checkpoint 2.1: Schema Definition**
  - Map the `lumina.yaml` schema to Rust structs using `Serde`.
  - Support `modules`, `metadata`, and `orchestration` blocks.
  - **Success**: Test suite parses a sample `lumina.yaml` without error.
- [ ] **Checkpoint 2.2: Virtual Root Pathing**
  - Implement logic to resolve `~/.lumina` and handle environment variables (XDG spec).
  - **Success**: Unit test confirms correct path resolution on Linux.
- [ ] **Checkpoint 2.3: Validation Engine**
  - Add logic to verify if source files exist before attempting to sync.
  - **Success**: CLI returns a clean error if a registry entry points to a missing file.

---

## 🟠 Mission 3: The Shadow Linker (The "Director")

*Goal: Execute atomic, safe symlinking from the Virtual Root.*

- [ ] **Checkpoint 3.1: Staging Logic**
  - Implement the "Shadow" directory (`~/.lumina/staging/`) where configs are pre-validated.
  - **Success**: CLI can copy files into the staging area.
- [ ] **Checkpoint 3.2: Collision & Backup**
  - Implement "Move-to-Bak": If a file exists at the target, rename it to `.bak` before linking.
  - **Success**: Existing `~/.bashrc` is safely backed up before being replaced by a symlink.
- [ ] **Checkpoint 3.3: Atomic Symlinking**
  - Execute the final symlink creation using `std::os::unix::fs::symlink`.
  - **Success**: File at `~/.config/hypr/hyprland.conf` is a verifiable link to the `~/.lumina` registry.

---

## 🔴 Mission 4: Hardware Awareness

*Goal: Detect modular hardware (Framework) to apply optimized profiles.*

- [ ] **Checkpoint 4.1: DMI/Sysfs Detection**
  - Implement a Rust module to read `/sys/class/dmi/id/board_name`.
  - Detect "Laptop-13-AMD" or "Laptop-16".
  - **Success**: `lumina status` correctly identifies the hardware model.
- [ ] **Checkpoint 4.2: Automated Profile Selection**
  - Logic to inject Framework-specific kernel parameters or Hyprland scaling based on detection.
  - **Success**: `lumina init` produces a YAML pre-configured for the detected hardware.

---

## 🟣 Mission 5: The Native Bootstrap (Welcome Flow)

*Goal: The first 5-minute experience on a live system.*

- [ ] **Checkpoint 5.1: CLI-Based Welcome**
  - Implement a `lumina welcome` command that guides the user through Git setup and Registry creation.
  - **Success**: User has a functional `lumina.yaml` in `~/.config/lumina/` after wizard completion.
- [ ] **Checkpoint 5.2: Matugen Auto-Generation**
  - Logic to pick a default "Lumina Gold/Obsidian" palette based on hardware detection.
  - **Success**: System colors shift to the primary Lumina palette immediately after init.

---

## 🚀 Final Verification (Phase 1 Exit)

- [ ] **Checkpoint 5.1: The "Clean Machine" Test**
  - On a fresh Arch install, run `lumina init && lumina sync`.
  - **Success**: Full desktop environment is functional in under 60 seconds.
