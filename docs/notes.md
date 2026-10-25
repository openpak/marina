# Notes: marina

## About

Marina is OpenPak's Wii emulator, built on the Dolphin codebase. It is
firmware-first: the goal is to boot the console's own System Menu, IOS and
BC/MIOS from the owner's NAND dump and to reach OpenPak's replacement online
services for Wii Wi-Fi Connection (WFC) games. GameCube software is meant to
run the way the real Wii runs it (System Menu, BC, boot2, MIOS), with no
separate GameCube firmware track.

**Status:** Early (builds on Linux; not yet run against firmware, a game or
OpenPak services).

## Not affiliated

Marina is an independent project maintained by OpenPak. It is not an official
Dolphin release, is not endorsed by the Dolphin project, and is not affiliated
with Nintendo. Nintendo, Wii and Wii Wi-Fi Connection are trademarks of their
owners.

## What works today

Marina starts from OpenPak's Dolphin fork at tag `v0.2.4`, which carries the
OpenPak integration listed below; everything else is upstream Dolphin.

- An OpenPak menu and window (account, friends read-only, cloud saves, mods
  catalogue, status, news) shared with the other OpenPak emulators, plus an
  Android port of those screens.
- Cloud saves for Wii titles: a title's NAND save directory is pulled before
  boot and pushed after stop, with a conflict dialog.

## Known limitations

- Marina currently behaves like Dolphin plus the OpenPak additions. The
  firmware-first work (real BC path, real per-title IOS selection, first-run
  firmware install) is planned, not done. Every IOS module is still a C++
  reimplementation.
- No game or firmware boot has been attempted with Marina.
- Many build targets, file names and docs still say Dolphin; the Marina icon
  in `Data/` is not wired into the build.
- The Mods page is a read-only catalogue; installing mods is not done. Friends
  are read-only, and Invitations and News have no content on Wii.
- Android lacks system notifications and keychain storage for the token.

## Contributing and support

Issues: https://github.com/openpak/marina/issues. Security problems: report them privately to the OpenPak
maintainers through the contact on https://openpak.org, not in a public issue.

Most useful right now: testing on your own NAND dump and reports of what the
real System Menu does, WFC titles that connect or fail, and Windows or macOS
build fixes. [Contributing.md](../Contributing.md) is the upstream code style and
legal guide and still applies.

## License and acknowledgements

Marina is licensed under GPL-2.0-or-later, as Dolphin is. See [COPYING](../COPYING),
[LICENSES](../LICENSES) and the per-file SPDX notices; some components carry
their own terms, and the whole tree is GPLv3-compatible.

Thanks to the Dolphin contributors ([dolphin-emu.org](https://dolphin-emu.org/),
[github.com/dolphin-emu/dolphin](https://github.com/dolphin-emu/dolphin)) and
the projects credited in the inherited source.

The Marina icon (`Data/marina.svg` and its 256 px render) is separate artwork,
Copyright 2026 tobagin, AGPL-3.0-only, packaged as an asset and not embedded
in the emulator.

The upstream Dolphin README is kept unchanged in [Readme.md](../Readme.md).
