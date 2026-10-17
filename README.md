# Marina

Marina is OpenPak's Wii emulator, built on the Dolphin codebase. It is an
independent project with its own name, direction and OpenPak integration.
This marks our departure from maintaining an OpenPak-branded Dolphin build:
the project is now Marina.

**Dolphin remains our upstream base.** We acknowledge and preserve the work
of Dolphin and its contributors, and can continue integrating applicable
upstream improvements. Marina is maintained by OpenPak; it is not an official
Dolphin release and is not presented as endorsed by the Dolphin project. The
original README is kept in [Readme.md](Readme.md).

## OpenPak direction

Marina is the active Wii emulator for OpenPak development and online
compatibility work. Its direction is firmware-first: it boots the console's
own firmware (System Menu, per-title IOS, BC/MIOS) from the owner's NAND
dump and talks to OpenPak's replacement online services, the way Harbor does
for the Switch, Pier for the PS3, Wharf for the Xbox 360 and Berth for the
original Xbox.

GameCube software runs the way the real Wii runs it: System Menu → BC →
boot2 → MIOS, from the owner's dump. There is no separate GameCube firmware
track.

## Source and development

- Workspace checkout: `emulators/marina` (links to `scratch/marina/src`).
- Upstream base: [Dolphin](https://github.com/dolphin-emu/dolphin).
- OpenPak patch base: `openpak/dolphin` at tag `v0.2.4` (branch `marina`).
- Base plan (phase 0): `docs/wii/marina-base-plan.md` in the OpenPak docs repo.
- OpenPak integration: [OPENPAK.md](OPENPAK.md) (WFC redirect, network
  profile, account sign-in, cloud saves).
- Current work state: [next-session.md](next-session.md).

Some inherited build targets, filenames, assets and documentation still use
Dolphin identifiers. These reflect the codebase's origin; the OpenPak
project is Marina. Follow local handoff documents for the current
implementation status.

No Wii firmware, keys or NAND contents are included or shipped. Obtain them
from your own console (BootMii dump) and import via Tools → Import BootMii
NAND Backup.

## License and acknowledgements

Marina preserves the upstream licensing and copyright notices. See [COPYING](COPYING),
[LICENSES](LICENSES) and individual source-file notices for the applicable
terms. Dolphin is GPL-2.0-or-later; components retain their own license terms.

Thanks to the Dolphin contributors and the other projects credited in the
inherited source. Renaming the fork does not change that provenance.

The separate Marina icon in `Data/marina.svg` (and its `Data/marina-256.png`
render) is user-supplied artwork, Copyright 2026 tobagin, AGPL-3.0-only as
declared in that SVG. It is packaged as a separate asset, not embedded into
the emulator binary. Wiring it into the build (desktop entry, window icon,
installer assets) happens with the application rename.
