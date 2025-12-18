# Lumina OS: Technical Solutions for the Open Professional

This document details the technical implementation of our two most ambitious "Friction-Free" pillars: **Lumina-Stateless** and **Mission-Aware Workspaces**.

---

## 1. Solving "Dotfile Debt" with Lumina-Stateless

**The Goal**: A single Git-mappable OS profile that ensures your machine is reproducible in minutes, not days.

### Technical Architecture (Stateless)

1. **The Unified Root (`~/.lumina`)**:
    * Instead of scattered dotfiles, all Lumina OS configurations (Hyprland, Waybar, Matugen, Zsh, AI Hooks) live inside a single, version-controlled directory: `~/.lumina`.
    * Lumina OS uses a **Shadow-Linker** (Rust binary) that symlinks these files to their traditional locations (e.g., `~/.config/hypr`) but monitors them for changes.

2. **State Declaration (`lumina.yaml`)**:
    * A declarative file where you define:
        * **Packages**: List of essential packages (`pacman` + `aur`).
        * **Secrets**: Pointers to your encrypted secret store (for API keys).
        * **Aliases**: Global shell shortcuts.

3. **One-Command Recovery**:
    * On a fresh Arch install, running `lumina sync <repo-url>` clones your profile, installs your packages, and applies your "Material You" theme instantly.

---

## 2. Solving "Environment Drift" with Mission-Aware Workspaces

**The Goal**: Eliminating the gap between your workstation state and your active project.

### Technical Architecture (Mission-Aware)

1. **The "Mission" Concept**:
    * A "Mission" is a workspace tied to a specific project directory (e.g., `~/Projects/nebula`).
    * Lumina OS uses an OS-level file watcher (using `inotify` via Rust) that detects when you enter a "Mission" directory in the terminal or file manager.

2. **Proactive State Switching**:
    * When you enter a Mission, the OS automatically executes:
        * **Shell Context**: Loads specific environment variables and aliases (direnv-style, but integrated into the shell prompt).
        * **UI Context**: Adjusts Waybar modules to show project-specific data (e.g., GitHub PR status, local server logs).
        * **Layout Context**: Autonomously tiles your windows according to that specific Mission's requirements (e.g., VS Code on the left, Terminal on the right).

3. **Lumina Assistant Integration**:
    * The Assistant is "Mission-Aware." If you ask, "What was I working on?" it summarizes the specific git diffs and open issues for the *current Mission*, not your entire system.

---

## Technical Moat: The `lumina` Rust Binary

Both of these solutions are powered by a single, blazingly fast Rust binary (`lumina`) that replaces dozens of fragile bash scripts.

| Solution | Tooling Foundation | Lumina Enhancement |
| :--- | :--- | :--- |
| **Dotfile Debt** | Git + Symlinking | **Declarative State + Automatic Sync**. |
| **Environment Drift** | direnv + Nix | **Mission-Aware UI & Layout Orchestration**. |

---

**Does this "Stateless" and "Mission-Aware" approach sound like the level of technical depth you want for the Lumina OS core?**
