# Marina

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

- The `marina` branch configures and builds on Linux (CMake and Ninja,
  Release) and reports its version on startup. This is the only thing run so
  far.
- A Config > Wii checkbox, "Connect Nintendo WFC to OpenPak", redirects the
  console's WFC host names to OpenPak. The host list and address come from a
  network profile fetched at launch, checked against a list compiled into the
  build, with the last good profile and then a built-in list as fallbacks.
- An OpenPak menu and window (account, friends read-only, cloud saves, mods
  catalogue, status, news) shared with the other OpenPak emulators, plus an
  Android port of those screens.
- Cloud saves for Wii titles: a title's NAND save directory is pulled before
  boot and pushed after stop, with a conflict dialog.

Not verified: the redirect and save sync build and link but have not been run
against a game. No Wii firmware boot has been attempted, no WFC match against
OpenPak has happened, and no title's online compatibility is established.

## Connecting to OpenPak

Create an account at https://openpak.org, then use OpenPak > Sign in in the
emulator. The account only names you and authorises cloud saves; WFC itself
has no accounts. Tick the WFC checkbox in Config > Wii to redirect the
console's names to OpenPak. Games that need a patch to use plain HTTP for
their login also need OpenPak's stage-0 Gecko code, published with the
wii-patcher project in the OpenPak organisation.

You must supply your own Wii NAND dump (made with BootMii on your own
console, with its keys) and your own games. Import the dump with Tools >
Import BootMii NAND Backup. OpenPak provides no firmware, keys, NAND contents
or games and never will.

## Downloads

No public build yet. The release workflow runs on `v*.*.*` tags, but no
release has been published and none is advertised. Releases would appear at
https://github.com/openpak/marina/releases.

## Building from source

Follow the upstream Dolphin build pages for your OS (Windows, Linux, macOS)
linked from [Readme.md](Readme.md), and pull submodules first:

```sh
git submodule update --init --recursive
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

OpenPak-specific notes:

- The OpenPak account and cloud-save code lives in the `Externals/openpak-client`
  submodule, which is currently in a private repository, so outside builders
  cannot fetch it yet.
- On a 12 GB machine `-j16` was OOM-killed and `-j8` completed.
- Android uses the Gradle project in `Source/Android`.

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
build fixes. [Contributing.md](Contributing.md) is the upstream code style and
legal guide and still applies.

## License and acknowledgements

Marina is licensed under GPL-2.0-or-later, as Dolphin is. See [COPYING](COPYING),
[LICENSES](LICENSES) and the per-file SPDX notices; some components carry
their own terms, and the whole tree is GPLv3-compatible.

Thanks to the Dolphin contributors ([dolphin-emu.org](https://dolphin-emu.org/),
[github.com/dolphin-emu/dolphin](https://github.com/dolphin-emu/dolphin)) and
the projects credited in the inherited source.

The Marina icon (`Data/marina.svg` and its 256 px render) is separate artwork,
Copyright 2026 tobagin, AGPL-3.0-only, packaged as an asset and not embedded
in the emulator.

The upstream Dolphin README is kept unchanged in [Readme.md](Readme.md).
