---
date: 2019-03-10
title: Set or modify the FydeOS command line chronos account password
categories:
  - tips
type: Document
permalink: /recipes/chronos-password/
lang: en
---

Starting with FydeOS for PC v6.0, the default user `chronos` on the system command line will no longer set a default password. You can directly use the `sudo` command to perform command line operations that require root privileges.

You can set or modify the password of the `chronos` account in the following two ways:

## 1. Using scripts

```
$ sudo chromeos-setdevpasswd
```
According to the prompt, enter and confirm the password you want to set.

Please note that the password set by this method cannot be used as the credentials for SSH remote login to the `chronos` account. If you want to gain root authority and open an SSH remote connection and use the same password, please use the next method.


## 2. Execute the command

If you want to gain root authority and open an SSH remote connection and use the same password, use the command:

```
$ sudo mount -o remount rw /
$ sudo passwd chronos
```
According to the prompt, enter and confirm the password you want to set.
