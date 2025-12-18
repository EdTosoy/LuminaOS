# Phase 3: Hyper-Granular Mission Log (Agentic Shell)

This document provides absolute-clarity directives for AI agents executing Phase 3.

---

## 🟢 Mission 1: Global Semantic Search

*Goal: Intelligent indexing of local and cloud files.*

### [ ] Checkpoint 1.1: Local Metadata Indexer

- **Task**: A background service that indexes files via `inotify`.
- **Directives**:
  - Crates: `notify-rust` (for monitoring) and `tantivy` (The full-text search engine).
- **Verification**: `lumina search` finds a file created 1 second ago.

### [ ] Checkpoint 1.2: LLM Query Mapping (Gemini)

- **Task**: Convert natural language queries into search filters.
- **Directives**:
  - Prompt: "Map 'files from yesterday' to a search query: `modified:>2025-12-16`."
- **Verification**: NL search for "that rust file" returns the correct path.

---

## 🟡 Mission 2: Framework Module Dashboard

*Goal: Hardware-Aware UI integration.*

### [ ] Checkpoint 2.1: Sysfs Module Discovery

- **Task**: Detect Framework expansion cards.
- **Directives**:
  - Logic: Scan `/sys/bus/usb/devices` to identify specific Framework IDs for DisplayPort, HDMI, and Storage modules.
- **Verification**: Dashboard UI shows a visual map of the 4/6 expansion slots.

### [ ] Checkpoint 2.2: Hot-Swap Safety logic

- **Task**: Prevent data loss on storage expansion removal.
- **Directives**:
  - Logic: Hook into `udev` events. If a storage module is pulled, check for active mounts and alert.
- **Verification**: Pull a dummy USB and verify the Lumina notification fires.

---

## 🟠 Mission 3: The Bazaar (Marketplace)

*Goal: Decentralized community ecosystem.*

### [ ] Checkpoint 3.1: Bazaar Pull/Push API

- **Task**: Subcommand `lumina bazaar install <widget>`.
- **Directives**:
  - Logic: Clone Git repos into `~/.lumina/bazaar/` and symlink into active UI paths.
- **Verification**: Install a community widget and see it appear in the HUD instantly.

### [ ] Checkpoint 3.2: Developer SDK (CLI Scaffold)

- **Task**: A tool to help people build for Lumina OS.
- **Directives**:
  - Command: `lumina init-widget`.
- **Verification**: Generated widget project compiles and runs out of the box.
