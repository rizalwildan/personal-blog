---
title: "Arch Linux Gaming #101"
date: 2022-08-09T10:35:04+07:00
draft: false
tags: [Cheat Sheet, ArchLinux]
---

## Requirements

### 1. Check if your GPU supports vulkan

Search for your GPU in the [database](http://vulkan.gpuinfo.org/)

- If there’s an entry you’re good to go!
- Not on the list? That means your GPU is too old to support Vulkan. Without it, DXVK won’t work and performance and compatibility will be worse. However you still can game;
  - Skip next steps: 3. Install Vulkan and 4. Install Vulkan driver for your GPU driver.
  - Make sure to disable DXVK/D3DVK globally in Lutris and Steam.

### 2. Install vulkan

```
vulkan-icd-loader
lib32-vulkan-icd-loader
```

### 3. Install GPU specific Vulkan

Nvidia

```
nvidia-utils
lib32-nvidia-utils
```

AMD AMDVLK

```
amdvlk
lib32-amdvlk
```

AMD RADV

```
vulkan-radeon
lib32-vulkan-radeon
```

Intel

```
vulkan-intel
lib32-vulkan-intel
```

## Aditional software

(GameMode)[https://github.com/FeralInteractive/gamemode] is a daemon that automatically optimizes your system while playing games.

```
pacman -S gamemode
```

(MangoHud)[https://github.com/flightlessmango/MangoHud] is an in-game overlay, it can display useful information and cap FPS.

```
yay -S mangohud
```

(ProtonUp-Qt)[https://davidotek.github.io/protonup-qt/] is a GUI tool to manage different versions of GE Proton.

```
yay -S protonup-qt
```

## Glossary

### Common terms

| terms                           |                                                                                                                           Description                                                                                                                           |
| :------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| PREFIX / WINEPREFIX             |                                                                        Separate directory inside your Linux, which represents a “Windows” machine, it’s drives, folders, registry, etc.                                                                         |
| Engine / (Wine / Proton)        |                                                                                  Allows you to run Windows programs on Linux, Downgrade / update engine version for any PREFIX                                                                                  |
| ARCH                            |                                                  Architecture of PREFIX is win64 or win32 based on chosen Engine You can use only one ARCH for PREFIX since it’s created, in most cases you should use win64!                                                   |
| dll override / WINEDLLOVERRIDES | It’s not always possible to run an application on builtin DLLs. Sometimes native DLLs simply work better. You can override any dll in your PREFIX, these DLL overrides can be set using winecfg or use the `WINEDLLOVERRIDES` environment variable to set them. |
| Winetricks / Protontricks       |                                                     Very important tool in your arsenal to tweak PREFIX and overcome some known problems, or install Windows libraries, to cover unfinished parts of Wine.                                                      |
| DXVK                            |                                                                         Vulkan-based translation layer for DirectX 9 / 10 / 11 Probably the most important project for gaming on Linux!                                                                         |
| VKD3D                           |                                                                                                   Aims to implement the full DirectX 12 API on top of Vulkan.                                                                                                   |
| Esync                           |                                                      Removes wineserver overhead for synchronization objects. This can increase performance for some games, especially ones that rely heavily on the CPU.                                                       |
| Fsync                           |                                                           More recent alternative with even better performance improvements, then Esync. However, you do need an Engine and Kernel that supports it.                                                            |
