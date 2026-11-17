# The HALO PS2 Project

**Bringing Halo to PlayStation 2 as a faithful port, retaining everything that makes it Halo.**

The HALO PS2 Project aims to deliver Halo as a faithful, contemporary PlayStation 2 port—as if it had launched alongside the original Xbox release.

## Screenshots

**These screenshots are from earlier development builds and do not represent the current state of the game. Updated screenshots will be published soon.**

### Pelican flyover

PCSX2 development capture, 12 November 2026.

![Pelicans during the opening flyover](https://github.com/user-attachments/assets/2b652625-9826-4836-b2c0-dd005b1a0f6f)

### A10 — The Pillar of Autumn

PCSX2 development capture, 14 November 2026.

![A10 interior with flashlight illumination](https://github.com/user-attachments/assets/6a185e58-1f5a-40c1-8b1d-aca54209531c)

### Per-pixel flashlight — A10

PCSX2 development capture, 16 November 2026. Flashlight off (left) and on (right), showing the terrain diffuse-lighting test. The performance target remains unmet.

![A10 flashlight off and on](https://github.com/user-attachments/assets/0179e8ed-ab01-484c-8351-690f5922f71b)

### Pelican landing

PCSX2 development capture, 12 November 2026.

![First-person view during the Pelican landing](https://github.com/user-attachments/assets/d5ea4b75-260e-44cf-b295-c4942b6a5aa2)

## Project goals

- **Faithful gameplay:** retain the combat, encounters and interactions that make Halo feel like Halo.
- **Uncompromised animation and physics:** preserve the original animation and physics behaviour.
- **Original geometry:** retain model and terrain geometry without reducing their detail to meet the platform.
- **Original audio:** preserve the game’s music, dialogue, ambience and sound effects.
- **Faithful visual effects:** represent all original graphics effects as accurately as possible within the PS2 rendering architecture.
- **The complete game from physical DVD:** run the game from beginning to end on a real PS2, streaming from a physical DVD without requiring an internal hard drive.

These are the project’s targets, not claims that every system is already complete.

## Technical development

Achieving these goals requires a custom engine and content pipeline built around PlayStation 2 hardware.

Current development includes:

- **PS2-focused rendering:** geometry processing and rendering work distributed across the Emotion Engine, Vector Units and Graphics Synthesizer.
- **GS Recipe System:** A PS2-native rendering framework that translates Halo's original Xbox shaders and material effects into optimised sequences of Graphics Synthesizer (GS) passes, known as *recipes*. Where direct recreation is impractical or too expensive, alternative PS2-native effects are designed to preserve the original visual appearance while respecting the console's hardware and performance limitations.
- **Content preparation:** offline processing of meshes, textures, materials, scenes and animation data for PS2 runtime use.
- **Visibility and memory management:** scene visibility, geometry culling and texture budgeting to use limited resources efficiently.

### Texture Fidelity and Optimisation

The objective is to **preserve Halo's original full-resolution textures wherever practical**, maximising fidelity to the original rendered frame rather than reducing texture quality uniformly to fit the PS2.

Each texture is assessed individually during content preparation to determine the most appropriate conversion and storage format. Decisions consider colour depth, palette or compression options, measured reconstruction error using **root mean square error (RMSE)**, and whether a reduction in resolution is actually necessary.

Texture choices also account for their visual importance, how they appear in-game, and their impact on limited GS texture memory and streaming bandwidth. Where a lower-cost representation produces an acceptable visual result, it can free resources for textures that benefit more from retaining their original detail.

The guiding principle is **measured, per-texture optimisation instead of blanket downscaling**, with the aim of reproducing the original Xbox image as faithfully as PS2 hardware permits.

## Project status

**Active development — native PS2 rendering and early Halo gameplay integration are working, but the campaign is not yet playable end to end.** The following separates demonstrated functionality from work still in progress.

### Working foundations

- **Native PS2 execution:** Halo-derived scenes and game systems are running in development builds on real PlayStation 2 hardware and in PCSX2.
- **VU1/GS rendering:** a PS2-specific geometry and rendering path is operational, including terrain, scenery, depth-tested occlusion, first-person hands and weapon presentation.
- **Asset preparation:** an offline content-cooking pipeline converts supported Halo scene and asset data into formats intended for the PS2 runtime.
- **Scene visibility:** BSP-informed visibility, frustum culling and other geometry-reduction techniques are integrated into the rendering work.
- **Gameplay integration:** movement and static collision are functioning in test scenes, with experimental enemy collision, weapon damage and actor removal.
- **Flashlight proof of concept:** a per-pixel diffuse flashlight response has been demonstrated in development captures, although its performance and full material response remain under development.

### Multi-layer streaming and prediction

A major part of the engine is a sophisticated, multi-layer streaming and prediction architecture designed around the PS2's limited memory and DVD bandwidth. Rather than relying on a single level-loading step, the system is being developed to coordinate several complementary layers:

- **Scene and BSP streaming:** prepare upcoming environment sections while retaining the data required by the active area.
- **Predictive prefetch:** use player movement, scene connectivity and likely transitions to anticipate which data may be needed next, instead of waiting for a visible loading event.
- **Asset-level residency:** manage textures, geometry and other resources independently so that high-priority content can remain available while less urgent data is loaded or evicted.
- **Memory-aware scheduling:** coordinate RAM budgets, decompression, asset preparation and transfers to reduce contention with gameplay and rendering.
- **Frame-coordinated delivery:** schedule loading and residency changes alongside simulation and rendering, with the aim of avoiding disruptive frame-time spikes.
- **Hardware-grounded virtual DVD testing:** develop and test on real PS2 hardware using a virtual DVD reading system that emulates disc seeks and read-data retrieval against a properly authored DVD ISO. Data placement within the image is organised to support efficient streaming, allowing the loading pipeline to be assessed under disc-like access patterns before physical DVD validation.

This architecture combines implemented foundations with ongoing integration and optimisation work. Its goal is seamless progression through Halo's environments from physical DVD, without requiring an internal hard drive.

### Current development priorities

- **Performance optimisation:** reduce CPU-side simulation, object processing, geometry submission and rendering overhead to approach a stable gameplay frame rate on real hardware.
- **GS Recipe System:** catalogue Halo's Xbox shaders and materials, develop efficient GS-pass recipes, and provide PS2-native alternatives where direct reproduction is too expensive or impractical. Recipes must meet visual and performance requirements before acceptance.
- **UI and menu reconstruction:** recreate Halo's interface, ring effects, transitions and materials using the PS2 rendering pipeline.
- **lxGS lighting:** develop efficient per-pixel diffuse, normal-mapped and specular lighting, including flashlight and spotlight effects.
- **aaGS antialiasing:** investigate practical GS-based approaches to reduce silhouette shimmer and edge crawling.
- **Multi-layer streaming and prediction:** develop and refine a coordinated streaming system that anticipates upcoming scene and asset requirements, balances memory residency and prepares data before it is needed.
- **Frame orchestration:** consolidate loading, streaming and rendering work under a coordinated frame-management system.

**The project remains in active development; no release date has been announced.**

## How AI Is Used in This Project

The HALO PS2 Project is a **human-architected engineering project developed in collaboration with agentic AI tools**.

The project's overall technical vision, engineering direction and system architecture are conceived and overseen by its creator, who serves as **Project Lead and Systems Architect**.

The majority of the project's core architectural concepts originate from human-led research, technical reasoning and proposed solutions to the unique challenges of PlayStation 2 hardware.

AI acts as a collaborative engineering partner, helping investigate these concepts, assess their feasibility, explore alternative approaches and identify opportunities for refinement.

Through an iterative design process, proposed architectures are researched, challenged, tested and collaboratively refined before their final implementation is agreed upon.

### Roles and Responsibilities

**Project Lead & Systems Architect (Human)**

- Establishes the project's vision, technical objectives and engineering priorities.
- Conceives and proposes the overarching system architectures, rendering techniques and optimisation strategies.
- Defines hardware constraints, performance targets and expected behaviour.
- Directs technical investigations and evaluates proposed solutions.
- Oversees architectural development and makes final design and implementation decisions.

**AI Engineering & Development Agents**

- Research PS2 hardware capabilities and investigate the feasibility of proposed architectural concepts.
- Evaluate implementation strategies, identify limitations and suggest refinements.
- Collaborate in developing detailed technical specifications and implementation plans.
- Translate agreed architectures into working code, tools and engine components.
- Execute tests, analyse profiling data, diagnose problems and implement optimisations.
- Maintain technical documentation and development records.

### Development Philosophy

**Human architectural vision. Collaborative engineering. AI-accelerated implementation.**

The project follows a continuous cycle of architectural design, technical investigation, collaborative refinement, implementation and hardware validation.

AI is not used simply to generate code, nor is it responsible for independently determining the project's direction. Instead, it provides the research, analytical and implementation capabilities needed to explore and realise ambitious human-conceived engineering ideas.

All systems are subject to technical evaluation, performance measurement and testing, including execution on real PlayStation 2 hardware.

This approach combines **human creativity, architectural oversight and engineering judgement with the analytical and development capabilities of modern agentic AI**, enabling complex, hardware-specific systems to be developed and refined at a pace that would otherwise be difficult for a small independent project.

*And yes, this section was written by AI — with human input, refinement, and final validation.*

## About this repository

This is the public companion repository for The HALO PS2 Project. It contains only this public README, with embedded project screenshots.

The development repository remains private. Source code, game assets, builds and confidential development documents are not published here.

## Contact

For questions about The HALO PS2 Project, contact [acidreach@gmail.com](mailto:acidreach@gmail.com).

## Acknowledgements

Halo and PlayStation are trademarks of their respective owners. This is an independent fan project, unaffiliated with Microsoft, Xbox, Bungie, Halo Studios or Sony Interactive Entertainment.
