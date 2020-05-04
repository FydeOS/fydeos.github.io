---
date: 2018-07-30
title: Multi-boot configuration guide for FydeOS (early versions) and other operating systems
categories:
  - 使用技巧
type: Document
permalink: /recipes/legacy-dual-boot/
redirect_from:
  - /使用技巧/FydeOS与其他操作系统多启动配置指南/
lang: en
---

## caveat:
This tutorial only uses the early version of FydeOS (v5.2 and earlier), the program and the involved scripts are no longer updated and maintained. In versions after FydeOS for PC v5.3, we have introduced a new multi-boot solution, see [this tutorial](/recipes/dual-boot/) for details.

<br>


> Note: This tutorial assumes that you are not new to Linux command line operations and have the most basic operating skills. If you find the following content difficult to understand, please seek the help of friends around you or go to [FydeOS Chinese Community](https://community.fydeos.com/) for help.


## 0. Preparation
#### Suitable

This tutorial is suitable for users who want to install FydeOS as a **second system** into the computer, that is, the target device already has a preferred operating system that can run and can complete basic disk operations.

#### System Requirements

 - One 64-bit PC, which needs to support UEFI and start in UEFI mode (CSM mode can be turned on or off).
 - The hard disk is partitioned by GPT, with at least 10GB of free space.
 - **New installation**: The remaining space of the hard disk needs to exist as free space, not an unused partition. In order to avoid data loss caused by accidentally deleting partitions, the installation script will not delete any existing partitions, so it is necessary for the installer to release and prepare enough remaining space by himself.
 - **Upgrade installation**: FydeOS dualboot mode partition is installed on the hard disk, and the capacity of the root partition is not less than the capacity of the root partition of the latest version.


## 1. Make room for FydeOS

You need to make at least 10G of free disk space for FydeOS to be installed. Note that this space must exist as **free space**, not an empty partition of any kind.

#### Windows system
You can directly use the disk manager that comes with the system to shrink the partition, leaving the free space to be installed.

#### macOS system
The Disk Utility tool that comes with the system can shrink the existing partition, but the free space obtained will be automatically divided into an "Untitled" partition. Need to use another partition tool to delete this "Untitled" partition to get free space. This step can be done using fdisk, gdisk, parted and other tools in the shell after starting FydeOS.

#### Linux system
If you will use Linux, you should not need additional instructions: p


## 2. Install your favorite boot manager

If your device does not carry the UEFI boot manager, or you do not want to use the boot manager provided by the system by default, you need to install an additional boot manager program.

Here we recommend [rEFInd](http://www.rodsbooks.com/refind/) maintained by [Roderick W. Smith](mailto: rodsmith@rodsbooks.com). For installing and configuring rEFInd under Windows, please refer to [this tutorial](https://blog.csdn.net/windking21/article/details/50402933); to install and configure rEFInd under macOS, you can refer to [this tutorial](https://blog.csdn.net/xiaoshaxs/article/details/52016628). If the installation script below detects rEFInd, it will automatically add a proprietary icon to FydeOS to highlight its personality.

Of course, [clover](https://sourceforge.net/projects/cloverefiboot/) or [efibootmgr](https://github.com/rhboot/efibootmgr) are also available options.


## 3. Boot FydeOS via USB

Use [this tutorial](https://fydeos.com/instructions-pc/) to put FydeOS into the mobile storage device and use it to boot the system. Make sure that FydeOS is running well on the target device without obvious hardware compatibility issues.


## 4. Enter TTY Shell

**If you have created a local FydeOS account and logged in to the system, please log out of the current user.**

Press the `Ctrl + Alt + F2` key on the keyboard at the same time (on some computers, such as Apple Mac, you need to press` Fn + Ctrl + Alt + F2`, then the system will automatically switch to tty command line mode. If necessary, press `Ctrl + Alt + F1` (or `Fn + Ctrl + Alt + F1`) to return to the graphical interface mode.

Do not use the Crosh Shell in the browser to perform the following operations. Be sure to cut into the TTY Shell with the user logged out to avoid unpredictable disk read and write errors.


## 5. Run the command

<br>
#### Check system information

First, you need to know the name of the hard disk device to be installed with FydeOS. You can use the following command to confirm the system hard disk information such as size, existing partitions, etc. to help confirm.

```bash
sudo fdisk -l
```
or
```bash
sudo blkid
```
The physical hard disk in your PC will be displayed in the form of `sd*`. For most single hard disk systems, it is usually `/dev/sda`, if it is the second hard disk, it is `/dev/sdb`, and so on. If it is an SSD, it may be `/dev/mmcblk0`. The following command will take `/dev/sda` as an example.

<br>
#### Run the installation script

```bash
sudo dual-boot-install -d /dev/sda
```
The installation script will check whether the system meets the requirements, whether the disk partition and remaining space meet the requirements, and then start to create the partition and install the required files.

After the script is run and the installation is completed normally, it will prompt that it is over. Please restart the system, the startup menu will appear during startup, select FydeOS to start.


<br>
#### Precautions
 - In the above command, the parameter is the entire disk, not the partition. This command will use the remaining space you prepared before on the disk you specified to perform partition and installation operations; instead of installing in a partition you specified.
 - The installation script does not help you install the boot manager.
 - Many PCs directly support multi-boot management by BIOS, so no additional boot manager is needed. But rEFIind can provide a more beautiful and customizable graphical interface.
 - As long as Apple devices such as MacBook Pro, press the OPTION key during the boot process to select the EFI default boot and directly boot FydeOS.
 - If rEFInd is already installed on the hard disk, the dualboot installer will add an icon to FydeOS during the installation process.

<br>
#### Upgrade the FydeOS system in the hard disk
As with the direct installation command, the script will skip the blank space check, but it will check whether the old root partition has sufficient capacity. If the new version has a larger root partition, it will not be upgraded. Please backup your personal files, uninstall FydeOS (see below), and reinstall.


<br>
#### Uninstall the FydeOS system in the hard disk
If you no longer want to keep the FydeOS system on the hard disk, please backup important personal files in the system yourself, and in the TTY Shell, run the following command to uninstall FydeOS:
```bash
sudo dual-boot-remove -d /dev/sda
```
This command is also suitable for clearing all FydeOS partitions and booters on the target hard disk after installation fails.


## 6. FAQ

> How long does it take to install?

Under normal circumstances, about 10 minutes or so, depending on the speed of the disk and USB boot device, there will be some fluctuations.


> How many partitions will a new installation create on the system?

2 new partitions will be created. According to the Chromium OS standard, there will be 12 partitions, and FydeOS will be reduced to 2.


> After the multi-boot configuration is completed, does the system support OTA upgrade?

Sorry, under the current multi-start strategy, the system will not support OTA, and related services will be blocked. To achieve OTA upgrade in a multi-start state, you need to create many disk partitions as a cost. Because the partition does not conform to the Chromium OS standard, if you forcefully try to upgrade through OTA, it may damage other partitions on the hard disk.


> Will upgrading FydeOS in multiple boot states cause user data loss?

will not. Please refer to this tutorial "Upgrading the FydeOS System on the Hard Disk" to burn the new version of the system to the U disk and boot successfully, and then run the multi-boot installation script again. The program will automatically detect the partition, upgrade the system partition, and will not destroy the user file partition.

**But we still recommend that you back up your data before upgrading!**



> Is the installation process safe? Will data be lost?

The installation process will do several things:
 - Create the required partition
 - Write files necessary for FydeOS to the newly created partition
 - Copy some files to ESP partition
 - Add system startup items

The script will not do any operations such as deleting existing partitions or emptying disks and partition tables. So in theory it is quite safe. Of course, please remember to make a backup before operating the disk at any time, or use a worthless hard disk for testing. We will not be responsible for any disk data problems caused by the installation and use of FydeOS.



> After FydeOS is installed, can I install other OS?

Of course, but you need to manually reduce the capacity of the FydeOS user partition and insert other partitions later. Or, delete the partitions of other previous OSs and create partitions for the new OS. FydeOS does not rely on the partition number to record its own partition in multi-boot mode.
