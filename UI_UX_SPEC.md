# Lumina OS: UI/UX Specification

## Design Language: Material You (M3) & ChromeOS Hybrid

This document defines the visual and interactive standards for the Lumina OS project.

---

## 1. The Kinetic Color System (Material You)

The core of the experience is that the OS "feels" the wallpaper.

### Dynamic Generation

- **Primary Source**: The dominant color of the current wallpaper.
- **Tonal Palettes**: Generation of 5 specific tones (Primary, Secondary, Tertiary, Neutral, Neutral Variant).
- **Application**:
  - **Waybar**: Background uses `Neutral 90%` with `Primary` accents.
  - **Hyprland Borders**: Active window uses `Primary 80%`.
  - **Terminal**: Colors 0-15 are re-mapped to the generated tonal palette.

---

## 2. Layout & Shell Architecture

### The "Shelf" (ChromeOS Style)

- **Position**: Fixed at the bottom.
- **Auto-Hide**: Smart hide when windows overlap.
- **Center-Focus**: App icons are centered (Pill-shaped containers).
- **The "Quick Settings" Cluster**: A consolidated module on the bottom-right for Wifi, Bluetooth, Battery, and Night Light.

### Window Management

- **Rounding**: 16px (Material 3 standard for large containers).
- **Gaps**: 8px inner, 12px outer (Balanced for focus).
- **Animations**:
  - **Bezier Curve**: `cubic-bezier(0.05, 0.9, 0.1, 1.05)` (Provides the "bouncy" Google feel).
  - **Workspace Transition**: Horizontal slide with a subtle scale-down effect.

---

## 3. Typography & Polish

### Font Selection

- **System Interface**: `Google Sans` or `Inter`.
- **Monospace**: `JetBrains Mono` or `Roboto Mono`.

### Visual Effects

- **Blur**: 20px Gaussian blur on all system sidebars.
- **Shadows**: Soft, multi-layered shadows for active windows (`0 10px 30px rgba(0,0,0,0.1)`).

---

## 4. Projections: Interaction Design

- **Gestures**: 3-finger swipe up for Workspace Overview (mimicking Android's multitasker).
- **Lumina Assistant**: `Super + Space` opens a centralized, Material-styled search bar that serves as an App Launcher, Calculator, and **Agent Portal**.
- **AI Immersion**: The Assistant "ghosts" through the system—it monitors terminal errors, summarizes folder contents in the file manager, and provides "Code-Action" suggestions in real-time.

---

## 5. Reactive UI Logic (The "Living" Shell)

The Lumina Shell is a **State Receiver**. It does not poll.

- **Hardware-Reactive**: Swapping a Framework expansion card triggers a smooth transformation animation in the Shelf.
- **Cloud-Reactive**: A new file in Google Drive triggers a subtle "Pulse" in the file manager icon.
- **Theme-Reactive**: Changing the wallpaper triggers a system-wide "Color Wave" that propagates through all open windows using `matugen-kinetix`.

---

## 6. Ownership of Design (Shadcn Style)

In Lumina OS, the UI is **Open Source Distribution**:

- **Source Widgets**: Every Waybar module (Weather, Clock, Battery) is at `/home/user/.config/lumina/widgets/`.
- **Edit on the Fly**: To change the battery icon's animation, you edit the CSS/JS directly in your home directory. No "locked" system themes.
- **Rebase Philosophy**: You can "pull" new widget designs from the Lumina repo and merge them into your custom mods.
