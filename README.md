# The HALO PS2 Project

**Bringing Halo to PlayStation 2 as a faithful port, retaining everything that makes it Halo.**

The HALO PS2 Project aims to deliver Halo as a faithful, contemporary PlayStation 2 port—as if it had launched alongside the original Xbox release.

## Screenshots

Development captures showing work in progress.

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
- **Lighting and effects:** developing Graphics Synthesizer pass recipes to represent effects originally accomplished with Halo’s Xbox shaders.
- **Content preparation:** offline processing of meshes, textures, materials, scenes and animation data for PS2 runtime use.
- **Visibility and memory management:** scene visibility, geometry culling and texture budgeting to use limited resources efficiently.

## Project status

**In active development, with working rendering and Halo integration on real PS2 hardware.**

Achievements so far include:

- **An efficient VU1-based renderer:** a rendering foundation built around the PS2’s Vector Unit 1 and Graphics Synthesizer.
- **GS pass recipes for Halo effects:** rendering techniques that integrate effects originally accomplished with Halo’s Xbox shaders, with further work toward full visual coverage and accuracy.
- **A working per-pixel flashlight:** functional lighting, with optimization still needed to meet the performance target.
- **Halo terrain and scenery rendering:** environments and placed objects rendered together, with terrain correctly hiding objects behind it.
- **First-person presentation:** working hands and rifle rendering, including ready and idle presentation.
- **Collision and movement:** working static scenery and enemy collision with sliding.
- **Limited weapon interactions:** an experimental combat slice supporting actor damage and removal of defeated actors from rendering and collision.

These milestones establish parts of the port’s foundation. They do not yet constitute a complete playable campaign. Full animation, active enemy AI, complete effects coverage and end-to-end DVD streaming remain development goals.

No release date is announced.

## About this repository

This is the public companion repository for The HALO PS2 Project. It contains only this public README, with embedded project screenshots.

The development repository remains private. Source code, game assets, builds and confidential development documents are not published here.

## Acknowledgements

Halo and PlayStation are trademarks of their respective owners. This is an independent fan project, unaffiliated with Microsoft, Xbox, Bungie, Halo Studios or Sony Interactive Entertainment.
