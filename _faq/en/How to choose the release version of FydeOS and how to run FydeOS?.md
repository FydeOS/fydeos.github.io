---
anchor: how-to-choose-fydeos-release-and-how-to-run-fydeos
weight: 998
lang: en
---
Currently we have the following three main FydeOS releases. According to different scenarios, you can choose the release download experience that suits you best:

 - **FydeOS for PC** is the most universal FydeOS release, intended to adapt to most PC devices with Intel CPU and Intel integrated graphics. You need to use a USB storage medium to boot for the first time. The specific installation guide can be viewed on [the following page](https://fydeos.com/instructions-pc/). If you have a PC device with Intel integrated graphics that was shipped after 2010, there is a high probability that FydeOS for PC is compatible.

 - **FydeOS for You** is our customized version for some designated devices. It has better adaptability and supports some device-specific functions. If you happen to have these adapted devices, then it is recommended that you use the corresponding version. The installation method is basically the same as FydeOS for PC. The list of devices supported by FydeOS for You will be updated from time to time. For details, please check the [download](https://fydeos.com/download/) page.

 - **FydeOS VM for VMWare** is our FydeOS virtual machine image file specially adapted for the VMWare virtual machine client. Use this release to experience FydeOS in the easiest way to experience, just [download](https://fydeos.com/download/) the latest image file of the FydeOS VM for VMWare client, follow the [guide](https://fydeos.com/instructions-vmware/) Import can experience most of the functions of FydeOS on all mainstream operating systems with VMware client installed. It is worth noting that due to the special design of FydeOS and its subsystems, some functions in FydeOS VM are restricted or unavailable. For details, please read the release notice of FydeOS VM carefully.

<br>

At the same time, we also open sourced some of the core technologies for making FydeOS, and maintained Chromium OS that can run on embedded devices and single-board computer development kits, including:

 - [Chromium OS for Raspberry Pi](https://github.com/FydeOS/chromium_os_for_raspberry_pi): Adapt to the famous single board computer development board Raspberry Pi and its suit (3B / 3B+ / 4B / Pi400).
 - [Chromium OS for Asus Tinker Board](https://github.com/FydeOS/chromium_os_for_tinker_board): It is compatible with the development board Tinker Board produced by Asus which has the same specifications as the Raspberry Pi.
 - [Chromium OS VM for VMWare](https://github.com/FydeOS/chromium_os-vm-vmware): The Chromium OS virtual machine adapted to the VMWware virtual machine client is also the technical basis of FydeOS VM for VMWare.