<div align="center">

<img src="assets/readme/hero.svg" alt="mingw64_dart — Dart SDK for MSYS2 MinGW64" width="100%"/>

<br/>

[![Build](https://github.com/Bloby22/mingw64_dart/actions/workflows/build.yml/badge.svg)](https://github.com/Bloby22/mingw64_dart/actions/workflows/build.yml)
[![GitHub Release](https://img.shields.io/github/v/release/Bloby22/mingw64_dart?color=54c5f8&labelColor=161b22&style=flat-square&label=latest)](https://github.com/Bloby22/mingw64_dart/releases)
[![License: MIT](https://img.shields.io/badge/license-MIT-f0c040?labelColor=161b22&style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-MINGW64-54c5f8?labelColor=161b22&style=flat-square)](https://www.msys2.org/)

</div>

---

## Install

Open an **MSYS2 MINGW64** terminal and run:

```bash
pacman -U https://github.com/Bloby22/mingw64_dart/releases/latest/download/mingw-w64-x86_64-dart-latest.pkg.tar.zst
```

Verify the install:

```bash
dart --version
# Dart SDK version: 3.13.5 (stable) on "windows_x64"
```

> **Requires MSYS2 MINGW64.** UCRT64 and CLANG64 are not supported.

---

## What this is

The official Dart SDK does not ship a native MSYS2 package. This project fills that gap: a community-maintained `PKGBUILD` that wraps the official Dart SDK into a proper `pacman`-installable `.pkg.tar.zst`, plus a native `dart.exe` launcher that works correctly inside MSYS2 bash.

**What's included:**

- Dart SDK (latest stable — currently `3.13.5`)
- Native `dart.exe` launcher for MSYS2 bash
- SHA256-verified download in every build

---

## How it works

<img src="assets/readme/how-it-works.svg" alt="Build pipeline: dart.dev → GitHub Actions → makepkg → Release → pacman" width="100%"/>

A GitHub Actions workflow runs daily, checks for a new Dart stable release, opens a PR with an updated `PKGBUILD` and the official SHA256 checksum, builds the package, and publishes the `.pkg.tar.zst` to Releases automatically.

---

## Build from source

```bash
# In MSYS2 MINGW64
pacman -S --needed git base-devel mingw-w64-x86_64-gcc
git clone https://github.com/Bloby22/mingw64_dart.git
cd mingw64_dart
makepkg -si
```

> The build downloads ~200 MB (the official Dart SDK archive).

---

## Compatibility

| Environment | Status |
|---|---|
| MSYS2 MINGW64 | ✅ Supported |
| MSYS2 UCRT64 | ❌ Not supported |
| MSYS2 CLANG64 | ❌ Not supported |
| Native Windows (no MSYS2) | ❌ Use [dart.dev](https://dart.dev/get-dart) instead |

---

## License

- **This project** — [MIT License](LICENSE)
- **Dart SDK** — [BSD 3-Clause](LICENSE-BSD) (Google)

This project is not affiliated with Google or the MSYS2 project.
