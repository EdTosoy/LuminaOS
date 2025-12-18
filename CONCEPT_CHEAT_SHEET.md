# Lumina OS: Conceptual Cheat-Sheet

## Clear the Fog, Build the Future

This is the non-marketing, no-hype breakdown of exactly what we are building and why.

---

### 1. What is the Core Product?

Lumina OS is a **Professional Workstation Layer** that sits on top of Arch Linux.

- **The Engine**: Arch Linux + Rust binaries.
- **The Look**: Material You + Hyprland (Google Pixel aesthetics).
- **The Brain**: One binary (`lumina`) that manages your system state.

---

### 2. How does "Stateless" work?

Think of it like **iCloud for your terminal**, but you own the data.

- Everything important (`.config`, fonts, packages) is listed in **`lumina.yaml`**.
- The `lumina` tool ensures your machine matches that file.
- **If your machine dies**: You run `lumina sync` on a new computer. 2 minutes later, your entire desktop is *identical* to your old one.

---

### 3. What is "Contextual Flow"?

It’s **Automatic Workspace Setup**.

- When you open a project folder, the OS "senses" it.
- It automatically silences Slack, opens your browser to the project URL, and tiles your editor.
- **No manual modes**: It just happens when you start working.

---

### 4. Why the "Framework Laptop"?

We are building for a specific high-end hardware target to ensure **Conceptual Integrity**.

- We don't try to be "Linux for Everyone."
- We are **"Lumina for the Modular Professional."**
- This lets us optimize the battery, fonts, and icons for one specific screen and CPU perfectly.

---

### 5. Why build it in Rust?

Stable, fast, and safe.

- We replace dozens of fragile pieces of code with one **Rock-Solid Core**.
- This core is compiled specifically for your CPU (**Silicon-Native**), making it faster than macOS or Windows on the same hardware.

---

### 6. Is it stable? (The "Arch Anxiety" Cure)

Yes. We use **Lumina-Stable** curated repos that lag behind Arch upstream by 2 days. This ensures that if an update breaks a desktop component, we catch it before it hits your machine. Plus, we take an automatic "System Snapshot" before every update.

---

### 7. How fast is the setup?

The **Life-Cycle Installer** detects your Framework hardware and sets everything up in 5 minutes. You log in to Google, and your workstation is ready to go.

---

### 8. The "Core-First" Vow

We build the **Stable Base** (The Registry and Shell) before we build the **Flashy AI**.

- If the AI breaks, your computer still works.
- If the Theme breaks, your files are still safe.
- **Stability is the first feature.**

---

**Does this breakdown make you feel like you are back in control of the vision?**
