---
date: 2018-07-30
title: Enable OTA upgrade in earlier FydeOS versions
categories:
  - 使用技巧
type: Document
permalink: /recipes/enable-ota-in-earlier-fydeos-releases/
redirect_from:
  - /使用技巧/在早期FydeOS版本中启用OTA升级/
lang: en
---

> Note: This tutorial assumes that you are not new to Linux command line operations and have the most basic operating skills. If you find the following content difficult to understand, please seek the help of your friends or upgrade your FydeOS with [Direct Programming](https://fydeos.com/instructions-pc).

> This tutorial is for early versions of FydeOS that have not activated OTA upgrades, including FydeOS for PC dev v4.0, v3.41, v3.4 and v3.3. If the version of FydeOS you are using is newer than the above version number, this tutorial is not applicable. Your FydeOS is already equipped with an OTA upgrade by default.

## 0. Preparation

__Please note that only after installing FydeOS into the hard disk can the OTA upgrade be enabled according to this tutorial, and the OTA upgrade cannot be performed through the USB flash drive experience!__

Please refer to [this full-disk installation tutorial](/en/getting-started/install-fydeos-to-hdd/) or [multi-boot installation tutorial](/en/recipes/dual-boot/) to install FydeOS for PC into the hard disk of the target PC and Successfully enter the graphical interface of FydeOS.


## 1 Enter Bash Shell

Refer to [this tutorial](/en/getting-started/shell-access/) to enter the Bash Shell environment and obtain root permissions.


## 2. Run the command

Please follow the line-by-line input strictly: <br>
(If possible, please copy and paste directly one by one-paste the following command to enter the command line. __Tip: By default, in the web version of Crosh Shell, you only need to right-click the blank space to paste the contents of the clipboard To the current cursor.__):

```bash
mount -o remount rw /
cat >> /etc/lsb-release <<EOF
CHROMEOS_RELEASE_APPID={49BA18F3-93DB-4F43-B966-3BBC57881C42}
CHROMEOS_BOARD_APPID={49BA18F3-93DB-4F43-B966-3BBC57881C42}
EOF
```

## 3. Check

Enter:
```bash
cat /etc/lsb-release
```
Then check whether the following items in the screen output contain `CHROMEOS_RELEASE_APPID` and `CHROMEOS_BOARD_APPID`, and the values ​​of the two items are strictly equal:
```
{49BA18F3-93DB-4F43-B966-3BBC57881C42}
```
_Note: Please be sure to check carefully, if any character error occurs, it will not be able to upgrade via OTA. If you find that the input is incorrect, you can modify the `/etc/lsb-release` file through the `vim` editor._


## 4. Start the upgrade

After executing the command, you can go to the browser "Customize and Control Chromium" menu -> "About FydeOS" -> click "Check for updates" to start the upgrade mechanism. If an upgrade exists, the system will automatically start the upgrade process. At this point, you can continue your work as much as possible. The upgrade process only consumes traffic and does not affect system performance. The installation package is relatively large and requires a certain amount of time to download. Please be patient. After the upgrade is complete, you only need to restart the system according to the screen prompts to automatically switch to the latest version of FydeOS.
