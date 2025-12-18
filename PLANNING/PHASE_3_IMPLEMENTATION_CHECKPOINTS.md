# Phase 3: Implementation Checkpoints (Agentic Shell)

This document provides granular directives for Phase 3: **The "Agentic" OS**.

---

## 🟢 Mission 1: Global Semantic Search

*Goal: A single, intelligent index for local files and Google Cloud assets.*

- [ ] **Checkpoint 1.1: Local File Indexer**
  - Implement a background crawler (using `notify` for real-time updates) that indexes file names and metadata.
  - **Success**: `lumina search <query>` returns local file paths in < 50ms.
- [ ] **Checkpoint 1.2: Google Cloud Pillars**
  - Authenticate with Google Drive/Workspace APIs.
  - Index document titles and "Last Modified" headers.
  - **Success**: HUD search returns both local project files and corresponding Google Docs.
- [ ] **Checkpoint 1.3: Natural Language Querying**
  - Use a small local LLM or Gemini API to map NL queries to file paths/commands.
  - **Success**: "Find that Rust project I worked on yesterday" returns the correct directory.

---

## 🟡 Mission 2: Framework Module Dashboard

*Goal: Deep hardware integration with modular expansion cards.*

- [ ] **Checkpoint 2.1: Sysfs Module Mapping**
  - Map Framework expansion cards (USB-A, HDMI, Storage) to UI icons.
  - Monitor power draw and health per module.
  - **Success**: Dashboard displays: "Slot 1: HDMI (Active), Slot 3: 250GB Expansion (Healthy)."
- [ ] **Checkpoint 2.2: Hot-Swap Safety Shell**
  - Visual warning when a storage module is removed without unmounting.
  - **Success**: System triggers a notification and safely attempts unmount before hardware release.
- [ ] **Checkpoint 2.3: Thermal/Fan Curves**
  - Interactive sliders to override fan curves for Framework-specific thermal profiles.
  - **Success**: User can toggle "Silent Mode" or "Performance Mode" from the main HUD.

---

## 🟠 Mission 3: The "Bazaar" (Community Marketplace)

*Goal: Decentralized registry for Shadcn-style widgets and automation.*

- [ ] **Checkpoint 3.1: Registry API**
  - Implement the `lumina add <widget>` logic to download source code from GitHub/GitLab.
  - **Success**: Widget code is placed in `~/.lumina/widgets/` and instantly available for editing.
- [ ] **Checkpoint 3.2: Bazaar UI**
  - Reactive dashboard to "Browse" featured community themes and modules.
  - **Success**: User can see screenshots of community themes before installing.
- [ ] **Checkpoint 3.3: Developer SDK**
  - Standardized templates for building custom Lumina widgets.
  - **Success**: A developer can run `lumina widget-init` to scaffold a new UI module.
