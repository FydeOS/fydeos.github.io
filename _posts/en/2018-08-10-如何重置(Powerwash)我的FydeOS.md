---
date: 2018-07-30
title: How to reset (Powerwash) my FydeOS
categories:
  - 使用技巧
type: Document
permalink: /recipes/powerwash/
redirect_from:
  - /使用技巧/如何重置(Powerwash)我的FydeOS/
lang: en
---

> The purpose of this operation is to restore the factory settings and clear all user data, including but not limited to the installed browser plug-ins, Android programs, data in the download folder, and browser cache files and historical records. The result of this operation is irreversible after successful execution, please think twice.


## 1. Enter Bash Shell

Refer to [this tutorial](/en/getting-started/shell-access/) to enter the Bash Shell environment.


## 2. Run the command


```bash
echo 'clobber' | sudo tee /mnt/stateful_partition/.update_available
sudo reboot
```

And enter the password after the prompt, the default is `chronos`.

After the system restarts, it will automatically complete the data clearing and automatically enter the OOBE (unpacking experience) link.
