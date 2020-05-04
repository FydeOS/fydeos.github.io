---
title: Install Linux apps
help_section:
  - Managing your apps
  - Install apps and extensions
weight: 4
type: Document
permalink: /help/apps/install/linux/
lang: en
---

You can install Linux tools, editors, and IDEs on FydeOS to meet the needs of writing code and creating applications.

Note: The support function provided for Linux is still in the testing stage, you may encounter problems.

For how to set up Linux (beta) and install Linux applications on FydeOS, please refer to the official website knowledge base [related documents](https://faq.fydeos.com/en/category/crostini/).

## Security and permissions

Normally, FydeOS protects the computer by running various applications in a "sandbox", but it runs all Linux applications in the same sandbox. In other words, harmful Linux applications may affect other Linux applications, but not the rest of FydeOS.

All Linux applications can use permissions and files shared with Linux.

## Solve problems with Linux

If you encounter problems with Linux or Linux applications, try the following steps:

- Restart FydeOS.
- Check if the virtual machine is the latest version. The specific method is: In the browser, go to `chrome://components`, under "cros-termina", choose to check for updates. If you download updates, you may need to restart FydeOS.
- Update packages. The specific method is: open the terminal, and then run `sudo apt-get update && sudo apt-get dist-upgrade`.

Note: You may need to restart FydeOS for the changes to take effect. Linux will automatically check for new packages after completing the initial setup, and check every 24 hours during operation.

## Learn which features or devices are not yet supported

- Speakers, microphones, cameras and USB devices are not yet supported.
- Android Studio is not yet supported, including emulator and USB debugging.
- Hardware acceleration is not yet supported, including GPU and video decoding.
- The default terminal application supports ChromeVox, but other Linux applications do not yet support it.
