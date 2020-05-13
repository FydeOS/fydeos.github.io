---
date: 2018-07-30
title: Enter Shell in FydeOS
categories:
  - getting-started
type: Document
permalink: /getting-started/shell-access/
redirect_from:
  - /使用技巧/在FydeOS中进入Shell/
lang: en
---

## 1. Enter Crosh Shell

Start the Chromium browser in the FydeOS graphical interface, and simultaneously press the `Ctrl + Alt + t` key on the keyboard (on some computers, such as Apple Mac, you need to press `Fn + Ctrl + Alt + t`, then The Chromium browser will automatically open a new tab called `crosh`.


## 2. Enter Bash Shell

At the prompt of the `crosh` tab that pops up, enter:
```bash
shell
```
The prompt at this time should be:

```bash
chronos@localhost / $
```


## 3. Get root permissions

Enter:

```bash
sudo su -
```
Note that as of FydeOS for PC v6.0, the default user chronos on the system command line will no longer set a default password. You can directly use the sudo command to perform command line operations that require root privileges. If you need to change the password, you can refer to [this document](/en/recipes/chronos-password/).
