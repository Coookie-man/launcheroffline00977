# Amethyst Offline (Android)

An offline-patched build of [Amethyst](https://github.com/AngelAuraMC/Amethyst-Android), a Minecraft: Java Edition launcher for Android based on PojavLauncher.

## What is this?

This repository takes the latest Amethyst-Android source (from the `v3_openjdk` branch) and applies patches to enable offline/local account usage — similar to [Amethyst-Offline](https://github.com/DumDum192/Amethyst-Offline).

### Patches Applied

- **Tools.patch** — Modifies `hasOnlineProfile()` to always return `true`, allowing local accounts to launch.
- **MinecraftDownloader.patch** — Removes the `isLocalProfile` check so downloads aren't blocked for offline accounts.

## Getting the APK

The APK is built automatically via GitHub Actions on every push. Download it from:

→ [Actions → Android CI → Latest run → Artifacts](../../actions/workflows/android.yml)

## Building Locally

### Prerequisites
- JDK 21
- Git

### Steps
```bash
git clone --recursive https://github.com/Coookie-man/launcheroffline00977.git
cd launcheroffline00977

# Apply patches
patch ./Amethyst-Android/app_pojavlauncher/src/main/java/net/kdt/pojavlaunch/Tools.java Tools.patch
patch ./Amethyst-Android/app_pojavlauncher/src/main/java/net/kdt/pojavlaunch/tasks/MinecraftDownloader.java MinecraftDownloader.patch

# Build
cd Amethyst-Android
./gradlew :app_pojavlauncher:assembleDebug
```

The built APK will be at: `Amethyst-Android/app_pojavlauncher/build/outputs/apk/debug/app_pojavlauncher-debug.apk`

## Credits

- [Amethyst](https://github.com/AngelAuraMC/Amethyst-Android) by AngelAuraMC
- [Amethyst-Offline](https://github.com/DumDum192/Amethyst-Offline) by DumDum192 (patch reference)
- Based on [PojavLauncher](https://github.com/PojavLauncherTeam/PojavLauncher)
