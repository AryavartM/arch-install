# arch-install

A highly configurable script installing
[Arch Linux](https://www.archlinux.org/).

*(work in progress)*

## Feature Highlights

* Fully automated installation of a ready-to-use [Arch Linux](https://www.archlinux.org/) system
* Installation to any device, including USB sticks
* Supports both BIOS (legacy) and EFI boot methods
  * for BIOS: `grub` boot loader
  * for EFI: choose between `grub` or the `gummiboot` boot loader
* Installation of an LVM-on-LUKS encrypted system (also on USB sticks!)
* `yaourt` installation to install [AUR packages](https://aur.archlinux.org/) right away
* X11 installation
* Optionally install Ubuntu's font rendering (much smoother!)
* [Xfce](http://www.xfce.org/) installation, including some nice themes and icons
* Graphical user login using LightDM
* Installation of individually configurable software package sets, already
including
  * [Chrome](https://www.google.de/chrome/browser/desktop/), [Firefox](https://www.mozilla.org/firefox/), [Thunderbird](https://www.mozilla.org/thunderbird/), [Skype](http://www.skype.com/), [TeamViewer](https://www.teamviewer.com/)
  * [GIMP](http://www.gimp.org/), [gThumb](https://wiki.gnome.org/Apps/gthumb), [Shutter](http://shutter-project.org/), [Kazam](https://launchpad.net/kazam)
  * [FileZilla](https://filezilla-project.org/), [Tor](https://www.torproject.org/)
  * [Audacity](http://web.audacityteam.org/), [Banshee](http://banshee.fm/), [VLC](http://www.videolan.org/), [Spotify](https://www.spotify.com/)
  * ...

It's best you look into the configuration file `arch-install.conf` -- almost
everything is configurable...

## Quick Start

*(For a more detailed usage guide scroll down.)*

Boot the [Arch Linux ISO image](https://www.archlinux.org/download/) and type
in:

```
pacman -Sy --noconfirm --needed git
git clone https://github.com/wrzlbrmft/arch-install.git
arch-install/arch-install.sh
```

After a while, `reboot` and enjoy!

## Usage Guide

Start by downloading(, burning) and booting the latest
[Arch Linux ISO image](https://www.archlinux.org/download/).

After the auto-login as `root`, you can load an alternative keyboard layout,
e.g. *German*:

```
loadkeys de-latin1
```

(on German keyboards: for `y` press `z`, for `-` press `ß`)

Make sure you have a working internet connection:

```
ping -c 3 8.8.8.8
```

To connect to a wireless network use:

```
wifi-menu
```

Next, install `git` and checkout the `arch-install` repository:

```
pacman -Sy --noconfirm --needed git
git clone https://github.com/wrzlbrmft/arch-install.git
```

You may want to change the default configuration:

```
nano -w arch-install/arch-install.conf
```

see also: *Configuration/Most Important Settings*

Finally, start the installation process:

```
arch-install/arch-install.sh
```

**NOTE:** For both the `root` and main user, and also if you enabled the
LVM-on-LUKS encryption, you will have to type in some passwords during the
installation process.

Depending on your computer and internet connection speed, the installation takes
45-60 minutes (downloading approx. 1.2 GB).

The installation is done, once you see

```
[arch-install] Wake up, Neo... The installation is done!
```

Finally, reboot your machine:

```
reboot
```

That's it!

## Configuration

*I will add comments to arch-install.conf soon...* :-)

### Most Important Settings

#### INSTALL_DEVICE

*Default:* `/dev/sda`

Definitely the most important setting: where to install
[Arch Linux](https://www.archlinux.org/).

#### BOOT_METHOD

*Value:* `legacy` (default) or `efi`

Boot method to be used: `legacy` for BIOS boot, `efi` for EFI/UEFI boot. This
affects the boot loader configuration.

#### LVM_ON_LUKS

*Value:* `yes` or `no` (default)

Whether to install an LVM-on-LUKS encrypted system.

#### ADD_MAIN_USER

*Value:* `yes` (default) or `no`

Whether to add a main user. If set to `yes`, have a look at the
`MAIN_USER_USERNAME` and `MAIN_USER_REALNAME` settings.

#### MAIN_USER_USERNAME, MAIN_USER_REALNAME

If `ADD_MAIN_USER` is set to `yes`, a main user will be created. Use these two
settings to configure user name and real name.

### Using an Alternative Configuration File

You can use an alternative configuration file by passing it to the installation
script:

```
arch-install/arch-install.sh -c my.conf
```

## License

This software is distributed under the terms of the
[GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.en.html).
