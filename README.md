# UE5 Medieval — First-Person Interaction Prototype

An Unreal Engine 5.4 learning project built on Epic's First Person template and
extended with a custom, **interface-driven interaction system** and a small
menu → level → game-over loop, set in a medieval village.

## Gameplay loop

**Main menu** (`Play` / `Exit`) → **BasicLevel**: explore in first person, look
at objects and press the interact key to trigger them. A roaming monster ends
the run and sends you back to the menu.

## What I built

- **Interaction system** — a base `BP_InteractActor` class exposing an
  interaction interface. The player character line-traces from the camera on the
  `IA_Interact` (Enhanced Input) action and calls the interface on whatever it
  hits, so any derived actor becomes interactable:
  - **`BP_Button`** — on interact, plays a sound and broadcasts
    `OnButtonActive` / `OnButtonPassive` event dispatchers that other actors
    subscribe to (a decoupled, event-driven design).
  - **`BP_Door`** — subscribes to a button and opens/closes with a
    Timeline-driven rotation.
  - **`BP_LightSource`** — toggles a point light on/off from the button events.
  - **`BP_Windmill`** — starts a Timeline-driven spin when the player enters its
    trigger volume.
- **`BP_Monster`** — a moving character that travels a Timeline-driven path;
  on contact with the player it calls `OpenLevel` to return to the main menu
  (game-over).
- **UI & flow** — `WBP_MainMenu` (Play → `BasicLevel`, Exit → quit) and
  `WBP_HUD` (bound text for the interaction prompt).
- **Player character** — `BP_UnrealLearningCharacter`, which extends the
  template's first-person character with the interaction line-trace logic.
- **Levels** — `BasicLevel` (gameplay) and `MainMenu`, laid out in the medieval
  village environment.

## What I did not build

The first-person movement, camera, weapon and projectile Blueprints under
`Content/FirstPerson` come from **Epic's First Person template**. My character
extends that template; the weapon/projectile assets are left in only so the
project runs and are not my work.

## Assets

Third-party art — Epic **Starter Content** and the **Advanced Village Pack**
(Marketplace / Fab) — is **not redistributed** here for licensing reasons.
Opening a map will show missing environment meshes until those packs are
re-added from the Epic Launcher / Fab. The gameplay Blueprints above are the
point of this repository.

## Tech

| | |
|---|---|
| Engine | Unreal Engine 5.4 |
| Type | Blueprint project (no C++) |
| Input | Enhanced Input System |
| Patterns | Interface-based interaction, event dispatchers, Timelines |
| Large files | Git LFS (`.uasset`, `.umap`, textures) |

## Running the project

1. Install Git LFS (https://git-lfs.com), then clone:
   ```
   git lfs install
   git clone https://github.com/etepeyurt/UE5Medieval.git
   ```
2. Open `UE5Medieval.uproject` with Unreal Engine **5.4**.
3. Re-add Starter Content and the Advanced Village Pack from the Epic
   Launcher / Fab to restore the full environment art.
