# Phase 2: Implementation Checkpoints (Intelligence & Isolation)

This document provides granular directives for Phase 2: **The "Observer" Hub**.

---

## 🟢 Mission 1: Mission-Aware Isolation (Podman)

*Goal: Decouple project development from the host OS using rootless containers.*

- [ ] **Checkpoint 1.1: Mission Container Engine**
  - Implement a Rust wrapper for Podman/Docker commands.
  - Define "Mission Profiles" in `lumina.yaml` (Base image, volume mounts, env vars).
  - **Success**: `lumina mission start <name>` launches a rootless container with project files mounted.
- [ ] **Checkpoint 1.2: Terminal Hooking**
  - Automatically inject container shell into active terminal sessions when entering a project directory.
  - **Success**: Entering `~/Projects/nebula` changes the shell prompt to indicate the "Mission" environment.
- [ ] **Checkpoint 1.3: Toolchain Virtualization**
  - Ensure common tools (Cargo, NPM, Pip) run inside the container but map output to host project dir.
  - **Success**: `cargo build` inside a mission produces a `target/` folder visible on the host.

---

## 🟡 Mission 2: The Gemini Observer (HUD)

*Goal: A non-agentic, read-only intelligence layer for system-awareness.*

- [ ] **Checkpoint 2.1: HUD Overlay (Hyprland)**
  - Create a lightweight sidebar/overlay using EWW or Gtk4.
  - Implement a toggle keybind (Super+G) to show/hide the Observer.
  - **Success**: Sidebar appears/disappears smoothly without layout shift.
- [ ] **Checkpoint 2.2: State Polling & Summarization**
  - CLI logic to pipe system logs (journalctl) and compiler errors to Gemini Flash API.
  - Summarize the "Current Problem" into a single, actionable sentence in the HUD.
  - **Success**: HUD displays "MISSION ERROR: Rust build failed due to missing 'tokio' dependency."
- [ ] **Checkpoint 2.3: Contextual Info-Cards**
  - Detect current active window and surface relevant docs or mission metadata.
  - **Success**: While in VSCode, HUD shows a link to our `DX_SPEC.md` or a "Mission Dashboard."

---

## 🟠 Mission 3: Contextual Flow (Event Bus)

*Goal: The system reacts to your mission state in real-time.*

- [ ] **Checkpoint 3.1: Reactive Event Bus**
  - Implement a lightweight D-Bus or Socket-based bus for system events (Project change, Battery low, Phone sync).
  - **Success**: CLI publishes "PROJECT_CHANGED" event when the user `cd`s into a mission dir.
- [ ] **Checkpoint 3.2: Theme Kinetix**
  - Automatically update Waybar colors and Wallpaper when a Mission starts (e.g., Green for Code, Red for Security Audit).
  - **Success**: System palette shifts instantly when a mission is activated.
- [ ] **Checkpoint 3.3: Notification Shadowing**
  - Suppress non-priority notifications while a "Deep Work" mission is active.
  - **Success**: System enters "Do Not Disturb" automatically upon mission start.
