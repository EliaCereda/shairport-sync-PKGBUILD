# Arch Linux package files for Shairport Sync

This package builds and optionally installs Shairport Sync on Arch Linux. It also creates a user and group to allow Shairport Sync to run as a daemon with the lowest possible privileges.

**Usage**

Download the package:
```
$ git clone https://github.com/mikebrady/shairport-sync-PKGBUILD.git
```

Move into the resulting directory:
```
$ cd shairport-sync-PKGBUILD
```

Execute the following command:
```
$ makepkg -sfi
```
to install dependencies (`-s`), download, build and install (`-i`) Shairport Sync, always (`-f`).
You will need to have `sudo` privileges and you will be asked to enter your password during installation. Do not try to run this script as `root` or superuser.

An existing configuration file at `/etc/shairport-sync.conf` will not be overwritten.

Please refer to the ["Configuring Shairport Sync"](https://github.com/mikebrady/shairport-sync/blob/master/README.md#configuring-shairport-sync)
for information on how to configure Shairport Sync.

**Automatic Startup**

To enable Shairport Sync to start automatically as a service upon startup, enter the following command from the superuser mode:
```
# systemctl enable shairport-sync
```
Reboot for it to take effect.

**Note**

BTW, the default non-root user `alarm` is not a member of the `audio` group, so it can not see or access any audio devices. To allow it to see and access audio devices, it must be added to the group `audio`:

```
# usermod -a -G audio alarm
```

