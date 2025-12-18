# Contributing to Lumina OS

Thank you for your interest in contributing to Lumina OS! We are building a "Core-First" operating system for the modular professional, and we value contributions that align with our pillars of **Stability, Polish, and Ownership.**

## Our Mission

Before contributing, please read the [MANIFESTO.md](file:///home/johncarlojose/Projects/luminaOS/MANIFESTO.md). Every line of code should move us closer to a "Zero-Drag" workstation experience.

## The Lumina-Flow Workflow

We follow a strict branching model:

1. **`main`**: Production stable. No direct pushes.
2. **`develop`**: The integration branch for current milestones.
3. **`feature/*`**: Individual features or bug fixes.
4. **`docs/*`**: Documentation improvements.

### Submission Process

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/amazing-feature`).
3. Commit your changes (`git commit -m 'feat: add some amazing feature'`).
4. Push to the branch (`git push origin feature/amazing-feature`).
5. Open a Pull Request against the **`develop`** branch.

## Standards

- **Rust**: Follow `clippy` and `rustfmt` defaults.
- **Commit Messages**: Use [Conventional Commits](https://www.conventionalcommits.org/).
- **Documentation**: All new features must be documented in a corresponding `.md` file in the core library.

## Questions?

Open an issue with the `question` label or join our community discussions.
