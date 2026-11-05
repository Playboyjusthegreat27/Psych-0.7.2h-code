# Freestyle port status

Target: Psych Engine 0.7.2h
Working branch: freestyle-port
Source project: Friday-Niite-Freestyle (original Kade source remains untouched)

## Source archive inspected

The supplied freestyle-html-main archive contains 18 playable song folders and 54 chart JSON files (normal, easy, and hard for each song), plus the matching OGG instrumental and vocal tracks.

The Kade chart files already use the familiar nested `song` object and section note arrays. They are close to Psych's chart structure, but need normalization and validation before they are copied into `assets/shared/data/<song>/`.

Songs:
- creepz
- cruise-control
- doobop
- ecstacy
- flurry
- funky-nice
- gunfight
- joyride
- night-lights
- north
- recess
- refreshed
- slurry
- snowblind
- social-suicide
- splinters
- spooky-fight
- turf-war

## Character IDs found in song metadata

`bf`, `bf-car`, `bf-christmas`, `bf-duet`, `bf-pixel`, `bf-pixel-glitch`, `dad`, `gf-car`, `gf-christmas`, `gf-pixel`, `gf-pixel-glitch`, `mom-car`, `parents-christmas`, `pico`, `senpai`, `senpai-angry`, `spooky`.

Psych's built-in character definitions cover several base characters. The custom IDs need dedicated Psych JSON definitions or explicit aliases. In particular, `bf-duet`, `bf-pixel-glitch`, and `gf-pixel-glitch` cannot be treated as existing built-in characters without checking their animation atlases and intended behavior.

## Stage IDs found

`halloween`, `limo`, `mall`, `philly`, `school`, `schoolEvil`.

The standard stage assets and stage Lua/Haxe behavior need to be checked against these names. Stage-specific Kade code will not automatically carry over.

## Important migration notes

- Keep original Kade source unchanged.
- Keep song chart timing, sustain lengths, section ownership, BPM changes, and character assignments intact.
- Convert chart JSONs into Psych's expected chart wrapper and remove or translate Kade-only metadata where needed.
- Copy song audio into Psych's `assets/songs/<song>/` layout.
- Convert Kade hardcoded character animation definitions into Psych character JSONs. Preserve animation prefixes, frame indices, offsets, scale, flip, health icon, and camera offsets.
- Port custom stages and gameplay behavior separately; copying image atlases alone is not enough.
- Build and test one representative song first, then expand to all 18 songs.

## Current state

This branch is a safe working branch only. No source project files have been overwritten and no claim is made that the port is complete or build-tested yet.
