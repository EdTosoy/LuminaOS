# Phase 4: Implementation Checkpoints (Hardening & Longevity)

This document provides granular directives for Phase 4: **The "Longevity Engine"**.

---

## 🟢 Mission 1: The BORE Kernel & Thermal Logic

*Goal: Optimize the kernel for "Zero-Drag" responsiveness and modular hardware health.*

- [ ] **Checkpoint 1.1: Custom Kernel Build**
  - Implement a `just` task or script to compile the Linux-BORE (Burst-Oriented Response Encoder) kernel tailored for Framework AMD/Intel.
  - **Success**: System boots into the Lumina-BORE kernel with verifiable scheduler improvements.
- [ ] **Checkpoint 1.2: P-State & Thermal Profiles**
  - Logic to automatically switch CPU scaling drivers (P-State) based on mission context (Low Power for Writing, High Performance for Compiling).
  - **Success**: Thermal throttle drops significantly during "Low-Drag" missions.

---

## 🟡 Mission 2: Deep Security Hardening (Defense-in-Depth)

*Goal: Move from "Containerized Apps" to a "Hardened System Core".*

- [ ] **Checkpoint 2.1: UFW/Firewall Mission Policy**
  - Automatically open/close ports based on the active mission (e.g., block all traffic except Git during "Focus Mission").
  - **Success**: Port 80/443 is blocked/unblocked based on mission state changes.
- [ ] **Checkpoint 2.2: Read-Only System Root**
  - Transition the primary OS partitioning to a immutable/read-only root (using `overlayfs` or `systemd-sysext`).
  - **Success**: `touch /usr/bin/test` fails by default; modifications require a "System Mission."
- [ ] **Checkpoint 2.3: Rootless Service Orchestration**
  - Migrate all Lumina background services (observer, bus, indexer) to run as unprivileged users.
  - **Success**: `ps aux` shows zero `lumina-*` processes running as root.

---

## 🟠 Mission 3: Atomic Multi-Layer Rollbacks

*Goal: Ensure "Arch Anxiety" is solved through filesystem-level snapshots.*

- [ ] **Checkpoint 3.1: Btrfs/ZFS Snapshot Hooks**
  - Integrate `lumina sync` with a pre-link snapshot command.
  - **Success**: A snapshot named `pre-sync-v1.x` is created before any symlink changes.
- [ ] **Checkpoint 3.2: The "Emergency Recovery" TTY**
  - A fallback shell script or binary that can restore a snapshot from the GRUB/Systemd-boot menu.
  - **Success**: Booting into "Lumina Restore" successfully reverts the system to the last known-good registry state.
