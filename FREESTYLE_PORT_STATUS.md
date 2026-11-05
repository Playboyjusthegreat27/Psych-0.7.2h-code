# Freestyle port status

Target: Psych Engine 0.7.2h
Working branch: freestyle-port
Source project: Friday-Niite-Freestyle (original Kade source remains untouched)

## Source archive inspected

The supplied freestyle-html-main archive contains 18 song folders and 54 chart JSON files (normal, easy, and hard for each song), plus matching OGG instrumental and vocal tracks.

The Kade chart files use the nested song object and section note arrays that are close to Psych's chart structure. They still need normalization and validation before import.

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

Psych's built-in definitions cover several base characters. Custom IDs need dedicated Psych JSON definitions or explicit aliases. The duet and glitch variants require atlas and behavior checks before they can be mapped safely.

## Stage IDs found

`halloween`, `limo`, `mall`, `philly`, `school`, `schoolEvil`.

Stage assets and behavior need to be checked against these names. Stage-specific Kade behavior will not automatically carry over.

## Migration rules

- Keep original Kade source unchanged.
- Preserve note timing, sustain lengths, section ownership, BPM changes, and character assignments.
- Convert chart JSONs into Psych's expected format and translate or remove Kade-only metadata deliberately.
- Copy song audio into Psych's `assets/songs/<song>/` layout.
- Convert character animation definitions while preserving prefixes, indices, offsets, scale, flip, health icon, and camera offsets.
- Port custom stages and gameplay behavior separately.
- Build and test a representative song before expanding to all 18 songs.

## Build environment progress

- Restored and inspected the supplied `freestyle-html-main.zip` from the user's Library.
- Rechecked all 54 charts and confirmed all 23,020 note entries use three-value note arrays.
- Added a dedicated HTML5 release workflow.
- The first build exposed a dependency mismatch: the workflow installed newest Haxe libraries, while Psych 0.7.2 expects a tested older set. This caused missing FlxSound and ClickStuff types inside FlxAnimate.
- Updated the workflow to Haxe 4.3.2, Psych 0.7.2-compatible library versions, and a pinned FlxAnimate commit from the engine's documented library set.
- The corrected workflow has not yet completed a build. No playable artifact is available yet.

## Current state

The source archive is available and inventoried. Dependency pinning is now in place; next is verifying the corrected build, then importing and validating charts, audio, characters, and stages. No original source project files have been overwritten.
