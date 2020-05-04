---
anchor: how-to-run-fydeos
weight: 998
lang: zh_CN
---
目前，我们发布的 FydeOS 是针对 PC 和平板电脑为载体优化的版本，功能最为完整。欲体验完整功能版的 FydeOS，有如下三种方式：

 - FydeOS VM for VMWare：最简便的体验方式，只需要[下载](https://fydeos.com/download/)我们提供的适配 VMWare 客户端的镜像文件，按照[指南](https://fydeos.com/instructions-vmware/)导入即可在所有主流操作系统上体验 FydeOS 的大部分功能。

 - FydeOS for PC：适配绝大多数 x86 硬件体系的设备，首次启动需要使用 USB 存储介质引导，具体的安装指南可以查看[以下页面](https://fydeos.com/instructions-pc/)。

 - FydeOS for You：为部分设备专门定制的版本，具有更好的适配性。如果你恰好拥有已适配的这些设备，那么推荐你使用相应的版本。安装方式与「FydeOS for PC」基本无异。

与此同时，我们还把制作 FydeOS 的一些核心技术开源，维护了能在嵌入式设备以及单板机开发套件上运行的 Chromium OS（FydeOS 的上游项目），包括：

 - [Chromium OS for Raspberry Pi](https://github.com/FydeOS/chromium_os_for_raspberry_pi): 适配著名单板机开发板树莓派（3B / 3B+ / 4B）。
 - [Chromium OS for Asus Tinker Board](https://github.com/FydeOS/chromium_os_for_tinker_board): 适配华硕出品的与树莓派同规格的开发板 Tinker Board。
