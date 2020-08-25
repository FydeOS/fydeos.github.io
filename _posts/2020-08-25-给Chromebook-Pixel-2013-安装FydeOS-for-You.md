---
date: 2020-08-25
title: 为 Chromebook Pixel 2013 刷写第三方（MrChromebox）固件
categories:
  - 起步走
permalink: /recipes/chromebook-pixel-2013-firmware/
type: Document
---


## 序

Chromebook Pixel 2013 目前处在 End-of-Life 的状态，最后一个可以在该设备上运行的官方 Chrome OS 版本为 69，且不支持安卓子系统以及 Linux（测试版）。

FydeOS for You - Chromebook Pixel 2013 为该设备提供了一个全新的选项，提供跟随上游项目的新版本 Chromium 以及完整的附属功能支持，包括安卓子系统以及 Linux（测试版）。

值得注意的是，Chromebook Pixel 2013 的原版固件过旧，无法提供 Linux（测试版）所需的硬件虚拟化界面。若你希望能在 FydeOS for You - Chromebook Pixel 2013 中启用 Linux（测试版），则需要为该设备刷写由 [MrChromebox](https://mrchromebox.tech) 提供的第三方固件。

本教程将介绍如何为携带原厂固件的 Chromebook Pixel 2013 设备刷写 MrChromebox 固件。


>注意！刷写固件是一件带有风险的操作，存在失败的可能性。本教程虽然经过燧炻创新团队测试，但仍存在发生小概率失败事件的可能。一旦刷写失败，有可能造成设备无法启动（变砖）以及数据丢失的风险。燧炻创新无法为潜在的风险承担任何责任。若要继续，所有操作的风险将由你来承担，请三思而后行。


>注意！固件刷写成功之后，现存的 Chrome OS 将无法启动，刷写前 Chrome OS 下的所有数据将随即丢失。请务必在执行以下操作之前备份好你认为重要的所有数据，且做好安装新系统的准备。


## 所需物料
 - 携带原厂 Chrome OS 的 Chrombook Pixel 2013
 - 8GB 及以上容量的 USB 存储设备（用于安装 FydeOS for You - Chromebook Pixel 2013）
 - USB 存储设备（用于备份原厂固件）


## 将你的 Chromebook Pixel 2013 转变为开发者模式
0. 备份你觉得有价值的数据，且跟你的原厂 Chrome OS 做最后的道别。
1. 同时按下键盘上 `esc` + `⟳` + `电源` 按键，系统会随即重启并切换至「系统恢复」模式，屏幕上将呈现一个黄色的感叹号。
2. 此时按下键盘的 `ctrl` + `d` 键，系统会随即显示一个即将切换成「开发者模式」的警告信息，按下键盘 `enter` 按键确认之，系统将立即重启。
3. 重启之后系统将呈现目前处于「开发者模式」的警告信息，伴有一个红色的感叹号图标。此时你需要同时按下键盘上的 `ctrl` + `d` 按键跳过该警告方可启动系统。
4. 系统启动之后，在 Chromium 浏览器开启的状况下按下键盘 `ctrl` + `alt` + `t` 则可开启系统的 Crosh 命令行页面。在命令提示符下输入 `shell` 并按下回车键，若提示符呈现绿色的 `chronos@localhost / $` 则说明开发者模式开启成功且你已成功进入命令行会话，如下图所示：
![shell](https://fydeos.com/wp-content/uploads/2020/08/shell.png)

    
## 解除 Chromebook Pixel 2013 上的固件写保护螺丝


## 执行刷写脚本
1. 确保互联网连接的情况下，在以上命令行会话下，复制以下命令并粘贴：

    ```
    cd; curl -LO fydeos.com/firmware && sudo bash firmware
    ```
    该命令将从由燧炻创新的镜像服务器上下载并执行最新版的 MrChromebox 固件刷写脚本，呈现如下的菜单选项：
    ![shell](https://fydeos.com/wp-content/uploads/2020/08/script-mod.png)

2. 确认以上菜单提示里 `Fw WP` 处于 `disabled` 的状态，否则固件刷写必将失败。
3. 选择 "Install/Update UEFI (Full ROM) Firmware"：键入相应选项数字并按回车确认。
4. 键入 `y` 确认所有脚本给出的两个风险提示。
5. 脚本会随即给出备份原厂固件的提示，此处强烈建议根据屏幕提示备份原厂固件。若不想备份，键入 `n` 跳过。
6. 脚本随即开始下载并自动执行固件刷写过程，正常情况下大约需要 90 秒左右的时间。刷写成功之后会给出绿色的 `success` 提示。按回车键回到主菜单之后则可重启系统。
7. 若刷写过程中出现任何错误导致进程中断，**切勿切断电源或者重启设备，否则很可能变砖。**请从步骤 1 开始重新尝试执行该刷写过程。若错误持续出现，请与我们或 MrChromebox 取得联系获取帮助。
8. 刷写成功之后重启系统你将看到 Coreboot 的看起来类似于 🐇 的 logo。此时含有新固件的系统将无法载入原有的 Chrome OS，会卡在寻找可被支持的 OS 状态下，属于正常现象。


## 安装 FydeOS for You - Chromebook Pixel 2013
1. 下载最新版的 FydeOS for You - Chromebook Pixel 2013 并烧写至 USB 储存设备中。
2. 将该储存设备插入 已经完成 MrChromebox 固件刷写的 Chromebook Pixel 2013 设备之中并重启。
3. 在 🐇 logo 出现之时按下键盘 `esc` 键呼出启动菜单，选择通过 USB 存储设备引导启动。
4. 进入通过 USB 存储设备启动的 FydeOS 中执行 Installer 程序完成 FydeOS 的安装。