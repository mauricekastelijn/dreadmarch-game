# DREADMARCH

**Hold the line. Bring down giants.**

[![Build and deploy](https://github.com/mauricekastelijn/dreadmarch-game/actions/workflows/deploy.yml/badge.svg)](https://github.com/mauricekastelijn/dreadmarch-game/actions/workflows/deploy.yml)

## [PLAY DREADMARCH](https://mauricekastelijn.github.io/dreadmarch-game/)

A third-person 3D rail shooter for mobile and desktop, built with Three.js. Fight marching soldiers and creatures, destroy supply targets to unlock weapons, and face six colossal guardians across twelve battlefields.

The game uses animated, skinned soldier, demon and skeleton assets. Rifles have modelled receivers, scopes, rails, magazines, heat fins and recoil. Environments feature textured terrain, ruins, mushrooms, crystals, water, ice, volcanic rocks and industrial structures. Hardware rendering adds lighting and dynamic shadows. An actual perspective-triangle software renderer keeps the game playable when WebGL 2 is unavailable, with reduced distant-character detail.

## Controls

| Input | Action |
| --- | --- |
| Mobile: drag across the battlefield | Aim and move to dodge; touch aim is offset above your finger |
| Desktop: mouse, WASD or arrow keys | Aim and move |
| Auto Fire | Enabled initially; toggle for manual firing |
| Hold FIRE / Space | Fire your current weapon |
| Shockwave button / E | Clear enemy projectiles and damage nearby threats; limited charges |
| Pause button / P / Escape | Pause or resume |
| Settings | Graphics, reduced shake, aim assist and inverted movement |

Tap **DEPLOY TO THE FRONTLINE** to start. Shooting and dodging share the reticle. Aim at the glowing core of a guardian for critical damage. Sound begins muted; tap **SOUND OFF** to enable synthesized combat audio. Changing tabs or apps pauses the game automatically.

## Shoot supply targets to upgrade

Glowing, rotating supply pods show their reward label. Destroy the pod to receive its reward immediately. Weapon unlocks persist on this device and become selectable in the deployment loadout.

| Weapon | Behaviour |
| --- | --- |
| MK-I Pulse | Reliable automatic rifle |
| Twin Repeater | Faster, stronger repeat fire |
| Scatter Cannon | Heavy hits with splash against nearby targets |
| Piercing Rail | High damage and penetration through aligned targets |
| Seeker Array | Finds the nearest hostile target when no target is directly locked |
| Arc Conductor | Chains damage between nearby enemies |

Other pods provide **barriers**, **repairs**, **shockwave charges** and **14-second overdrive**. Maintain a kill chain for score multipliers. Reserve ships restore health after defeat, with a checkpoint immediately before guardian battles.

## Campaign

| Sector | Battlefield | Encounter |
| --- | --- | --- |
| 01 | Emerald Frontier | Iron Captain |
| 02 | Mushroom Wilds | Spore Titan |
| 03 | Sunken Causeway | Tide Warden |
| 04 | Drowned Temple | Leviathan |
| 05 | Crystal Canyon | Prism Hunter |
| 06 | Frozen Citadel | Frost Colossus |
| 07 | Ashen March | Cinder Commander |
| 08 | Iron Foundry | Siege Walker |
| 09 | Storm Above | Sky Reaper |
| 10 | Bone Desert | Sand Devourer |
| 11 | Fractured Reality | The Last Legion |
| 12 | Heart of the Rift | Rift Sovereign |

Marching waves last approximately 72 simulation seconds before a commander or guardian arrives. Giant guardians appear in even-numbered sectors and increase their attacks as health falls. Enemy families include rifle soldiers, shield troops, running demons, skeletons, drones, brutes and summoners. Commanders, winged demons, articulated serpents and a mechanical walker have different silhouettes and animation systems.

## Modes and progression

- **Campaign:** three reserve ships, unlocked insertion points and saved progress.
- **Arcade:** one life and a high-score focus.
- **Endless Survival:** cycles through the twelve sectors indefinitely.
- **Boss Rush:** the six giant-guardian encounters in succession.
- **Daily Assault:** a dated seed selects a battlefield and reproducible random formations. This is a local challenge, without an online leaderboard.
- **Recruit / Standard / Veteran:** change damage received.

Best score, campaign checkpoint, reached sectors, unlocked weapons and settings stay in browser local storage. Nothing is uploaded to a game server. Clearing browser data resets this progress.

## Build and automatic deployment

Every push to `main` runs syntax checks, tests, a static build, and GitHub Pages deployment. Pull requests run checks without publishing. Launch manually with **Actions → Build and deploy game → Run workflow**.

One-time setup: in [Settings → Pages](https://github.com/mauricekastelijn/dreadmarch-game/settings/pages), select **GitHub Actions**. Publishing from `main` at `/ (root)` also works: the repository and Actions artifact have identical root launchers that open `dist/`, avoiding README landing pages.

No dependency install, build service, API key or personal access token is needed. Three.js and character models are bundled locally.

```sh
# Node.js 22
npm run check
npm test
npm run build

# Python 3
python3 -m http.server 8080 --directory _site
```

Open http://localhost:8080. For direct development, run `python3 -m http.server 8080` from the project root. Serve over HTTP rather than opening files directly because JavaScript modules and models need web requests.

## Rendering and mobile performance

- Real perspective camera and 3D meshes; skeletal animation with clip blending.
- Shared geometry/materials, merged rifle meshes and instanced scenery/projectiles.
- Fixed 120 Hz gameplay simulation, capped frame catch-up and bounded enemy/projectile counts.
- Automatic resolution reduction on slow hardware, plus explicit high, balanced and battery-saver modes.
- Hardware shadows on supported settings; a software 3D fallback uses the same scene and model animation, with simpler distant soldiers and fewer detailed actors.
- Original procedural environmental textures, effect sprites and Web Audio sounds.

High-detail graphics performance depends on the device. The compatibility renderer prioritises playability over hardware-renderer fidelity.

## Source

- `dist/engine.js` — deterministic combat, modes, campaign and rewards.
- `dist/visuals.js` — character rigs, weapons, monsters, scenery and effects.
- `dist/game.js` — Three.js scene, interface, targeting, controls, audio and saves.
- `dist/software.js` — perspective software fallback with animated skinning.
- `dist/models/` — bundled animated GLBs.
- `dist/vendor/` — Three.js and loader utilities.
- `tests/` — combat and asset validation.
- `scripts/build.mjs` — standalone release packaging.

Asset sources and licenses are documented in [CREDITS.md](CREDITS.md).
