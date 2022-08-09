---
title: "Pacman Basic Commands"
date: 2022-08-09T09:14:46+07:00
draft: false
tags: [Cheat Sheet, ArchLinux]
---

## Updating the system

```
sudo pacman -Syu
```

## Searching for packages

```
pacman -Ss package_name
```

_\*for searching and installing packages in the AUR we refer to the [yay](https://aur.archlinux.org/packages/yay)_

## Installing packages

```
sudo pacman -S package_name
```

_You can also use this command to install several packages by just hitting the space bar after the first package name and enter the other package name(s)._

## Installing package groups.

```
sudo pacman -S plasma
```

```
Enter a selection (default=all): 1-15 20
```

In this case it will install packages 1 through 15 and package number 20.

```
Enter a selection (default=all): ^5-8 ^15
```

This will install everything that belongs to the DE group, except packages 5 through 8 and package number 15.

## Removing packages

To remove a package without the dependencies use the following command.

```
sudo pacman -R package_name
```

If you rather want to avoid a cluttered system you can remove a package and its dependencies, without removing dependencies that are used by other installed packages, use the following command.

```
sudo pacman -Rs package_name
```

## Refreshing mirrors

```
sudo pacman -Syyu
```

## Skipping package updates

```
sudo nano /etc/pacman.conf
```

Ad the line IgnorePkg = package_name like this.

```
# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup
 #IgnorePkg =
 IgnorePkg = package_name
 #IgnoreGroup =
```

In this case, Pacman will always inform you that there’s an update for a certain package on the Ignore list like this.

```
:: package_name is in IgnorePkg/IgnoreGroup. Install anyway? [Y/n]
```

You can also put an entire group on the ignore list by adding the line `IgnoreGroup = gnome`

To remove the package or group from the ignore list just open the file as described above and remove the added lines, save and close the file, then type the following command.

```
sudo pacman -S package_name
```

The above method will permanently stop the specified package from being upgraded until you remove it from the ignore list

To do this temporarily, you can simply run:

```
sudo pacman -Syu --ignore=package_name
```

This command will skip the package from being updated. Similarly, to skip a package group, just run:

```
sudo pacman -Syu --ignoregroup=gnome
```
