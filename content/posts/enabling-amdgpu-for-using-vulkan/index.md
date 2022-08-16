---
title: "Enabling Amdgpu for Using Vulkan with R7 and R9 Radeon Cards"
date: 2022-08-09T11:23:54+07:00
draft: false
tags: [Cheat Sheet, ArchLinux]
---

| Card Family      | Models                                                 | Module Parameter     |
| ---------------- | ------------------------------------------------------ | -------------------- |
| Southern Islands | HD7750-HD7970, R9 270, R9 280, R9 370X, R7 240, R7 250 | amdgpu.si_support=1  |
| Sea Islands      | HD7790, R7 260, R9 290, R7 360, R9 390                 | amdgpu.cik_support=1 |

First, determine which kernel driver is currently in use:

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

If your Kernel driver in use result says amdgpu you’re working, there’s nothing for you to do except install Vulkan (if that’s your goal). If your result says radeon, read on.

1. Install the amdgpu driver, along with Vulkan (both x64 and x86):

```
sudo pacman -S amdvlk lib32-amdvlk vulkan-icd-loader lib32-vulkan-icd-loader
```

2. The GRUB Bootloader needs to be modified to (a) disable the ‘radeon’ driver for your card and (b) enable the module parameter for amdgpu. Edit `/etc/default/grub` append one of the following inside the quotes on the `GRUB_CMDLINE_LINUX` line:

   - For Southern Island cards: `radeon.si_support=0 amdgpu.si_support=1`
   - For Sea Island cards: `radeon.cik_support=0 amdgpu.cik_support=1`

3. Build the GRUB config
   - For EFI systems:
   ```
   sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
   ```
   - For BIOS systems:
   ```
   sudo grub2-mkconfig -o /boot/grub2/grub.cfg
   ```
4. Reboot

For additional information, refer to the [Arch](https://wiki.archlinux.org/title/AMDGPU) wikis.
