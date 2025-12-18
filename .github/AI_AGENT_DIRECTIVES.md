# AI Agent Operation Manual: "The Lumina Framework"

This document is the **Mandatory System Instruction** for any AI agent interacting with the Lumina OS codebase. To ensure "Zero Vagueness," follow these hard-coded protocols.

---

## 1. The "Zero-Vagueness" Protocol

Before making any edit, the agent MUST:

1. **Reference the Mission Log**: Identify the current `PHASE_X_IMPLEMENTATION_CHECKPOINT.md` and the specific Checkpoint being addressed.
2. **State the Goal**: Explicitly state which "Success Condition" is being worked toward.
3. **Audit the Core 15**: Ensure the proposed change does not contradict the `MANIFESTO.md`, `STRATEGY.md`, or `SECURITY_ARCHITECTURE_ADR.md`.

---

## 2. Technical Commandments

- **Architecture**: Always use the **Stateless Shadow-Linker** pattern. Never write directly to system paths (e.g., `/etc`, `~/.config`) from a binary. Always stage in `~/.lumina/staging`.
- **Language**: Use **Safe Rust**. Avoid `unsafe` blocks unless absolutely required for FFI (Foreign Function Interface) and documented in an ADR.
- **Dependencies**: Prioritize crates mentioned in the Mission Logs (e.g., `clap`, `serde`, `camino`, `bollard`). Proposing new crates requires an "Impact Rationale."
- **Multi-Arch**: Every piece of code MUST be compatible with `aarch64` (ARM). Avoid CPU-specific intrinsics without fallbacks.

---

## 3. Communication Standards

- **Tone**: Professional, engineering-led, and precise. Avoid fluff.
- **Reporting**: When a checkpoint is complete, update the `[ ]` to `[x]` in the Mission Log and provide the "Verification Proof" (e.g., terminal output or test results).
- **Veto Logic**: If an instruction from a human feels like it introduces "Technical Debt" or contradicts a "Core Pillar," the agent MUST raise a "Strategic Warning" before proceeding.

---

## 4. Execution Workflow (The 4-Step Loop)

1. **Research**: Use `grep` and `find` to map all dependencies of the task.
2. **Plan**: Write an `implementation_plan.md` (or update the one provided by the human).
3. **Execute**: Apply code changes in atomic chunks.
4. **Verify**: Run the "Success Verification" commands defined in the Mission Log.

---

## 5. Folder Hierarchy standards

- `/lumina`: CLI frontend (Command parsing, Logging).
- `/lumina-core`: Core logic (Filesystem, Registry, Hardware detection).
- `/PLANNING`: All Strategic Library docs and Mission Logs.
- `/config`: Pre-baked Hyprland/Waybar modules for the "Staging" demo.

---

## 6. Technical Standards (The "Prescriptive" Layer)
- **Error Handling**: Use `anyhow::Result` for CLI-level errors. Provide "Contextual Narratives" (e.g., `.with_context(|| "Failed to parse registry at path...")`).
- **Path Handling**: ALWAYS use `camino::Utf8PathBuf` instead of standard `PathBuf` to ensure UTF-8 safety and avoid panics.
- **Serialization**: Use `serde` with `rename_all = "camelCase"` or `snake_case` explicitly defined in the struct to prevent registry drift.
- **Logging**: Use the `tracing` crate. All hardware-aware logic must include `trace!` and `debug!` spans for remote auditing.
- **Testing**: Every new logic function in `lumina-core` must have a corresponding test in the `tests/` directory or a doc-test.
