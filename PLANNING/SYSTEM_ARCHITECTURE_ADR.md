# Architectural Decision Records (ADR)

This document tracks the "Why" behind the core technical architecture of Lumina OS.

---

## ADR 001: Language Selection - Rust

**Status**: Accepted | **Date**: 2025-12-18

### ADR 001: Context

We need a core orchestrator binary (`lumina`) to manage system state, themes, and phone sync.

### ADR 001: Decision

Use **Rust** for the core system logic.

### ADR 001: Rationale

- **Memory Safety**: Eliminates entire classes of system crashes common in C/C++.
- **Blazing Performance**: Critical for maintaining the "Zero-Drag" workstation feel.
- **Modern Tooling**: Cargo provides a robust dependency and build system for a complex OS.

---

## ADR 002: Environment Isolation - OCI Containers (Podman/Docker)

**Status**: Accepted | **Date**: 2025-12-18

### ADR 002: Context

Maintaining 100% reproducible development environments ("Statelessness") is traditionally prone to configuration drift.

### ADR 002: Decision

Utilize OCI-compliant containers to isolate project-level toolchains.

### ADR 002: Rationale

- **Absolute Reproducibility**: If it runs in the container, it runs on every Lumina machine.
- **System Hygiene**: Prevents "Dependency Hell" from polluting the host Arch Linux base.
- **Maintainability**: Vastly simpler than building a custom symlink-orchestration layer for every language.

---

## ADR 003: Stability Tier - Curated Repositories (Lumina-Stable)

**Status**: Accepted | **Date**: 2025-12-18

### ADR 003: Context

Vanilla Arch is prone to breaking desktop components during upstream updates.

### ADR 003: Decision

Implement a 24-48 hour delay on package updates via a curated repository tier.

### ADR 003: Rationale

- **Risk Mitigation**: Catch breaking changes in a testing environment before they reach users.
- **Reliability**: Provides the "stability of a LTS" with the "speed of a Rolling Release."
