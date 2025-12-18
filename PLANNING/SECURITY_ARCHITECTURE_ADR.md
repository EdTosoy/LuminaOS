# ADR 004: Security Architecture & Least Privilege

**Status**: Accepted | **Date**: 2025-12-18

## Context

Lumina OS aims to be the most secure professional workstation while providing the polish of a consumer product. We need a model that protects the user without treating them like a child (Apple-style).

## Decision

Adopt a **Layered Defense-in-Depth** model centered on the `lumina` orchestrator.

### 1. The "Observer" Sandbox

The Lumina Assistant (Observer) runs with **Read-Only** access to system logs and project metadata. It cannot execute `sudo` or modify system binaries without explicit, authenticated user consent (via Polkit).

### 2. OCI Safe-Rooms

Project-specific development happens in **Rootless Containers (Podman)**.

- **Rationale**: If a malicious npm/pip package is executed, the impact is confined to the "Safe-Room" container, protecting the host Arch OS.

### 3. Verifiable State

The `lumina.yaml` registry acts as an audit log.

- **Decision**: All system-level changes managed by the CLI are logged and can be rolled back using Btrfs/ZFS snapshots.

### 4. Hardened Kernel & UFW

Lumina OS ships with the **BORE/Hardened Kernel** and a pre-configured **UFW (Uncomplicated Firewall)** that blocks all non-essential telemetry.

## Rationale

- **Trust through Transparency**: Users can audit the registry and the container configs.
- **Resilience**: The host system remains pristine even during intensive, multi-tool development.
