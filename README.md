A collection of scripts and hacks i have written over the years, mostly for
maintaining my Gentoo system. This is free software, released into the
public domain. See the LICENSE file for more informations.

## Provided tools

Most of these tools have no configuration file and must be configured by
modifying their source code.

### update-system

Updates the entire system, including the kernel and various config files.
It performs some additional cleanups.

### build-kernel

Builds and updates kernels. It will automatically migrate kernel
configurations and reinstall modules.

**Note**: This script assumes that your kernel can boot itself and will
install it to `/boot/efi/boot/bootx64.efi`. It will also mount `/dev/sda1`
to `/boot` during installation.

### remove-kernel-residue

This script removes all kernels and modules, which are not used anymore and
do not belong to any package.

### print-gentoo-splash

Prints a centered Gentoo logo in various colors.
