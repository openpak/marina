# Marina

OpenPak's Marina Emulator.

| | |
| --- | --- |
| Console | Wii |
| Kind | Emulator |
| Based on | [Dolphin](https://github.com/dolphin-emu/dolphin) (GPL-2.0-or-later) |

## What it does

- Firmware-first: the goal is to run the console's own System Menu, IOS and
  BC/MIOS from your own NAND dump. GameCube software runs the way the real Wii
  runs it, with no separate GameCube firmware track.
- Redirects the console's Wii Wi-Fi Connection (WFC) host names to OpenPak when
  Config > Wii > "Connect Nintendo WFC to OpenPak" is on. The host list comes
  from a network profile fetched at launch.
- An OpenPak menu and window (account, friends, cloud saves, mods catalogue,
  status, news), shared with the other OpenPak emulators, with an Android port
  of those screens.
- Cloud saves for Wii titles: a title's NAND save directory is pulled before
  boot and pushed after stop, with a conflict dialog.
- Imports your own BootMii NAND backup (Tools > Import BootMii NAND Backup).
  OpenPak provides no firmware, keys, NAND contents or games.

## Build

See [deploy](docs/deploy.md).

```sh
git submodule update --init --recursive
cmake -B build -G Ninja -DCMAKE_BUILD_TYPE=Release
cmake --build build
```

## Docs

- [Protocol](docs/protocol.md)
- [Evidence](docs/evidence.md)
- [Deploy](docs/deploy.md)
- [Notes](docs/notes.md)
- [autoupdate_overview.md](docs/autoupdate_overview.md)
- [CustomPipelineGraphicsMod.md](docs/CustomPipelineGraphicsMod.md)
- [DolphinDeviceIOCTLs.md](docs/DolphinDeviceIOCTLs.md)
- [DynamicInputTextures.md](docs/DynamicInputTextures.md)
- [ResourcePacks.md](docs/ResourcePacks.md)
- [WiaAndRvz.md](docs/WiaAndRvz.md)
- [codehandler.ld](docs/codehandler.ld)
- [codehandler.s](docs/codehandler.s)
- [game-mod-descriptor.json](docs/game-mod-descriptor.json)
- [gc-font-tool.cpp](docs/gc-font-tool.cpp)
- [ActionReplay](docs/ActionReplay)
- [DSP](docs/DSP)
- [WiiMote](docs/WiiMote)
