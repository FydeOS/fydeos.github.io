---
anchor: experimental-tpm-fallback
weight: 601
lang: zh_CN
---
可信平台模块 (TPM) 通常是一种植于计算机内部为计算机提供可信根的芯片，为了保障系统安全性，FydeOS 有不少功能依赖于 TPM 芯片提供的功能。市面上存在许多不同的 TPM 芯片及对应的规格，有些时候因为不兼容的原因 FydeOS for PC 无法加载你设备上的 TPM 芯片模块，会导致如下功能不可用：

 - <chrome://flags> 页面空白
 - 浏览器无法导入自定义安全证书
 - 「关于 FydeOS」-「更多详情」-「变更版本」按键不可用

若出现上述情况，可以开启此开关促使系统跳过一些原本设定好的对 TPM 芯片的检查以保障这些功能可用。