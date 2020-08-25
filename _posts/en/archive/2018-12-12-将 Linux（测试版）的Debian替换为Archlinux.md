---
date: 2018-12-12
title: Replace Debian for Linux (beta) with Arch Linux
categories:
  - tips
  - crostini
type: Document
permalink: /recipes/install-arch-linux/
redirect_from:
  - /使用技巧/crostini/将Linux-测试版-的Debian替换为Arch-Linux/
lang: en
---

# 0. Known issues

Linux support is in the beta stage. Depending on your specific hardware configuration, the components required by Linux (beta) have a certain probability of failing to start.


# 1. Enter Termina and install the container

Use `Ctrl` + `Alt` + `t` to open and open `crosh`, enter `vmc start termina` in it to start the `Termina` virtual machine.

```
crosh> vmc start termina
(termina) chronos@localhost ~ $
```

`lxc list` lists the installed containers:

```
(termina) chronos@localhost ~ $ lxc list
+---------+---------+-----------------------+------+------------+-----------+
| NAME    | STATE   | IPV4                  | IPV6 | TYPE       | SNAPSHOTS |
+---------+---------+-----------------------+------+------------+-----------+
| penguin | RUNNING | 100.115.92.202 (eth0) |      | PERSISTENT | 0         |
+---------+---------+-----------------------+------+------------+-----------+
```

Use the `run_container.sh` command to download and install the `Arch Linux` container. Since FydeOS modified this command relative to Chromium OS, edit this script to undo the changes. Since termina is read-only, copy the script to the temporary directory `/tmp`:

```
cp /usr/bin/run_container.sh /tmp
cd /tmp
vim run_container.sh
```

Find the following snippet:

```bash
# lxc init "google:${FLAGS_lxd_image}" "${FLAGS_container_name}" || \
#   die "Unable to create container from image '${FLAGS_lxd_image}'"
local container_root="/usr/share/intergrade_container"
local lxd_info="${container_root}/lxd.tar.xz"
local root_file="${container_root}/rootfs.squashfs"
local container_alias="intergrade_fydemina"
lxc image import $lxd_info $root_file --alias $container_alias || \
    die "Unable to import image from $root_file"
lxc init $container_alias ${FLAGS_container_name} || \
    die "Unable to create container from image $container_alias"
```

change into:

```bash
lxc init "google:${FLAGS_lxd_image}" "${FLAGS_container_name}" || \
    die "Unable to create container from image '${FLAGS_lxd_image}'"
```

Run the following command, please make sure the username is the username displayed in the **Settings** app. You can choose the container name specified by `container_name`, the Linux image specified by `lxd_image`, or the image source specified by `lxd_remote`.

```
bash ./run_container.sh --container_name arch --user 你的用户名 --lxd_image archlinux/current --lxd_remote https://mirrors.tuna.tsinghua.edu.cn/lxc-images/
```

Make sure that the download is successful and the user creation is successful (ignoring the few errors that cannot join the user group).


# 2. Enter the command line of the container

##### Execute the command line of the container:

```
(termina) chronos@localhost /tmp $ lxc exec arch -- bash
[root@arch ~]#
```

##### Execute the following command in the container:

```bash
# Set password. Never set a password for root, otherwise the Chromium OS integration service will not run
passwd <your_username>
# Add user to wheel group
usermod -aG wheel <your_username>
```

##### Set the source, cut and paste tuna ustc 163 and other Chinese sources to the front (cut the entire line of `dd` in the vi editor, `p` paste, `/` search):

```bash
vi /etc/pacman.d/mirrorlist
```

##### Set archlinuxcn source:

```bash
vi /etc/pacman.conf
```

##### Insert at the end:

```ini
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```

##### Installation dependencies:

```bash
pacman -Syu archlinuxcn-keyring base-devel git gtk3 openssh xdg-utils xkeyboard-config
```

Enable sudo without password, execute

```bash
visudo
```

##### Delete the comment before the following line:

```ini
%wheel   ALL=(ALL:ALL) NOPASSWD: ALL
```

##### Exit to termina:

```bash
exit
```

# 3. Log in to the container

**Login** to the user you created (previously, the method of executing bash was not login, unable to load the service).

Run `lxc console arch`, then enter the user name directly:

```
(termina) chronos@localhost /tmp $ lxc console arch
[<your-username>@arch ~]$
```

After successful login, install `cros-container-guest-tools-git` on aur. Since you need to download files from `chromium.googlesource.com`, please solve network problems yourself. Note that the proxy settings in the Android subsystem or Chromium OS will not be applied to the virtual machine.

```bash
git clone https://aur.archlinux.org/cros-container-guest-tools-git.git
cd cros-container-guest-tools-git
makepkg -i
#Solve the problem that the .config does not exist and the default browser is not set
mkdir ~/.config
xdg-settings set default-web-browser garcon_host_browser.desktop
```

Solve the problem that the update of `xkeyboard-config` in Arch Linux results in` Sommelier` not supporting two key codes
Open `/usr/share/X11/xkb/keycodes/evdev`, comment or delete the two lines starting with `<i372>` and `<i374>`.

`cros-container-guest-tools-git` is applied to the latest version of Chromium OS. FydeOS has not been updated to R71 yet and does not support `x-auth` function. Therefore, the file needs to be modified (no need to change after the update).

Open `/usr/lib/systemd/user/sommelier-x@.service` and find the following snippet:

```bash
ExecStart=/opt/google/cros-containers/bin/sommelier \
              -X \
              --x-display=%i \
              --sd-notify="READY=1" \
              --no-exit-with-child \
              --x-auth=${HOME}/.Xauthority \
              /bin/sh -c \
                  "systemctl --user set-environment ${DISPLAY_VAR}=$${DISPLAY}; \
                   systemctl --user set-environment ${XCURSOR_SIZE_VAR}=$${XCURSOR_SIZE}; \
                   systemctl --user import-environment SOMMELIER_VERSION; \
                   touch ${HOME}/.Xauthority; \
                   xauth -f ${HOME}/.Xauthority add ${HOST}:%i . $(xxd -l 16 -p /dev/urandom); \
                   . /etc/sommelierrc"
```

To

```bash
ExecStart=/opt/google/cros-containers/bin/sommelier \
              -X \
              --x-display=%i \
              --sd-notify="READY=1" \
              --no-exit-with-child \
              /bin/sh -c \
                  "systemctl --user set-environment ${DISPLAY_VAR}=$${DISPLAY}; \
                   systemctl --user set-environment ${XCURSOR_SIZE_VAR}=$${XCURSOR_SIZE}; \
                   systemctl --user import-environment SOMMELIER_VERSION; \
                   . /etc/sommelierrc"
```

Enable all systemd services included with `cros-container-guest-tools-git`

```bash
sudo systemctl enable cros-sftp
systemctl --user enable sommelier@0.service
systemctl --user enable sommelier@1.service
systemctl --user enable sommelier-x@0.service
systemctl --user enable sommelier-x@1.service
systemctl --user enable cros-garcon.service
```

# 4. Rename the container

Due to some limitations, currently FydeOS Linux (beta) can only be enabled by integrating a container named `penguin`. Therefore, you need to rename the container (do not delete the Debian container):

```bash
[<your-username>@arch ~]$ exit
#Press ctrl-A Q
(termina) chronos@localhost /tmp $ lxc stop arch
(termina) chronos@localhost /tmp $ lxc stop penguin
(termina) chronos@localhost /tmp $ lxc rename penguin debian
(termina) chronos@localhost /tmp $ lxc rename arch penguin
```

Restart the virtual machine:

```bash
sudo reboot
```


# 5. Localization

Open the terminal application, wait a few seconds, Arch Linux starts, and then do some localization:

##### Set the time zone:

```
sudo timedatectl set-timezone Asia/Shanghai
```

##### Set the Chinese language:

Edit `/etc/locale.gen` and delete the comment before `zh_CN.UTF-8`. Then execute

```bash
sudo locale-gen
```

Modify `/etc/locale.conf`:

```bash
LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN.UTF-8"
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
```


##### Install fonts, input methods, and Sogou input methods are also installed here, bugs may occur, please choose as appropriate.

```bash
sudo pacman -S fcitx-im fcitx-configtool fcitx-sogoupinyin wqy-microhei
```

Open `/usr/lib/systemd/user/cros-garcon.service.d/cros-garcon-override.conf`

Insert:

```bash
Environment="GTK_IM_MODULE=fcitx"
Environment="QT_IM_MODULE=fcitx"
Environment="XMODIFIERS=@im=fcitx"
```

Execute:

```bash
echo /usr/bin/fcitx-autostart > $HOME/.sommelierrc
```

Restart the container:

```bash
sudo reboot
```

Run `fcitx-config-gtk3` to configure the input method.


# Reference

[https://www.reddit.com/r/Crostini/wiki/howto/run-arch-linux](https://www.reddit.com/r/Crostini/wiki/howto/run-arch-linux)
