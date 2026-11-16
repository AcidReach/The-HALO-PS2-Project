# The HALO PS2 Project

**Bringing Halo to PlayStation 2 as a faithful port, retaining everything that makes it Halo.**

The HALO PS2 Project aims to deliver Halo as a faithful, contemporary PlayStation 2 port—as if it had launched alongside the original Xbox release.

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

## Screenshots

Development captures showing work in progress.

### Terrain rendering

![Halo terrain rendering](https://github.com/user-attachments/assets/cd078378-e9ae-419c-9aa1-bb89e1e6a888)

### First-person presentation and scenery

![First-person rifle and scenery](https://github.com/user-attachments/assets/653dc9de-3ad0-41b1-b0db-a1b1339b423d)

## About this repository

This is the public companion repository for The HALO PS2 Project. It contains only this public README, with embedded project screenshots.

The development repository remains private. Source code, game assets, builds and confidential development documents are not published here.

## Acknowledgements

Halo and PlayStation are trademarks of their respective owners. This is an independent fan project, unaffiliated with Microsoft, Xbox, Bungie, Halo Studios or Sony Interactive Entertainment.
