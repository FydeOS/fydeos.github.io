---
date: 2018-07-15
title: Running FydeOS for TKB for the first time
categories:
  - 起步走
type: Document
permalink: /getting-started/fydeos-for-tkb/
redirect_from:
  - /安装教程/FydeOS-for-TKB-安装指南/
  - /起步走/首次运行FydeOS-for-TKB/
lang: en
---

## Minimalist

We recommend using [etcher](https://etcher.io/) to burn the SD card. etcher is a tool software that helps users quickly burn image files to USB devices or flash memory cards, and can be used in various operating systems such as Windows, macOS, and mainstream Linux versions. The software is beautifully designed and the interface is friendly, I believe you will be familiar with its simple trilogy operation immediately:

![img](https://fydeos.com/wp-content/uploads/2016/11/etcher-1.gif)

You can download the etcher installation package for Windows, macOS or Linux from [etcher official website](https://etcher.io/).

Please get the image file of FydeOS for TKB in our [download page](https://fydeos.com/download/). After downloading, there is no need to unzip and rename, please directly use the etcher to open the image file; then please select the SD card that will be used to burn FydeOS for TKB; Finally, you only need to click the "Flash!" Button Help you deal with the rest! After everything is completed, you can remove the SD card and put it in your Tinker Board to enjoy the new browsing experience brought by FydeOS.

If you prefer a more traditional installation method, you can proceed as follows:

## Windows

1. Please obtain the image file in .zip or .xz format from our [download page](https://fydeos.com/download/) and decompress it using your favorite decompression software, such as [7zip](https://www.7-zip.org/download.html).

2. After unzipping, you should get an .img image file. But if you get a .bin file, don't panic! This is the same as the .img file, just rename it and modify the suffix.

3. Use the file manager included with Windows to format an SD card with 4GB or more memory.

4. Use [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/) to select the image file and SD card you are using. Please be sure to select the correct driver to prevent damage to any useful data.

5. Press "Write", after the burning is successfully completed, the SD card is ejected, and the SD card can be inserted into the Raspberry Pi and used.

## macOS

1. Please obtain the image file in .zip or .xz format from our [download page](https://fydeos.com/download/) and use the decompression program that comes with macOS to decompress it.

2. After unzipping, you should get an .img image file. But if you get a .bin file, don't panic! This is the same as the .img file, just rename it and modify the suffix.

3. Use the "Disk Utility.app" that comes with macOS to format an SD card with 4GB or more memory.

4. Then, refer to the [guide](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md) on the Raspberry Pi website for operation. It provides a variety of technical methods for reference, you can Choose according to your needs.

4. After burning, you can insert the SD card into the Tinker Board and use it.

## Linux

1. Please obtain the image file in .zip or .xz format on our [download page](https://fydeos.com/download/) and use your favorite decompression software to decompress it, such as [7zip](https://www.7-zip.org/download.html).

2. After unzipping, you should get an .img image file. But if you get a .bin file, don't panic! This is the same as the .img file, just rename it and modify the suffix.

3. Format an SD card with 4GB or more memory. If you are not familiar with Linux command line operation, you can use software with a graphical interface, such as GNOME Disks.

4. After that, you can refer to the [guide](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md) on the Raspberry Pi website for operation. It provides a variety of technical methods for your reference. You can choose according to your needs.

5. After burning, you can insert the SD card into the Tinker Board and use it.

Install FydeOS and play with Tinker Board! If you encounter any problems during the installation process, please contact us!
