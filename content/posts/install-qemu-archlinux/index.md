---
title: "Install Qemu Archlinux"
date: 2022-08-17T12:49:59+07:00
draft: true
tags: [Cheat Sheet, ArchLinux]
---

## Install Qemu
```
sudo pacman -S qemu-basic
```

## Libvirt

Some of the major libvirt features are: 

- VM management
- Remote machine support
- Storage management
- Network interface management
- Virtual NAT and Route based networking

### Server

Libvirt provides a convenient way to manage QEMU virtual machines.

Installation:

```
sudo pacman -S libvirt
```

for network conectivity, install:

```
sudo pacman -S iptables-nft dnsmasq
```

### Client

virt-manager -- Graphical manager KVM

```
sudo pacman -S virt-manager
```

### Daemon

Enable `libvirtd.service` (which will also enable `virtlogd.socket` and `virtlockd.socket` units, so there is NO need to also enable `virtlogd.service`)

```
sudo systemctl enable libvirtd.service
```
