# Phase 5: Hyper-Granular Mission Log (Ecosystem & Autonomy)

---

## 🟢 Mission 1: The "Magic" ISO (Installer)

*Goal: Zero-touch installation for Framework hardware.*

### [ ] Checkpoint 1.1: Automated Archer (Archiso)

- **Task**: Build a custom Arch Linux ISO.
- **Directives**:
  - Include the `lumina` binary in the `/usr/bin/` of the live image.
- **Verification**: ISO boots into a Lumina-branded wallpaper with a "Setup" terminal.

### [ ] Checkpoint 1.2: Identity-First Wizard

- **Task**: Setup wizard that pulls the Git registry before Disk partitioning.
- **Directives**:
  - Requirement: If the user provides a Git URL, pull the `lumina.yaml` and use its `metadata` to define the install (e.g., disk layout, hostname).
- **Verification**: User enters Git URL, and the machine completes the install without further prompts.

---

## 🟡 Mission 2: Full Agentic Autonomy

*Goal: Proactive assistance.*

### [ ] Checkpoint 2.1: Action Proposal Bus

- **Task**: AI logic that asks for permission to execute system changes.
- **Directives**:
  - UI: A "Toast" notification with "Approve" and "Deny" buttons.
- **Verification**: HUD suggests a Mission switch based on time of day, and clicking "Approve" executes the switch.

### [ ] Checkpoint 2.2: Self-Healing Logic

- **Task**: Automated diagnosis of a "Broken" state.
- **Directives**:
  - Logic: If a symlink points to nothing, attempt a `git pull` on the registry to re-acquire the source.
- **Verification**: Intentionally delete a config file and see the system repair it automatically.
