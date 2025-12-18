# Lumina OS: Project Roadmap (2025-2026)

## Milestones & Feature Projections

---

## 🟢 Phase 1: The "Shadow" & Core Stability (Q1 2025)

*Focus: Foundation, State Management, and Modular UI.*

- [x] **Material You Engine**: Integration of `matugen` into Hyprland and Waybar.
- [ ] **Lumina CLI (v0.1)**: Core Rust tool for **Stateless Profile** syncing (The "Director").
- [ ] **Shadow-Linker (MVP)**: Implementing the `~/.lumina` unified root with safe symlinking.
- [ ] **Lumina-Shelf**: Essential Waybar configuration (Pill-shaped modules).
- [ ] **Environment Snapshotting**: Basic Btrfs/ZFS hook for `lumina update`.

---

## 🔵 Phase 2: Contextual Intelligence (Q2-Q3 2025)

*Focus: Seamless orchestration and proactive observation.*

- [ ] **Contextual Flow**: Automatic environment and notification switching based on project directory.
- [ ] **Containerized Missions (Docker)**: Using Podman/Docker to isolate project environments (The "Clean Room").
- [ ] **PixelHub Widget**: System tray applet for Pixel status and hot-toggles.
- [ ] **Lumina Assistant (Observer)**: A sidebar for summarized system logs and metadata (Non-agentic).

---

## 🟣 Phase 3: The Agentic Shell (Q4 2025+)

*Focus: Proactive automation and global integration.*

- [ ] **Lumina Search**: Global index of local files and Google Workspace data.
- [ ] **Framework Module Dashboard**: Hardware-aware UI for expansion card management.

---

## 🚀 Future Horizon (Stretch Goals)

*These features are deferred to ensure the stability of the core OS foundations.*

- **Proactive Agent Assistant**: Autonomous system actions and proactive code fixes.
- **Life-Cycle Installer**: The agent-led "Magic" ISO for zero-touch hardware setup.
- **Lumina SDK (Bazaar)**: The community widget market and decentralized registry.
- **Longevity Engine (v1.0)**: Deep silicon-native kernel optimizations.

---

## 🏗️ Repository & Governance: "Lumina-Flow"

To maintain production-grade quality, the project follows a tiered branching model:

- **`main`**: The Stable Core. Reflects the current production-ready strategic state.
- **`develop`**: The Integration Hub. All Phase 1 implementation (CLI Core) occurs here.
- **`feature/*`**: Atomic missions. Merged into `develop` via Pull Request only.
- **`docs/*`**: Significant strategic shifts or technical specification updates.

### Community & Contribution

We welcome contributions that respect our pillars. See [CONTRIBUTING.md](CONTRIBUTING.md) for details on how to join the mission.
