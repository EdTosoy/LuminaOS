# Risk Management & Mitigation Register

This document identifies the critical risks to the Lumina OS project and explains how we neutralize them.

| Risk Category | Risk Description | Impact | Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| **Technical** | **Complex Symlink Drift**: The `lumina.yaml` registry fails to track 100% of state. | High | **OCI Isolation**: Move project-level deps into Docker/Podman to ensure the host remains clean. |
| **Technical** | **Hardware Entropy**: Driver issues on non-Framework hardware. | Medium | **Framework-First**: Declare Framework as the primary Tier-1 target to ensure "Perfect" optimization. |
| **Operational** | **Maintenance Burnout**: Managing custom repos (Lumina-Stable) is labor-intensive. | Medium | **Agentic Automation**: Utilize CI/CD scripts to auto-test upstream breaks and flag them. |
| **Market** | **"The NixOS Problem"**: The technical barrier is too high for power users. | High | **Native Bootstrap**: Provide a "One-Click" setup that doesn't require learning a new language like Nix. |
| **Social** | **Lack of Ecosystem**: No community widgets or themes being built. | High | **Bazaar Model**: Adopt the Shadcn "Source Distribution" model—making it trivial to copy and edit code. |

---

## Technical Debt Tracker

1. **Phase 1 Debt**: We are bypassing a custom ISO for a Native Bootstrap. This adds a dependency on a "Vanilla Arch" install first.
2. **Phase 2 Debt**: The HUD Observer will start as a sidebar widget, not a full-screen agent, to minimize initial UI complexity.
