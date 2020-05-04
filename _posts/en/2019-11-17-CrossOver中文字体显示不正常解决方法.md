---
date: 2019-11-17
title: Solution to Chinese font display issue of CrossOver
categories:
 - 使用技巧
type: Document
permalink: /recipes/crossover-chinese-font/
lang: en
---

If you think the text is too long, you can jump directly to the "Main content" section

## 0. Advance knowledge

CrossOver is based on wine, so many wine configurations can also be implemented on CrossOver.

CrossOver is here in the form of an Android app. Its data is in the `/data/data/com.codeweavers.cxoffice/files/` directory in the Android container. To access this directory in an external system, add `/opt/google/containers/android/rootfs/android-data/`. Take a look at the content

![image-20191116210221289](https://fydeos.com/wp-content/uploads/2019/11/image-20191116210221289.png)

### 0.1 wine environment
Each wine container (environment) is distinguished by WINEPREFIX, here is the `prefixes` folder under the data directory, you can know that each time a new wine environment is created, there will be one more subdirectory, and the content in each subdirectory is similar

![image-20191116205648049](https://fydeos.com/wp-content/uploads/2019/11/image-20191116205648049.png)

Here we choose the QQMusic container to test

First look at the directory:

![image-20191116205920621](https://fydeos.com/wp-content/uploads/2019/11/image-20191116205920621.png)

There are two main things to note here:

#### 0.1.1 Font folder

There are three font folders. Two of them are in `./drive_c/fonts/`

![image-20191116210431018](https://fydeos.com/wp-content/uploads/2019/11/image-20191116210431018.png)

One is `system`, it can be seen that it points to the font folder in the Android subsystem, this folder is read-only

The other is the folder with wine. I see that it is also a soft link pointing to the `share/wine/fonts` directory in the data directory. This should be the font with wine, which is common to all containers.

The third is `./drive_c/windows/Fonts/`, which is actually the Windows system font directory, each container is independent. Check to see that this directory is actually empty, presumably due to copyright reasons.

#### 0.1.2 Registry key

Note that the files with the suffix `.reg` are actually Windows registry data stored in text format. Different file names correspond to different registry trees. In this problem, we need to solve the problem by modifying the registry.

There are mainly registry entries related to fonts in wine
- Wine related configuration
  - `HKEY_CURRENT_USER\Software\Wine\Fonts\Replacements` can be known by name, here is the replacement font of a certain font
  - `HKEY_CURRENT_USER\Software\Wine\Fonts\External Fonts` path of the external font (fonts other than C:\\windows\Fonts) file recorded here
  - `HKEY_CURRENT_USER\Software\Wine\Fonts\Cache` font cache may be, the name of each subdirectory is the standard name of the font
- Windows related configuration
  - `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT \CurrentVersion\ FontLink\SystemLink` seems to be able to specify the corresponding file path for a certain font. I have seen many tutorials saying that this is modified to support Chinese, but it seems to have no effect.
  - The path corresponding to the font name of `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Fonts`, don't worry about this here

## 1. Main content

There are two steps to fix, it is recommended to stop all wine processes in the CrossOver menu before operating

### 1.1 Add Chinese font

Here we choose to add the classic Wenquanyi micro-black font `wqy-microhei.ttc`, which can be downloaded from the Internet and placed in `./drive_c/windows/Fonts/`, wine will automatically recognize this font,

**It is recommended to restart the subsystem after adding fonts and then ensure correct reading. Otherwise, the next modification of the registry key may not take effect, the reason is unknown.**

How to ensure that the font is read by wine?

Select `Command Shell` from the menu and enter `regedit` in the command line that appears to start the Windows Registry Editor. In `HKEY_CURRENT_USER\Software\Wine\Fonts\Cache` you should find a file called `WenQuanYi Micro Hei` The sub-directory shows that the Wenquanyi micro-black font is correctly read by wine.

### 1.2 Modify the registry key

Here we can choose to edit the registry in `regedit`, but there are too many entries to be modified, no one should do so.

We can achieve this goal by modifying `user.reg`. The effect is the same. First, we recommend stopping all wine processes before operating!

The entry we want to modify is `HKEY_CURRENT_USER\Software\Wine\Fonts\Replacements`, which indicates the candidate font after a certain font is missing. We want to add Wenquanyi Micro Black as a candidate font to all commonly used Chinese fonts.

The registry before modification:

![](https://fydeos.com/wp-content/uploads/2019/11/regedit0.png)

Before we modify it, there will be many table entries with the value `Noto Sans CJK SC Regular`, which is also a Chinese font, we need to replace the values ​​of these items with `Noto Sans CJK SC Regular` and `WenQuanYi Micro Hei`, and add some fonts such as `Song type`, `Bold type` and other candidates.

- Open `user.reg`, find the block that starts with `[Software\\Wine\\Fonts\\Replacements]` (at the end of the file), delete the block that looks like `"XXXXXXX"="Noto Sans CJK SC Regular"` lines, be careful not to leave blank lines in the middle.

- Add the following items at the end of the block

  ```
  "DFKai-SB"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "FangSong"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "Hiragino Sans GB"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "KaiTi"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "Microsoft JhengHei"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "Microsoft Sans Serif"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "Microsoft YaHei"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "MingLiU"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "NSimSun"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "PMingLiU"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "SimHei"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "SimKai"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "SimSun"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x4eff\x5b8b"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x4eff\x5b8b_GB2312"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x5b8b\x4f53"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x5fae\x8f6f\x96c5\x9ed1"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x601d\x6e90\x9ed1\x4f53 Regular"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x65b0\x5b8b\x4f53"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x65b0\x7d30\x660e\x9ad4"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x6977\x4f53"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x6977\x4f53_GB2312"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x96b6\x4e66"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  "\x9ed1\x4f53"=str(7):"Noto Sans CJK SC Regular\0WenQuanYi Micro Hei\0"
  ```
After saving, you can see from regedit that some common fonts have been added, and Wenquanyi Micro Black has been added as a candidate font.

  ![](https://fydeos.com/wp-content/uploads/2019/11/regedit1.png)

## 2. Effect

The Chinese part of the original lyrics is displayed as a square, and it is now displayed normally.

![](https://fydeos.com/wp-content/uploads/2019/11/qqmusic.png)



In addition, another seemingly reliable method on the Internet is to directly put all the fonts in the Fonts folder of the original Windows into `./drive_c/windows/Fonts/`, but I have not tried it, you can try it.
