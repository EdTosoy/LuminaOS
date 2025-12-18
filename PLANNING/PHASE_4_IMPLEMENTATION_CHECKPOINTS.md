# Phase 4: Hyper-Granular Mission Log (Hardening & Longevity)

---

## 🟢 Mission 1: The BORE Kernel & Thermal Logic

*Goal: System responsiveness through scheduler optimization.*

### [ ] Checkpoint 1.1: Lumina-BORE build

- **Task**: Compile the BORE (Burst-Oriented Response Encoder) kernel.
- **Directives**:
  - Use `makepkg` with specific Framework optimization flags (e.g., `march=x86-64-v3`).
- **Verification**: `uname -a` shows "lumina-bore" kernel.

### [ ] Checkpoint 1.2: Dynamic Thermal Profiles

- **Task**: Logic to switch CPU scaling based on Mission importance.
- **Directives**:
  - Logic: Write to `/sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference`.
- **Verification**: HUD shows "Power Mode: Efficiency" during writing tasks and "Performance" during builds.

---

## 🟡 Mission 2: Immutable System Hardening

*Goal: A "Read-Only" core to prevent system drift.*

### [ ] Checkpoint 2.1: Read-Only System Root

- **Task**: Set the root partition as read-only and mount `/etc` and `/var` as writable overlays.
- **Directives**:
  - Tools: `mkinitcpio` hooks for overlayfs.
- **Verification**: `touch /usr/bin/locked` results in a Read-Only Filesystem error.

### [ ] Checkpoint 2.2: Atomic Rollbacks (Btrfs)

- **Task**: Hook into `lumina sync` to create pre-sync snapshots.
- **Directives**:
  - Command: `btrfs subvolume snapshot`.
- **Verification**: A failed sync allows for a 5-second rollback to the previous state.
