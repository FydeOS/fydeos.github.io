---
anchor: fydeos-preinstalled-browser-extension-has-high-permissions-and-cannot-be-deleted-what-is-it-used-for
weight: 910
lang: en
---
FydeOS comes with a browser extension called "FydeOS System Controller" by default (id: `mofiofjpikncjaigmdlblhojbnkabako`). This extension provides indispensable system functions for FydeOS and is an important part of FydeOS system.

Due to the particularity of the extension, there are many contents of the permission applied by the extension displayed on the extension detail page. But don't worry, this plugin only provides services for FydeOS and its affiliated functions, and the interfaces involved in the bottom layer of the system are protected by solutions such as `minijail` (see [Design Document](https://www.chromium.org/chromium-os/developer-guide/chromium-os-sandboxing)), which guarantees the overall security of the system to the greatest extent.
