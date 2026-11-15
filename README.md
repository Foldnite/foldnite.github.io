# Foldnite

**Foldnite is an independent STEM-focused project for interactive 3D worlds, collaborative science-inspired missions, and game-based problem solving.**

The project explores how science and engineering topics can become tangible experiences: players navigate virtual environments, interact with equipment and systems, collaborate on challenges, and learn by testing ideas.

## What STEM means in Foldnite

**STEM** stands for **Science, Technology, Engineering, and Mathematics**. Foldnite uses this as a practical design framework—not just a label:

- **Science:** biology, chemistry, molecular structures, materials, climate, energy, and environmental systems.
- **Technology:** interactive 3D environments, simulation, AI-assisted tools, and runtime integrations where available.
- **Engineering:** virtual equipment, systems thinking, robotics, infrastructure, and troubleshooting missions.
- **Mathematics:** geometry, measurement, patterns, optimisation, data interpretation, and quantitative reasoning.

The experience draws inspiration from collaborative scientific puzzle-solving and creator-driven game worlds. Inspiration does not imply ownership, endorsement, or an official relationship with Foldit, Fortnite, Epic Games, or any other third party.

## Product principles

- **Mission-based learning:** give players an objective, an environment, tools, constraints, and a way to inspect outcomes.
- **Collaboration:** support shared exploration and problem-solving rather than relying only on individual scores.
- **Scientific honesty:** distinguish a game result or visual effect from a validated scientific result.
- **Engine-aware design:** keep scientific concepts and mission definitions as portable as practical, while respecting each runtime's technical and licensing limits.
- **Rights-aware production:** track provenance and licences for code, documentation, datasets, models, fonts, audio, and visual assets.

## Project map

| Repository / resource | Purpose |
|---|---|
| [Arctic / MAS “Snezhinka” documentation](./arctic/README.md) | Scientific-world concept, environment, mission domains, and architecture assumptions |
| [Arctic showcase](https://foldnite.github.io/arctic/) | Browser-accessible project showcase |
| [UNIGINE repository](https://github.com/Foldnite/UNIGINE) | High-fidelity simulation and standalone-runtime workstream |
| [UEFN repository](https://github.com/Foldnite/UEFN) | Fortnite / Unreal Editor for Fortnite workstream |
| [Unity repository](https://github.com/Foldnite/UNITY) | Unity runtime and integration workstream |
| [Foldnite organisation](https://github.com/Foldnite) | Repositories and public project updates |

## Runtime and scientific-service boundaries

UNIGINE is identified in the Arctic planning documentation as the current production baseline for that concept. UEFN/Fortnite publishing, Unity integrations, standalone builds, Web delivery, and cloud-rendered sessions are distinct deployment paths; capabilities or releases in one path must not be assumed to exist in another.

AI, Scientific MCP, cloud rendering, and quantum-computing integrations are optional or staged capabilities. Quantum execution is relevant only to selected suitable tasks and is not a requirement for running the game. External scientific jobs should be handled through appropriate server-side adapters, authorization, and validation—not by exposing credentials in a game client. Never claim quantum advantage or scientific validity without task-specific evidence.

## Current state and evidence

The `arctic/` directory contains planning and architecture material. Numbers and feature sets described there are planning assumptions unless a document explicitly identifies them as measured or implemented. A repository landing page or design document is not, by itself, evidence that a feature has shipped, that a service is deployed, or that funding has been approved.

## Intellectual property and licensing

Foldnite-owned code, documentation, original designs, and other proprietary materials are covered by the repository's **Restricted Proprietary License**, unless a file or component is explicitly governed by another written licence. Public visibility on GitHub is not permission to reproduce, republish, fork for external use, redistribute, sell, or commercially exploit protected materials.

Third-party software, SDKs, trademarks, characters, datasets, media, and assets remain subject to their own rights and terms. The Foldnite licence does not override upstream open-source or third-party licences.

**Historical licence note:** earlier versions of this repository were distributed with GNU AGPLv3. The current licensing notice is prospective and does not purport to revoke rights validly granted to earlier recipients under the AGPLv3 or another prior written agreement. Any rights arising from those earlier grants remain subject to their applicable terms.

## Language

- English: this file
- [Русская версия](./README.ru.md)

**Explore science. Build ideas. Solve missions together.**
