---
date: 2018-07-16
title: Flint OS for Firefly-RK3399 Installation guide
categories:
  - 早期版本
type: Document
permalink: /previous-releases/firefly-rk3399/
redirect_from:
  - /早期版本/Flint-OS-for-Firefly-RK3399安装指南/
lang: en
---
> Attention! Flint OS needs to be burned into Firefly-RK3399's onboard high-speed flash memory (eMMC) to ensure normal and stable operation. This operation will erase all the data in eMMC and is irreversible. If you want to continue, please do a good job of data backup in advance. To restore the original system, please use the official recovery tool. We cannot be responsible for potential data loss and various problems that may occur during installation or provide timely technical support. Please think twice!

## Linux

#### 0. Required tools

Hardware and related tools:
* [Firefly-RK3399 Development Board](http://www.t-firefly.com/product/rk3399.html)
* Adapt to the power supply of Firefly-RK3399 development board
* USB OTG cable

Operating system and related software:
* Common Linux distributions (we recommend Ubuntu 16.04 LTS)
* Unzip tool [7-zip](http://www.7-zip.org/)

#### 1. Download and unzip

Please obtain the image file of Flint OS for Firefly-RK3399 in our [download page](https://fydeos.com/download/) early version (Flint OS) download. The following command will take the file name of `flint_os_firefly_3399_emmc_v0.1.7z` as an example.

Run the following command under your Linux to decompress the downloaded compressed package and enter the decompressed folder:

```
$ 7z x flint_os_firefly_3399_emmc_v0.1.7z
$ cd firefly3399_emmc_flintos_0.1
```

#### 2. Enter loader mode

Use the USB-OTG cable to connect the target Firefly-RK3399 development board to the Linux PC being used. Hold down the RESET button and turn on the power to make the target Firefly-RK3399 development board enter the loader mode.

#### 3. Run the burn script

Enter the command to execute the script under Linux (sudo password required)

```
$ ./upload_emmc.sh
```

#### 4. Enter Flint OS

After the script finishes running, a prompt of `all finished.` will appear. At this moment, manually restart Firefly-RK3399 to enter Flint OS.
