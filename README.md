#Arch Linux package files for Shairport Sync

This package builds and optionally installs Shairport Sync on Arch Linux. It also creates a user and group to allow Shairport Sync to run as a daemon with the lowest possible privileges.

**Usage**

Download the package:
```
$git clone https://github.com/EliaCereda/shairport-sync-PKGBUILD.git
```

Move into the resulting directory:
```
$cd shairport-sync-PKGBUILD
```

Excute the following command:
```
$makepkg -sfi
```
to install dependencies (`-s`), download, build and install (`-i`) Shairport Sync, always (`-f`).
You will need to have `sudo` privileges and you will be asked to enter your password during installation. Do not try to run this script as `root`.

Please refer to the ["Configuring Shairport Sync"](https://github.com/mikebrady/shairport-sync/blob/master/README.md#configuring-shairport-sync)
for information on how to configure Shairport Sync.
