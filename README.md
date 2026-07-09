# UE5 Medieval — First-Person Prototype

A first-person gameplay prototype built in **Unreal Engine 5.4**, set in a medieval
village environment. This repository contains **my own work** — Blueprints, the
gameplay/weapon systems, input setup and level design — as a portfolio sample.

> **Note on assets:** Third-party art packs (Unreal *Starter Content*, the
> *Advanced Village Pack* from the Marketplace/Fab, and *Unreal Learning*
> content) are **intentionally not included** in this repository. They are
> licensed and may not be redistributed as raw assets. Because of this, opening
> the map will show missing environment meshes until those packs are re-added.
> The purpose of this repo is to show the **code and systems**, not the art.

## What I built

- **First-person character** — movement, look and jump using Enhanced Input
  (`BP_FirstPersonCharacter`, `IMC_Default`, `IA_Move` / `IA_Look` / `IA_Jump`).
- **Weapon system** — a modular weapon component with a pickup flow
  (`BP_Weapon_Component`, `BP_Pickup_Rifle`, `IA_Shoot`, `IMC_Weapons`).
- **Projectile logic** — `BP_FirstPersonProjectile`.
- **Game framework** — custom Game Mode and Player Controller
  (`BP_FirstPersonGameMode`, `BP_FirstPersonPlayerController`).
- **Level design** — the medieval village scene assembled with modular pieces
  (level actor data under `Content/FirstPerson` and the `__ExternalActors__`
  one-file-per-actor data).

## Tech

| | |
|---|---|
| Engine | Unreal Engine 5.4 |
| Type | Blueprint project (no C++) |
| Input | Enhanced Input System |
| Large files | Tracked with Git LFS (`.uasset`, `.umap`, textures) |

## Running the project

1. Clone the repository (Git LFS is required — install from https://git-lfs.com).
   ```
   git lfs install
   git clone https://github.com/etepeyurt/UE5Medieval.git
   ```
2. Open `UE5Medieval.uproject` with Unreal Engine **5.4**.
3. To restore the full environment art, re-add **Starter Content** and the
   **Advanced Village Pack** from the Epic Launcher / Fab.

## Repository layout

```
Content/FirstPerson/     # Blueprints, input, weapon system, main map  (my work)
Content/FirstPersonArms/ # First-person arms & weapon meshes (UE template)
Content/LevelPrototyping/# Greybox prototyping meshes (UE template)
Config/                  # Project configuration
UE5Medieval.uproject     # Project file
```
