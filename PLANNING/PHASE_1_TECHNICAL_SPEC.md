# Phase 1 Technical Specification: The Orchestrator

This document defines the implementation details for the first milestone of Lumina OS: **The Rust CLI and Stateless Registry**.

---

## 1. Binary Architecture: `lumina`

The core binary will be a modular Rust CLI using `clap` for subcommands and `serde` for registry parsing.

### Subcommands

- `lumina init`: Detects hardware (Framework modules) and initializes a default `lumina.yaml`.
- `lumina sync`: Reads the registry and applies symlinks and package states.
- `lumina add <module>`: Interactively adds a new config module (e.g., `waybar`, `hyprland`).

### Multi-Arch Validation

- **Requirement**: Mandatory `aarch64` (ARM64) cross-compilation in CI.
- **Logic**: Rust core must remain architecture-agnostic to ensure "Future-Proof" hardware transitions.

---

## 2. Registry Schema (`lumina.yaml`)

A declarative YAML structure defining the system's "Soul".

```yaml
version: 1.0
metadata:
  identity: "Professional-Workstation"
  target: "Framework-13-AMD"

modules:
  shell:
    source: "./config/hyprland"
    target: "~/.config/hypr"
    enabled: true
  
  orchestration:
    missions:
      nebula:
        path: "~/Projects/nebula"
        image: "lumina/rust-mission:latest"
        env:
          - KEY=VAL
```

---

## 3. The "Shadow Linker" Logic

To ensure stability, the CLI follows a **Staging -> Linking** pattern.

1. **Staging**: Registry files are validated for syntax and existence.
2. **Virtual Root**: Files are staged in `~/.lumina/active/`.
3. **Atomic Linking**: The CLI creates relative symlinks to the home directory.
4. **Collision Check**: If a file already exists at the target, the CLI creates a `.bak` before proceeding.

---

## 4. Performance Goals & KPIs

- **Registry Parse**: < 10ms.
- **Symlink Sync (100 files)**: < 100ms.
- **Binary Footprint**: < 15MB (Statically linked).
- **Cold Boot Interference**: Zero (The binary should not delay shell login).

---

## 5. Error Handling

We use the `anyhow` crate for professional error narratives.

- **User-Friendly Logs**: "MISSION FAILED: Permission denied at ~/.config/hypr. Please run with sudo or check permissions."
