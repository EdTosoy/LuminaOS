# Phase 2: Hyper-Granular Mission Log (Intelligence & Isolation)

This document provides absolute-clarity directives for AI agents executing Phase 2.

---

## 🟢 Mission 1: Mission-Aware Isolation (Podman)

*Goal: Rootless dev environments decoupled from the host OS.*

### [ ] Checkpoint 1.1: Podman Orchestration wrapper

- **Task**: Create a Rust abstraction for managing Podman containers.
- **Directives**:
  - Crates: `bollard` (if using Docker socket) or command-line wrappers for `podman` (safer for rootless).
  - Logic: Parse "Mission" blocks in `lumina.yaml` to define volume mounts and image tags.
- **Verification**: `lumina mission up <name>` launches a container that successfully mounts the local project directory.

### [ ] Checkpoint 1.2: Shell Environment Injection

- **Task**: Implement a shell hook (`zsh`/`bash`) that detects when the user is inside a "Mission" directory.
- **Directives**:
  - Logic: `lumina status --check-dir` called via `precmd` or `chpwd`.
  - Effect: Automatically alias commands like `cargo` to `podman exec -it <mission> cargo`.
- **Verification**: `cd ~/Projects/my-app` and verify `which cargo` points to the containerized version.

---

## 🟡 Mission 2: The Gemini Observer (HUD)

*Goal: The non-agentic read-only system intelligence layer.*

### [ ] Checkpoint 2.1: HUD Shell (EWW/Gtk)

- **Task**: Implement the visual sidebar in Hyprland.
- **Directives**:
  - Crates/Tools: `eww` (Elkowar's Wacky Widgets) or a custom Gtk4-RS app.
  - Requirement: Must be positioned as a Layer-Shell (Overlay) that does not steal focus by default.
- **Verification**: Super+G toggles the bar. `top` shows minimal CPU usage (< 1%).

### [ ] Checkpoint 2.2: Contextual Log Summarizer

- **Task**: Logic to pipe system events to Gemini API.
- **Directives**:
  - Logic: Listen to `journalctl -f` and parse for "Error" tags.
  - Prompt: "Summarize this system error into a 10-word actionable tip for a developer."
- **Architectural Guardrail**:
  - Do NOT send personal data; sanitize logs for usernames/IPs before sending to the cloud.
- **Verification**: Trigger a fake system error and see the HUD update with a summary.

---

## 🟠 Mission 3: Contextual Flow (Event Bus)

*Goal: Real-time system reactivity.*

### [ ] Checkpoint 3.1: D-Bus Event Publisher

- **Task**: Implement a D-Bus service for Lumina events.
- **Directives**:
  - Crates: `zbus`.
  - Common Events: `ModuleChanged`, `ThemeUpdated`, `FocusMissionStarted`.
- **Verification**: Use `dbus-monitor` to see Lumina events firing in real-time.

### [ ] Checkpoint 3.2: Kinetix Palette Swapping

- **Task**: Connect the Event Bus to the Matugen engine.
- **Directives**:
  - Logic: When a "Mission" starts, trigger `matugen` with the mission's custom color seed.
- **Verification**: System colors change automatically when switching directories in the terminal.

---

## 🟣 Mission 4: Pixel & Google Sync

*Goal: Identity-based ecosystem integration.*

### [ ] Checkpoint 4.1: Phone Bridge (KDEConnect-RS)

- **Task**: Integration with phone notification streams.
- **Directives**:
  - Sync Clipboard and Battery Status into the HUD.
- **Verification**: Phone battery level is visible in the Lumina Waybar/HUD.

### [ ] Checkpoint 4.2: Workspace Drive Mount

- **Task**: Mount Google Drive as a local folder.
- **Directives**:
  - Tool: `rclone` or a custom OIDC implementation in Rust.
- **Verification**: `ls ~/Drive` shows your Google Workspace files.
