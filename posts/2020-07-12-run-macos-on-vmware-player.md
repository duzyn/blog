---
title: 在 Windows 的 VMWare Player 运行 macOS 虚拟机
author: David Peng
date: 2020-07-12
---

在需要体验 macOS 时，比如学习 Apple 最新的设计，测试 macOS app 等场景，使用虚拟机运行 macOS 是方便省事的，你并不需要一台 Mac 电脑。

当然了，虚拟机并不适合日常使用，只是偶尔体验一下。本文并非手把手教学，只是说明了重点步骤，你需要对 VMWare 安装虚拟机有些经验。另外，动手能力也是必不可少的。

# 准备工作

在开始体验 macOS 前，你需要：

- 一台 Windows 桌面电脑/笔记本，Intel CPU 更好。
- [VMWare Workstation Player](https://www.vmware.com/products/workstation-player.html)，Player 是免费的，你并不需要装收费的 Pro，免费的已足够了。不要使用 VirtualBox。
- [auto-unlocker](https://github.com/paolo-projects/auto-unlocker)，用于解锁 VMWare 运行 macOS 虚拟机的隐藏技能。
- [gibMacOS](https://github.com/corpnewt/gibMacOS)，一个可以从 Apple 官网下载 macOS 安装包的程序。
- [QEMU](https://qemu.weilnetz.de/w64/)，用于将 macOS 恢复盘文件转换为 VMDK 硬盘 [^1]。

[^1]: "[Guide] Simple Steps To Create Macos Installer For Vmware On Linux Or Windows". 2020. Insanelymac Forum. https://www.insanelymac.com/forum/topic/342603-guide-simple-steps-to-create-macos-installer-for-vmware-on-linux-or-windows/.

# 实际操作

1. 安装 VMWare Workstation Player，使用一般的软件安装方法，略去不表。安装后不要启动 VMWare，下一步解锁 VMWare 时其不能正在运行。
2. 下载 [auto-unlocker](https://github.com/paolo-projects/auto-unlocker/releases)，解压缩后双击 Unlocker.exe 运行，等待提示已经完成打补丁时，关闭程序。
3. 下载 [gibMacOS](https://github.com/corpnewt/gibMacOS/archive/master.zip) 后解压缩，运行 gibMacOS.bat，在弹出的窗口中选择 I. Only Print URLs (Currently False)，意思是只打印下载地址。因为我们只需要下载 macOS 的一个恢复盘文件，在复制这个文件的 URL 后我们可以用其他方法下载。选择后，我们按提示选择操作系统版本，比如选 1，会打印出一些 URL，我们找到结尾是 BaseSystem.dmg 的那个，然后复制后下载它。
4. 安装 QEMU。可以从 <https://qemu.weilnetz.de/w64/> 下载安装包，或者使用 Scoop 命令 `scoop install qemu` 安装。推荐使用后者。
5. 使用命令将恢复盘文件转换为 VMDK 硬盘：`qemu-img convert -O vmdk -o compat6 BaseSystem.dmg recovery.vmdk`。
6. 现在可以从 VMWare 新建 macOS 虚拟机了。记住，要选操作系统为 Apple Mac OS X，另外要手动添加一个硬盘，选中刚才我们转换得到的 recovery.vmdk。
7. 完成后启动虚拟机，然后像正常的重装 macOS [^2] 即可。在安装的过程中，会从 Apple 官方下载文件，网速快安装就快。装完后会自动重启，进入设置助理，按界面提示设置完 [^3] 就可使用 macOS 虚拟机了。

[^2]: "关于 Macos 恢复功能". 2020. Apple Support. https://support.apple.com/zh-cn/HT201314.

[^3]: "设置 Mac". 2020. Apple Support. https://support.apple.com/zh-cn/guide/macbook-pro/apd831707cb3/mac.

# 总结

使用本文的方法来安装 macOS 虚拟机，优点是安装盘文件来自 Apple 官方的，并非其他人制作的，有效防止了木马或病毒。安装盘是 500MB 左右的恢复盘文件，下载快，但装系统的过程中需要下载很多文件，这需要你有很好的网络。

本文的方法也适用于 Linux。因为用到的工具都是支持 Linux 的，但笔者并未实测，读者可自行验证。
