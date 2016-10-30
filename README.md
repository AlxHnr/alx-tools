A collection of scripts and hacks i have written over the years, mostly for
maintaining my Gentoo system. This is free software, released into the
public domain. See the LICENSE file for more informations.

These tools can be installed directly from my
[Gentoo overlay](https://github.com/AlxHnr/gentoo-overlay).

## Provided tools

Most of these tools have no configuration file and must be configured by
modifying their source code.

### build-kernel

Builds and updates kernels. It will automatically migrate kernel
configurations and reinstall modules. If `/etc/efikeys` exists and contains
the files _db.key_ and _db.crt_, they will be used for signing the kernel.

**Note**: This script assumes that your kernel can boot itself and will
install it to `/boot/efi/boot/bootx64.efi` after mounting `/boot`.

### remove-kernel-residue

Removes all kernel files and modules, which are not needed anymore and do
not belong to any installed package.

### ppack

Creates project archives. It will append the timestamp of either the newest
file or the latest commit to the archive name. Only git is supported. If
git is not installed, it will fallback to searching the most recent file.

### nb-sync

Synchronizes two [nano-backup](https://github.com/AlxHnr/nano-backup)
repositories.

Usage:

```sh
nb-sync current/ to old/
```

### sync-overlay-with-projects

Renames the ebuilds in your overlay to match the git tags of your projects.
It will also update the manifests and commit and push the changes.

For this to work, the following conditions must be met:

* The overlay must contain an ebuild with a version suffix other than
  "-9999". If it contains two ebuilds that fulfill this requirement, e.g.
  "-0.1.0" and "-0.1.1", it will pick one of them and may overwrite the
  other.
* The archive in the ebuilds SRC\_URI must be available for download. It
  must have a name like "foo-0.1.0.tar.gz" after being fetched via portage.
* The projects name must be the same as its packages name.
* The projects working tree must be at the exact state of the tag to which
  the ebuild should be renamed to. This is required to assert that the
  files in the distributed archive have not been tampered with, before
  generating its manifest.

##### Usage example

If you have your overlay in the same directory as your project:

```
~/Projects/my-overlay/category/package-name/...-0.1.0.ebuild
~/Projects/package-name/... (Currently at v0.1.1)
```

You just need to cd into the overlays root directory and run this script:

```sh
cd ~/Projects/my-overlay
sync-overlay-with-projects
```

### clear-colors-getty

My Vim [colorscheme](https://github.com/AlxHnr/clear_colors) for the TTY.

### print-gentoo-splash

Prints a centered Gentoo logo in various colors.
