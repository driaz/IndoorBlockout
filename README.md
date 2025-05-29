# IndoorBlockout (UE 5.5.4)

> **Tier 0 playable prototype** demonstrating moment-to-moment navigation, key pickup / door unlocking, and contextual player feedback in a compact interior space.

![screenshot](Docs/Images/cover.jpg) <!-- optional—add your own -->

---

## ✨ Features
| System              | Summary                                                                                |
|---------------------|----------------------------------------------------------------------------------------|
| **Grey-box environment**     | Single-room + mezzanine layout sized to UE mannequin metrics (1 uu = 1 cm).             |
| **Key / Door workflow**      | `BP_KeyPickup` & `BP_Door` Blueprints—collect key, unlock door, destroy key.          |
| **Floating reward orb**       | `BP_RewardPickup` with hover timeline; stores initial location to prevent drift.     |
| **Player notification HUD**   | `W_PlayerNotification` widget + `ShowStatusMessage` event for all on-screen feedback.|
| **Robust timer reset**        | Single 2 s timer per notification; spam-safe logic (Override Existing handle).       |
| **Performance guard-rails**   | < 60 draw calls in view; VSync ready; Nanite enabled on all heavy meshes.           |

---

## ▶️ Quick Start

1. **Clone**  
   ```bash
   git clone https://github.com/<your-username>/IndoorBlockout.git
   cd IndoorBlockout

2. Launch Unreal Engine 5.5.4 and open IndoorBlockout.uproject.

3. Press ▶ Play-In-Editor
	W/S/A/D – move Space – jump

| Blueprint Notes           | Purpose                                                     | Gotchas                                                         |
| ------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------- |
| **BP\_KeyPickup**         | Destroy-on-overlap; broadcasts `OnKeyCollected` dispatcher. | Collision = trigger only (no physics).                          |
| **BP\_Door**              | Listens for `OnKeyCollected`; rotates open with Timeline.   | Box collider disabled post-unlock to stop spam messages.        |
| **BP\_RewardPickup**      | Hover timeline; adds float to stored `StartLocation`.       | Stores initial Z so it doesn’t drift.                           |
| **W\_PlayerNotification** | Public `UpdateNotification(Text)` event sets TextBlock.     | Timer logic: Clear → SetTimer(OverrideExisting) → store handle. |


Version History
Tag	Date	Notes
v1.0-blockout	24 May 2025	First playable grey-box prototype.
v1.5-polished	⏳ planned	Add hero character, art kit pass, night-lighting option.


Roadmap 🛣️
1. Replace UE mannequin with marketplace hero mesh (retarget animations).

2. Swap grey boxes with library asset kit (large windows version).

3. Lumen lighting pass with Rect-Light window portals.

4. Fade-in / fade-out animation track for W_PlayerNotification.

5. Sound cues on pickup / unlock.

Contributing
Pull requests are welcome for bug-fixes or optimization tweaks.
For major changes please open an issue first to discuss scope.
