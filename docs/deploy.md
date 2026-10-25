# Deploy: marina

## Downloads

No public build yet. The release workflow runs on `v*.*.*` tags, but no
release has been published and none is advertised. Releases would appear at
https://github.com/openpak/marina/releases.

## Build from source

Follow the upstream Dolphin build pages for your OS (Windows, Linux, macOS)
linked from [Readme.md](../Readme.md), and pull submodules first:

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

## Wii NAND dump

You must supply your own Wii NAND dump (made with BootMii on your own
console, with its keys) and your own games. Import the dump with Tools >
Import BootMii NAND Backup. OpenPak provides no firmware, keys, NAND contents
or games and never will.
