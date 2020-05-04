---
date: 2018-07-16
title: Install FydeOS for PC into the hard disk (full disk installation)
categories:
  - 起步走
type: Document
permalink: /getting-started/install-fydeos-to-hdd/
redirect_from:
  - /使用技巧/将FydeOS-for-PC安装进硬盘（全盘安装）/
lang: en
---

> Note! Installing FydeOS on the hard drive will erase all data on the hard drive. This feature is still in the testing stage, we can not be responsible for potential data loss and various problems that may occur in the installation or provide timely technical support. Please think twice!
In addition, in the latest version of FydeOS for PC, we provide a graphical installation program that you can install and use in the "FydeOS App Store". If the program does not work, try the following tutorial.

## 0. Boot and start FydeOS for PC via USB

Please refer to [this tutorial](https://fydeos.com/instructions-pc/) to make a FydeOS for PC that can be booted and successfully boot into the graphical interface of FydeOS on the target PC.

## 1. Enter the terminal

After the FydeOS for PC graphical interface appears, please press the `Ctrl` + `Alt` + `F2` key on the keyboard (on some computers, such as Apple Mac, you need to press `Fn` + `Ctrl` + `Alt` + `F2`, then the system will automatically switch to TTY command line mode. If necessary, press `Ctrl` + `Alt` + `F1` (or `Fn` + `Ctrl` + `Alt` + `F1`) Return to the graphical interface mode.

## 2. Log in to the system

FydeOS will prompt you to enter your username and password in command line mode. In FydeOS for PC, the default user name is `chronos`, the user has no password by default, and after entering the command line, it will enter the developer mode.

## 3. Confirm the target disk

Enter the command `lsblk` to get the list of currently loaded physical disks. Normally, the physical hard disk in your PC will be displayed in the form of `sdX`. According to the prompted disk space size and the number of partitions, please determine the physical disk letter of FydeOS, such as `sda`. The following command will take `sda` as an example.

## 4. Run the installation script

input the command:

```
sudo /usr/sbin/chromeos-install --dst /dev/sda
```

The installation script will finally confirm whether you want to continue and prompt that if you continue, the target disk will be emptied. If you are sure, please enter `Y` and press Enter to confirm.

## 5. Wait for the script to run

Make a cup of coffee and watch an American drama.

## 6. After running the script

If prompted, please remove the USB drive, restart the computer, and pray that all of the above have been successful. Good luck.
