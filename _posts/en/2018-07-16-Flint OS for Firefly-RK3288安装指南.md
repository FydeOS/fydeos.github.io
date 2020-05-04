---
date: 2018-07-16
title: Flint OS for Firefly-RK3288 Installation guide
categories:
  - 早期版本
type: Document
permalink: /previous-releases/firefly-rk3288/
redirect_from:
  - /早期版本/Flint-OS-for-Firefly-RK3288安装指南/
lang: en
---
> Attention! The early version of Flint OS for Firefly-RK3288 needs to be burned into Firefly-RK3399's onboard high-speed flash memory (eMMC) to ensure normal and stable operation. This operation will erase all the data in eMMC and is irreversible. If you want to continue, please do a good job of data backup in advance. To restore the original system, please use the official recovery tool. We cannot be responsible for potential data loss and various problems that may occur during installation or provide timely technical support. Please think twice!

## Linux

#### 0. Required tools

Hardware and related tools:
* [Firefly-RK3288 Development Board](http://www.t-firefly.com/product/rk3288.html)
* Adapt to the power supply of Firefly-RK3288 development board
* USB OTG cable

Operating system and related software:
* Common Linux distributions (we recommend Ubuntu 16.04 LTS)
* Unzip tool [7-zip](http://www.7-zip.org/)

#### 1. Download and unzip

Please obtain the image file of Flint OS for Firefly-RK3288 in our [download page](https://fydeos.com/download/) early version (Flint OS) download. The following command will take the file name of `flint_os_firefly_3288_emmc_v0.1.7z` as an example.

Run the following command under your Linux to decompress the downloaded compressed package and enter the decompressed folder:

```
$ 7z x flint_os_firefly_3288_emmc_v0.1.7z
$ cd firefly3288_emmc_flintos_0.1
```

#### 2. Enter loader mode

Use the USB-OTG cable to connect the target Firefly-RK3288 development board to the Linux PC being used. Hold down the RESET button and turn on the power to make the target Firefly-RK3288 development board enter the loader mode.

#### 3. Run the burn script

Enter the command to execute the script under Linux (sudo password required)

```
$ ./upload_emmc.sh
```

#### 4. Enter Flint OS

After the script finishes running, a prompt of `all finished.` will appear. At this moment, manually restart Firefly-RK3288 to enter Flint OS.

## Windows

#### 0. Required tools

Hardware and related tools:
* [Firefly-RK3288 Development Board](http://www.t-firefly.com/product/rk3288.html)
* Adapt to the power supply of Firefly-RK3288 development board
* USB OTG cable

Operating system and related software:
* Can use Windows system in administrator mode (we recommend Windows 7)
* Unzip tool [7-zip](http://www.7-zip.org/)
* Officially provided programming tool - AndroidTool_Release_v2.33 - [click to download](http://flintos-misc.oss-cn-beijing.aliyuncs.com/AndroidTool_Release_v2.33.rar)

#### 1. Download and unzip

Please obtain the image file of Flint OS for Firefly-RK3288 in our [download page](https://fydeos.com/download/) early version (Flint OS) download. The following will take the file name of `flint_os_firefly_3288_emmc_v0.1.7z` as an example.

Unzip it under Windows, and you should get a folder named `firefly3288_emmc_flintos_0.1`.

Drag the unzipped AndroidTool_Release_v2.33 folder into the above `firefly3288_emmc_flintos_0.1` folder, the folder structure at this time should be:

```
\firefly3288_emmc_flintos_0.1
|-- AndroidTool_Release_v2.33
|   |-- Language
|   |   |-- Chinese.ini
|   |   `-- English.ini
|   |-- Log
|   |-- AndroidTool.exe
|   |-- config.cfg
|   |-- config.ini
|   `-- RK3288UbootLoader_V2.19.01.bin
|-- tools
|   `-- upgrade_tool
|-- boot.img
|-- kernel.img
|-- parameter_emmc.img
|-- part_1_STATE.img
|-- part_2_KERN-A.img
|-- part_3_ROOT-A.img
|-- resource.img
`-- upload_emmc.sh</code>
```

#### 2. Enter loader mode

Use the USB-OTG cable to connect the target Firefly-RK3288 development board to the Windows PC being used. Hold down the RESET button and turn on the power to make the target Firefly-RK3288 development board enter the loader mode.

#### 3. Flash using AndroidTool

Go to the AndroidTool_Release_v2.33 folder and run AndroidTool.exe as an administrator. At this point, AndroidTool should automatically find the disk image file in the upper directory, as shown in the following figure:

![img](https://flintos.com/wp-content/uploads/2017/04/androidTool.png)

At this point, click "Execute" to start the programming process.

#### 4. Enter Flint OS

After programming, restart Firefly-RK3288 manually to enter Flint OS.
