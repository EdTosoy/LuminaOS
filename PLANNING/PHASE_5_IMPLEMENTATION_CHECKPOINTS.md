# Phase 5: Implementation Checkpoints (Ecosystem & Autonomy)

This document provides granular directives for Phase 5: **The "Magic" ISO & Autonomy**.

---

## 🟢 Mission 1: The "Magic" ISO (Life-Cycle Installer)

*Goal: A zero-touch, hardware-aware installer that delivers Lumina OS in < 5 minutes.*

- [ ] **Checkpoint 1.1: Custom ISO Scaffold**
  - Use `archiso` to build a live environment with the Lumina CLI and Hyprland pre-baked.
  - **Success**: The ISO boots directly into a "Lumina Welcome" UI session.
- [ ] **Checkpoint 1.2: Calamares/Custom Welcome Flow**
  - Create a Material You themed installer that asks for **Google Credentials** and **Identity Profile** first.
  - **Success**: User completes the wizard and enters a functional desktop without terminal input.
- [ ] **Checkpoint 1.3: Post-Install "Magic" Sync**
  - Installer automatically clones the user's registry from Git and runs `lumina sync` as the final step.
  - **Success**: The first login looks identical to the user's previous machine.

---

## 🟡 Mission 2: Full Agentic Autonomy (Observer -> Assistant)

*Goal: Transitioning from read-only HUD to a proactive system collaborator.*

- [ ] **Checkpoint 2.1: Proactive Action Bus**
  - Implement a "Safe Execution" layer where Gemini can suggest and (with approval) run `lumina` commands.
  - **Success**: Agent suggests: "I noticed your theme is out of sync with your Google Calendar event 'Night Shift'. Shall I update the palette?"
- [ ] **Checkpoint 2.2: Automated Mission Generation**
  - AI logic to suggest new Mission profiles based on the user's local projects.
  - **Success**: Agent detects a Python project and asks to create a `python-mission` container image.
- [ ] **Checkpoint 2.3: Global Workflow Optimization**
  - Proactive notification cleaning and window tiling adjustments based on gaze/activity patterns.
  - **Success**: Non-relevant windows are minimized/moved to secondary workspaces during high-intensity CPU missions.

---

## 🟠 Mission 3: The "Closed Loop" Support

*Goal: System-aware bug reporting and self-healing.*

- [ ] **Checkpoint 3.1: Snapshot-Aware Bug Reports**
  - Automatically attach the current `lumina.yaml` and latest Btrfs snapshot ID to GitHub issue reports.
  - **Success**: Bug reports include everything needed to reproduce the user's exact system state.
- [ ] **Checkpoint 3.2: Self-Healing Binary**
  - Logic to detect broken symlinks or missing dependencies and offer a "Lumina Repair" mission.
  - **Success**: User clicks "Repair" and the system re-runs local validation/fix logic.
