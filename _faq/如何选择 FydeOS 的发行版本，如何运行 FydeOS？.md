---
anchor: how-to-choose-fydeos-release-and-how-to-run-fydeos
weight: 998
lang: zh_CN
---
目前我们有如下三种主要的 FydeOS 发行版，根据不同的场景，你可以选择最适合你的发行版下载体验：

 - **FydeOS for PC** 是最普适的 FydeOS 发行版，意在适配绝大多数带有 Intel CPU 及 Intel 集成显卡的的 PC 设备。首次启动需要使用 USB 存储介质引导，具体的安装指南可以查看[以下页面](https://fydeos.com/instructions-pc/)。如果你拥有一台 2010 年之后出厂的 携带有 Intel 集成显卡的 PC 设备，很大概率上 FydeOS for PC 是能够兼容的。

 - **FydeOS for You** 是我们为部分指定设备专门定制的版本，具有更好的适配性，并且支持一些根据具体设备功能。如果你恰好拥有已适配的这些设备，那么推荐你使用相应的版本。安装方式与 FydeOS for PC 基本无异。FydeOS for You 支持的设备列表将不定期更新，详情请查看[下载](https://fydeos.com/download/)页面。

 - **FydeOS VM for VMWare** 是我们针对 VMWare 虚拟机客户端专门适配的 FydeOS 虚拟机镜像文件。使用该发行版可以以最简便的体验方式体验 FydeOS，只需要[下载](https://fydeos.com/download/)最新的 FydeOS VM for VMWare 客户端的镜像文件，按照[指南](https://fydeos.com/instructions-vmware/)导入即可在安装有 VMware 客户端的所有主流操作系统上体验 FydeOS 的大部分功能。值得注意的是，由于 FydeOS 及其子系统设计的特殊性，FydeOS VM 里的部分功能是受到限制或者无法使用的，详情请认真阅读 FydeOS VM 的发布通知。

<br>

与此同时，我们还把制作 FydeOS 的一些核心技术开源，维护了能在嵌入式设备以及单板机开发套件上运行的 Chromium OS，包括：

 - [Chromium OS for Raspberry Pi](https://github.com/FydeOS/chromium_os_for_raspberry_pi): 适配著名单板机开发板树莓派及套装（3B / 3B+ / 4B / Pi400）。
 - [Chromium OS for Asus Tinker Board](https://github.com/FydeOS/chromium_os_for_tinker_board): 适配华硕出品的与树莓派同规格的开发板 Tinker Board。
 - [Chromium OS VM for VMWare](https://github.com/FydeOS/chromium_os-vm-vmware): 适配 VMWware 虚拟机客户端的 Chromium OS 虚拟机，也是 FydeOS VM for VMWare 的技术基础。