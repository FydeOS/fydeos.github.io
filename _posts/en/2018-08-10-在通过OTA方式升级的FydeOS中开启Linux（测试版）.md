---
date: 2018-07-30
title: Open Linux (beta) in FydeOS upgraded by OTA
categories:
  - 使用技巧
  - crostini
type: Document
permalink: /recipes/enable-crostini-after-ota-update/
redirect_from:
  - /使用技巧/crostini/在通过OTA方式升级的FydeOS中开启Linux-测试版/
lang: en
---

This tutorial is aimed at users who have upgraded to v4.2 and newer via OTA and have not successfully started Linux (beta) before.

FydeOS can be started directly by booting from a USB flash drive or newly installed into the hard disk. It does not require additional settings and is not applicable to this tutorial.

## 0. Preparation

This article assumes that you have upgraded the early FydeOS version to v4.2 or later through OTA. The version of FydeOS can be viewed in "More" -> "About FydeOS" - "Detailed Version Information" on the right side of the browser. For example: `10718.78.1.3 (Release Build v4.2 stable-channel amd64-fydeos)` means that this is the release version of FydeOS v4.2.

This article also assumes that your system did not successfully start Linux (beta) before the upgrade.


## 1. Download the file

Download [this file](https://download.fydeos.io/tatl-fydeos.tar.gz) in FydeOS browser, after downloading, you get a compressed package named `tatl-fydeos.tar.gz` file.


## 2. Enter Shell

Refer to [this tutorial](/en/getting-started/shell-access/) to enter the Bash Shell environment.


## 3. File operations

Refer to the following command to move the downloaded `tatl-fydeos.tar.gz` to the `/mnt/stateful_partition/dev_image/` directory, decompress it and restart.

```bash
cd ~/Downloads
sudo cp ./tatl-fydeos.tar.gz /mnt/stateful_partition/dev_image/
sudo su -
cd /mnt/stateful_partition/dev_image/
tar -zxvf tatl-fydeos.tar.gz
rm -rf tatl-fydeos.tar.gz
reboot
```

## 4. Open Linux (beta)

Enter the "Settings" interface and scroll to the bottom, find "Linux (Beta)", and click "Enable".


## 5. Matters needing attention

 - It takes a long time to activate Linux (beta) components for the first time, ranging from about 15 minutes to half an hour, depending on the computer configuration and network environment.
 - If you have tried to open Linux (beta) in v4.1 version and it is not successful, you can still follow this tutorial to provide the required files to the system. After completing the file operation, click on the "Termnial" program and try to start it.
 - If there is still an error, you can try to download the latest version of FydeOS for PC image file and re-burn and install the built-in Linux (beta) required dependencies. Or, execute [Powerwash](https://faq.fydeos.com/en/recipes/powerwash/) to clear user files before performing this tutorial.
