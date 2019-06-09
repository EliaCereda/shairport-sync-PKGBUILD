# Arch Linux package files for Shairport Sync

This package builds and optionally installs Shairport Sync on Arch Linux. It also creates a user and group to allow Shairport Sync to run as a daemon with the lowest possible privileges.

**Usage**

First, you should update your system and include basic development tools and `git`.
```
# pacman -Syu
# pacman -S --needed base-devel
# pacman -S --needed git
```
To use this script, you need to be logged in as a non-root user with `sudo` privileges. The default `alarm` user is a member of the `wheel` group, but the `wheel` group must be enabled to activate `sudo`. To enable it, as the `root` user, use `visudo` to find and uncomment the line:

```
#%wheel ALL=(ALL) ALL
```
so that it reads:
```
%wheel ALL=(ALL) ALL
```
If you are logged in as user `alarm`, you should now log out and log in again.

Next, download the package:
```
$ git clone https://github.com/mikebrady/shairport-sync-for-arch-linux.git
```

Move into the resulting directory:
```
$ cd shairport-sync-for-arch-linux
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

The default non-root user `alarm` is not a member of the `audio` group, so it can not see or access any audio devices. To allow it to see and access audio devices, it must be added to the group `audio`:

```
# usermod -a -G audio alarm
```

When Shairport Sync has been installed and tested successfully, you may delete the `shairport-sync-for-arch-linux` directory and its contents, as they are no longer needed.
