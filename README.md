# Bashir Electronic – 14.02 Stability Edition

**Release:** 1.0.0  
**Date:** 2026-11-15  
**Purpose:** PS4 browser host with the existing firmware branches and the dedicated 14.00 / 14.02 Afterglow path.

## Supported firmware routes

- 9.00–9.60
- 10.00–11.02
- 11.50–12.02
- 12.50–13.00
- 13.02–13.52
- 14.00 and 14.02

The 14.02 path has its own Afterglow firmware table and its own `slopkit/patches/1402.bin` file. The 14.02 entry is not a rename of `1400.bin`.

## Offline cache

`slopkit.manifest` includes the GoldHEN payload and all Slopkit assets, including `slopkit/patches/1402.bin`. The patch file is already included in this ZIP; the `prepare-1402.bat` / `prepare-1402.ps1` downloader utilities are intentionally not shipped in the website folder.

Upload the **entire `b2` folder** to the same relative path on your host. Do not upload only selected files. After replacing an existing deployment, clear the PS4 browser's old site data/cache once so the new AppCache manifest can be installed.

## Stability-focused changes in this package

- Bundled the user-supplied `1402.bin` at the exact path expected by Afterglow.
- Added the 1402 patchset to the Slopkit AppCache manifest and changed its revision comment so AppCache sees the new manifest.
- Kept 14.00 and 14.02 kernel tables separate.
- Added cleanup for the JavaScript watchdog and RAM-monitor timers when the UI reaches a final state or a retry state. This is UI housekeeping only; it does not modify exploit offsets, kernel patches, payload bytes, or the exploit sequence.
- Updated the README and added checksums for the two critical binary assets.

## Important safety note

Kernel exploit runs can still hard-crash or power-cycle a console if a low-level race fails in an uncaught stage. Save open application/game data before testing. A successful cache install is not proof that the exploit run will be stable. Do not interpret a retry message as proof that the whole kernel process is still alive.

## Integrity

See `CHECKSUMS.txt` for SHA-256 fingerprints of `slopkit/patches/1402.bin` and `goldhen_2.4b18.14.bin`.

## Attribution and upstream references

- Afterglow web implementation and firmware tables: https://github.com/well0nez/afterglow-web (AGPL-3.0-or-later; see upstream `LICENSE`).
- The current GamerHack G2All landing-page route accepts 14.00 and 14.02 and sends both to `slopkit/jb2.js`: https://github.com/GamerHack/GamerHack.github.io/tree/main/g2all
- Bashir project: https://github.com/pas3/8/tree/main/b2

This package preserves the existing Bashir Arabic UI, background, message styling and older firmware folders. It is a static code package; no actual PS4 hardware test can be performed in this build environment.

**Arabic identity:** تعريب وتطوير بشير لصيانة الأجهزة الإلكترونية والرقمية.
