This is notes on the following book:

http://file.allitebooks.com/20160412/Learning%20Raspbian.pdf

---

**Download raspbian**

go to [http://www.raspberrypi.
org/downloads/](http://www.raspberrypi.
org/downloads/)

**Install using Linux**

- `sudo -i`
- `df -h`
- `umount /dev/sdb1` _replace with sd dir_
- `cd Desktop`
- `dd bs=1m if=2014-06-20-wheezy-raspbian.img of=/dev/sdb1` _replace distro version and sd dir_

**Start software configuration tool**

- `raspi-config`
- use this to resize root filesystem, change default password, boot to scratch lang, change keyboard, enable camera, enable SSH

**Register pi with community**

It can be added to [rastrack](http://rastrack.co.uk), which will publish the physical location to the world.

**Explanation of filesystem**
- `/` _root_
- `/bin` _boot programs_
- `/dev` _devices_
- `/etc` _config_
- `/home` _user-specific_
- `/lib` _shared code_
- `/mnt and /media` _connected filesystems_
- `/opt` _etc_
- `/proc` _kernal_
- `/sbin` _admin_
- `/tmp` _temporary_
- `/usr` _user home_
- `/var` _logs_
- `/root` _root-specific_
- `/boot` _boot config_

**Multiple desktops**

use openbox configuration manager


**Connecting to Ethernet network**

- `sudo nano /etc/network/interfaces`
- change the `iface` line to the following lines:  
```txt
auto eth0
iface eth0 inet static
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
```
- `sudo service networking restart`

**Connecting to wifi**

see a list of working dongles [here](http://elinux.org/RPi_VerifiedPeripherals)

Plug in the dongle when the pi is turned off.

**Included software**

[sonic-pi](http://sonic-pi.net) music synthetizer

IDLE Python IDE

[Scratch](http://scratch.mit.edu) animation/game creator

Raspberry Pi (app) Store

Mathematica

**Installing software**

APT-archives: _main_, _contrib_, _non-free_

with `build_essentials` _./configure_ (creates Makefile), _make_ (compiles), and _make install_

Update with `apt-get update` and `apt-get upgrade`

**Record video**

`cat /dev/video0 > video.file`

**BASH file manipulation**

- ls
  - `-a` show hidden
  - `-l` verbose
  - `-h` human-readable
- cat
  - `-n` show line numbers
  - `-E` add $ to EOL
- cp
  - `-r` recursive
  - `-f` force overwrite
  - `-p` preserve owner/timestamp
  - `-v` verbose
- mv
  - `-f` force overwrite
  - `-u` overwrite if newer
- rm
  - `-f` force (no confirmation)
  - `-i` confirm each deletion
  - `-r` recursive
- mkdir
  - `-p` create parent directories
  - `-v` verbose
- `cat /etc/passwrd` shows all users
- `cat /etc/group` shows all groups
- `sudo passwrd` to set initial password
- chown
  - `-R` recursive
  - `-v` verbose
- chmod
  - `-R` recursive
  - `-v` verbose
  - `-c` show changes
  - owner / group / all users
  - 0: no permissions
  - 1: execute
  - 2: write
  - 3: write and execute
  - 4: read
  - 5: read and execute
  - 6: read and write
  - 7: read, write, and execute

**Rebooting**

- `reboot`
- `shutdown`
  - `-r` reboot
  - `-h` power off
  - `-k` don't really shut down
- i.e. `shutdown -h now`
- `halt`

**Other distros**

- [raspbmc](http://www.raspbmc.com) for media playback
- [volumio](http://volumio.org) for music
- [thinbox](http://www.jontylovell.net/index.php?page=30) minimal remote desktop
- [piplay](http://pimame.org) for emulating old games
- [torberry](https://code.google.com/p/torberry) for running tor
- [kali](http://kali.org) for pentesting