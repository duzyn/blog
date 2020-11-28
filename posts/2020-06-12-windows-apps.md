---
title: 值得推荐的 Windows 应用
author: David Peng
date: 2020-06-12
toc: true
---

这些都是我在工作和生活中必用的 Windows 应用，每一个都是各自领域的佼佼者。有了这些应用，处理各项事情都可以有更高的效率。

# Scoop

为什么先介绍 [Scoop](https://scoop.sh)？因为它是安装应用的应用，使用它我们可以快速安装多个其他的应用。

Scoop 是一个包管理器，主要是给开发人员使用命令行快速安装软件包所用。在 Linux 上有 [apt-get](https://linux.die.net/man/8/apt-get)，[pacman](https://wiki.archlinux.org/index.php/pacman)，[yum](https://fedoraproject.org/wiki/Yum)，在 Mac 上有 [Homebrew](https://brew.sh)，在 Windows 上，之前有个 [Chocolatey](https://chocolatey.org/)，功能与 Scoop Scoop 类似，但是是一家公司维护的。综合来说，Scoop 是 Windows 平台上目前最好用的包管理。

Scoop 的优势是：

- 简单。使用一个命令就能快速搜索、安装、卸载软件。无需去到软件的官网的下载页面，下载 app。因为 Scoop 是开源项目，支持的软件也越来越多，所以它变得越来越方便。
- 安全。虽然是开源的项目，但是每个软件都是从官方渠道下载，并且使用 [VirusTotal](https://www.virustotal.com/) 扫描，确保网友贡献的包不会出现病毒。这比个人维护的项目更加可靠。
- 更新。Scoop 使用一个 JSON 文件表示一个应用的各项元数据和安装、更新、卸载方法，并且有一个持续集成的服务，自动定期检测软件的更新版本。这样我们可以一个命令就将软件更新到最新版本。
- 强大。Scoop 可以同时安装一个软件的多个版本，并在多个版本中可以设置使用哪个版本。这在使用的不同版本的开发环境时特别有用，比如不同的 JDK 版本，不同的 apache 版本等。

还有很多其他强大的特性，不再一一列举，可以访问 [Scoop Wiki](https://github.com/lukesampson/scoop/wiki) 了解更多。

## 安装 Scoop

安装 Scoop 特别简单，只需要以 **管理员身份** 打开 PowerShell，运行以下命令将 Scoop 安装到电脑（默认在我的文档的 scoop 下）

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
iwr -useb get.scoop.sh | iex
```

或运行下述命令将 Scoop 安装到 C 盘：

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
$env:SCOOP='C:\scoop'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
iwr -useb get.scoop.sh | iex
```

要了解 Scoop 的基本用法，输入命令 `scoop help`。

## 添加常用软件源

安装 Scoop 后初始只有 main 软件源，里面都是些命令行的应用。日常用的 GUI 应用基本都在 extras 软件源中。常用软件的老版本在 versions 软件源中。JRE，JDK 在 java 软件源中。

使用下述命令添加软件源：

```powershell
scoop bucket add extras
scoop bucket add java
scoop bucket add versions
```

## 搜索应用

搜索应用使用命令，其中 APP 是搜索关键词：

```powershell
scoop search APP
```

## 安装应用

安装应用使用命令，其中 APPNAME 是应用名称：

```powershell
scoop install APPNAME
```

## 卸载应用

卸载应用使用命令，其中 APPNAME 是应用名称：

```powershell
scoop uninstall APPNAME
```

## 更新应用

更新应用使用命令，其中 APPNAME 是应用名称：

```powershell
scoop update APPNAME
```

要更新所有应用，使用命令：

```powershell
scoop update *
```

# v2rayN

[v2ray](https://www.v2ray.com/) 是一个好用的 **上网** 工具。[v2rayN](https://github.com/2dust/v2rayN)(Windows) 或 v2rayU(macOS) 或 Shadowrocket(iOS) 是 v2ray 的 GUI 版本。使用命令安装：

```powershell
scoop install v2rayn
```

然后在 [ugvf2009/Miles](https://github.com/ugvf2009/Miles) 查看使用教程。

在订阅设置中添加以下订阅：

- 备注：ugvf2009/Miles
- 地址：https://jiang.netlify.com

然后更新订阅，选择一个服务器看能不能上网。最好设置为打开全局代理，然后绕过局域网及大陆地址。这样只有局域网和大陆的地址走直连，其他海外地址都走代理，速度会快一些。

# Git

[Git](https://gitforwindows.org) 是目前最流行的源代码版本管理软件。Git 是装完 Scoop 后第一个要装的应用。因为 Scoop 的软件源都是使用 Git 管理的。使用命令安装：

```powershell
scoop install git
```

[Github Desktop](https://desktop.github.com/) 是 Github 的管理 Github 上的 repo 的工具。可视化的操作比 Git 命令行更友好一些。使用命令安装：

```powershell
scoop install github
```

![Github Desktop](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/github-desktop-screenshot-windows.png)

[TortoiseSVN](https://tortoisesvn.net) 是一个 SVN GUI。使用命令安装：

```powershell
scoop install tortoisesvn
```

![TortoiseSVN 右键菜单](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/tortoisesvn-context-menu-dir-control.png)

# 7-Zip

[7-Zip](https://www.7-zip.org/) 是免费好用的压缩、解压缩工具，支持几乎所有的压缩格式，而且文档好用，支持命令行。使用命令安装：

```powershell
scoop install 7zip
```

就算不主动安装 7-Zip，在你安装其他应用时，也可能会自动安装 7-Zip，因为有些安装包下载下来后会保存为 7z 压缩包，Scoop 会先安装依赖包 7zip，然后用它解压缩 7z 文件。

同类软件 [PeaZip](https://www.peazip.org) 也可以尝试，两者差别不大。使用命令安装：

```powershell
scoop install peazip
```

![PeaZip](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/peazip.png)

# Everything

[Everything](https://www.voidtools.com) 是基于名称快速定位文件和文件夹的工具。其可以在数分钟内索引完整个硬盘的文件。有了它之后，你的文件可以随意放，只需要依稀记得文件名即可。使用命令安装：

```powershell
scoop install everything
```

![Everything 搜索窗口界面](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/everything-search-window.png)

# Google Chrome

[Google Chrome](https://www.google.com/chrome/) 是目前最快、最好用、跨平台的浏览器。使用命令安装：

```powershell
scoop install googlechrome
```

![Google Chrome](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/connected_global_desktop.png)

同类软件 [Firefox](https://www.mozilla.org/firefox/) 也可以尝试。使用命令安装：

```powershell
scoop install firefox
```

![Firefox 桌面版](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/firefox-desktop.jpg)

# SumatraPDF

[SumatraPDF](https://www.sumatrapdfreader.org) 是轻量化的 PDF 阅读器，比庞大臃肿的 Adobe Acrobat PDF Reader 不知道轻爽了多少。其打开 PDF 文件速度快，在打开 PDF 文件时，如果文件有变化，可以实时刷新。使用命令安装：

```powershell
scoop install sumatrapdf
```

![SumatraPDF](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/sumatrapdf.png)

# Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) 是微软出品的免费开源、跨平台的编辑器。功能强大，插件丰富，记笔记、写代码都合适。使用命令安装：

```powershell
scoop install vscode
```

![Visual Studio Code Windows 版](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/vscode-screenshot-win-lg.png)

同类软件 [Notepad++](https://notepad-plus-plus.org) 也还不错。在打开特别大的文本文件时，比 Code 性能好。使用命令安装：

```powershell
scoop install notepadplusplus
```

![Notepad++ 演示](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/notepad4ever.gif)

[Sublime Text](https://www.sublimetext.com/3) 也不错，使用命令安装：

```powershell
scoop install sublime-text
```

# draw.io

[draw.io](https://www.draw.io) 是一个免费开源、基于浏览器的流程图编辑器，可以完全替代庞大臃肿的 Visio。使用命令安装：

```powershell
scoop install draw.io
```

![draw.io](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/diagrams-features.png)

# ShareX

[ShareX](https://getsharex.com/) 是强大好用的截图工具。可截取桌面、区域、应用、录制视频、录制 GIF 图，截图之后可标注、分享到图床。使用命令安装：

```powershell
scoop install sharex
```

![ShareX](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/ShareX_Screenshot.png)

要录制视频和 GIF 图，需要安装 [FFmpeg](https://ffmpeg.org)，使用命令安装：

```powershell
scoop install ffmpeg
```

安装并打开 ShareX 后，依次进入 动作设置 → 屏幕记录 → 屏幕录制选项，在 FFmpeg 路径中设置 ffmpeg.exe 的地址，例如是 C:\\scoop\\apps\\ffmpeg\\current\\bin\\ffmpeg.exe。

ShareX 不太好用的功能是滚动截屏，[FastStone Capture](https://www.faststone.org/FSCaptureDetail.htm) 则更好用。使用命令安装：

```powershell
scoop install fscapture
```

![FastStone Capture](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/FSCapturePanel.gif)

FastStone Capture 是收费软件，但百度搜索即可找到可用的序列号，请自行查找。

# FastStone Image Viewer

[FastStone Image Viewer](https://www.faststone.org/FSViewerDetail.htm) 和 FastStone Capture 是同一家公司出品的，是免费强大的看图、图片管理软件。使用命令安装：

```powershell
scoop install fsviewer
```

![FastStone Image Viewer](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/FSViewerScreenShot1.jpg)

# WizTree

[WizTree](https://antibody-software.com/web/software/software/wiztree-finds-the-files-and-folders-using-the-most-disk-space-on-your-hard-drive) 是一个硬盘空间分析软件，可列出每个文件和文件夹的硬盘占用情况。在磁盘分区存满文件后，我们可以用它来快速找到那些占用空间大而没用的文件，从而清理以获得更多空间。WizTree 的速度特别快，扫描一个分区比同类软件 [WinDirStat](https://windirstat.net/) 快得多，和 Everything 有的一比。使用命令安装：

```powershell
scoop install wiztree
```

![WizTree](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/wiztree-treemap.jpg)

# VLC

[VLC](https://www.videolan.org/) 是免费开源、跨平台的全能音视频播放器。使用命令安装：

```powershell
scoop install vlc
```

![VLC](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/vlc_win.jpg)

# QuickLook

[QuickLook](https://pooi.moe/QuickLook/) 可以实现按空格即可预览文件，而无需双击打开。就像在 Mac 电脑上一样。使用命令安装：

```powershell
scoop install quicklook
```

![QuickLook](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/quicklook.png)

# WinDynamicDesktop

[WinDynamicDesktop](https://github.com/t1m0thyj/WinDynamicDesktop) 可以实现 Windows 10 在天黑后自动切换系统主题为暗色，天亮后再自动切换为亮色，桌面壁纸也可随一天的时刻变化。就像在 Mac 电脑上一样。使用命令安装：

```powershell
scoop install win-dynamic-desktop
```

![WinDynamicDesktop 选择主题](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/win-dynamic-desktop-select-theme.png)

# Windows Terminal

[Windows Terminal](https://github.com/microsoft/terminal) 是微软出品的终端软件。可以在一个软件中同时打开命令提示符、PowerShell、WSL、MSYS2、Cygwin 等各种 Shell。使用命令安装：

```powershell
scoop install windows-terminal
```

![Windows Terminal](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/windows-terminal-overview.png)

打开设置后，添加 PowerShell Core 到新建菜单中，其中 guid，可以使用后面的 [uuid](#uuid) 生成。

```json
            {
                // PowerShell Core
                "guid": "{30d8318e-49bf-4c92-bea9-5aa57741014f}",
                "name": "PowerShell Core",
                "commandline": "pwsh.exe",
                "startingDirectory": "%USERPROFILE%",
                "hidden": false
            },
```

# Pandoc

[Pandoc](https://pandoc.org) 是一个全能标记语言转换工具。使用命令安装：

```powershell
scoop install pandoc pandoc-crossref
```

从 GitHub 上下载 [pandoc-templates](https://github.com/duzyn/pandoc-templates)。然后将此目录和 Pandoc 的目录链接起来。

在 Windows 上以管理员身份打开命令提示符，输入命令 `mklink /D "%APPDATA%\pandoc" "D:\GitHub\pandoc-templates"` 创建命令的符号链接。

# wkhtmltopdf

[wkhtmltopdf](https://wkhtmltopdf.org/) 可以将 HTML 文件转换为 PDF 文件，可配合 Pandoc 使用。使用命令安装：

```powershell
scoop install wkhtmltopdf
```

# MiKTeX

[MiKTeX](https://miktex.org) 是一个 TeX 发行版。优点是可以在编译 LaTeX 文件时，自动下载安装缺失的包，可配合 Pandoc 使用，将 Markdown 文件转换为 PDF 文件。使用命令安装：

```powershell
scoop install latex
```

# Python 相关

[Python](https://www.python.org/) 是一种常用的编程语言，有很多 Python 应用。使用命令安装：

```powershell
scoop install python37
```

## pipenv

[pipenv](https://github.com/pypa/pipenv) 是 Python 环境管理工具，可让不同的项目使用不同的 Python 版本。使用命令安装：

```shell
pip install pipenv
```

## WeasyPrint

[WeasyPrint](https://weasyprint.org/) 可以将 HTML 文件转换为 PDF 文件，可配合 Pandoc 使用。使用命令安装：

```shell
pip install WeasyPrint
```

## mkdocs

[mkdocs](https://www.mkdocs.org) 是技术文档编写工具，可将 Markdown 文档转换为静态网站，适合编写技术文档，例如用户书册、产品介绍说明等。使用命令安装：

```shell
pip install mkdocs
```

[mkdocs-material](https://squidfunk.github.io/mkdocs-material/) 是 mkdocs 的材料设计主题，美观而做了很多功能扩展。使用命令安装：

```shell
pip install mkdocs-material
```

# Node.js 相关

[Node.js](https://nodejs.org) 是 Javascript 运行时。使用命令安装：

```powershell
scoop install nodejs-lts
```

## uuid

[uuid](https://github.com/uuidjs/uuid) 是生成 UUID 的命令行工具。使用命令安装：

```shell
npm install -g uuid
```

## capture-website-cli

[capture-website-cli](https://github.com/sindresorhus/capture-website-cli) 是截取网页的命令行工具。使用命令安装：

```shell
npm install -g capture-website-cli
```

## nativefier

[nativefier](https://github.com/jiahaog/nativefier) 将网页转换为原生桌面应用程序。使用命令安装：

```shell
npm install -g nativefier
```

![nativefier 演示](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/nativefier-walkthrough.gif)

## trash-cli

使用 [trash](https://github.com/sindresorhus/trash-cli) 命令将文件删除到回收站，而不是像 rm 将文件彻底删除。使用命令安装：

```shell
npm install -g trash-cli
```

# watchexec

[watchexec](https://github.com/watchexec/watchexec) 可在监控到文件变化后自动执行命令。使用命令安装：

```powershell
scoop install watchexec
```

# SpeedCrunch

[SpeedCrunch](http://speedcrunch.org/) 是一个更好用的计算器，支持很多数学函数、变量，使用起来特别简单。使用命令安装：

```powershell
scoop install speedcrunch
```

![SpeedCrunch 演示](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/speedcrunch.gif)

# Geek Uninstaller

[Geek Uninstaller](https://geekuninstaller.com/) 可以在卸载应用时顺便清理残留的文件和注册表。使用命令安装：

```shell
scoop install geekuninstaller
```

![Geek Uninstaller](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/geekuninstaller_screen.png)

# Figma

[Figma](https://www.figma.com/downloads/) 是一个 Web UI/UX 设计软件，对标的是 [Sketch](https://sketchapp.com)，但 Sketch 只支持 macOS，Figma 因为可以运行在浏览器中，所以可以跨平台。而且 Figma 可以免费使用，虽然功能有受限。

![Figma](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/figma-canvas.png)

# Axure

[Axure](https://www.axure.com/download) 是国内产品经理必备的工具，用于快速原型设计。

![Axure 9](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/Axure_9.png)

# Affinity Photo

[Affinity Photo](https://store.serif.com/zh-cn/update/windows/photo/1/) 是对标 Photoshop 的产品，比 Photoshop 更易使用，性能更优。

![Affinity Photo](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/photo_1.7_focusstack_windows.png)

# Affinity Designer

[Affinity Designer](https://store.serif.com/zh-cn/update/windows/designer/1/) 是对标 Illustrator 的产品，比 Illustrator 更易使用，性能更优。

![Affinity Designer](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/designer_1.7_artboards_windows.png)

# Affinity Publisher

[Affinity Publisher](https://store.serif.com/zh-cn/update/windows/publisher/1/) 是对标 InDesign 的产品，比 InDesign 更易使用，性能更优，但功能暂时比 InDesign 少，对中文排版支持不太好。

![Affinity Publisher](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/CHN-Windows-Affinity-Publisher-MasterPages.jpg)

# VirtualBox

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) 是免费开源的虚拟机，支持各桌面操作系统。也可以使用同样免费的 [VMWare Workstation Player](https://www.vmware.com/products/workstation-player.html)。

![在 Windows VirtualBox 中运行 Ubuntu 14.04](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/Ubuntu_14.04_on_Windows_7.png)

# Sizer

[Sizer](http://www.brianapps.net/sizer4/) 可以将应用窗口设定为固定的大小。在你要截图一个应用时，你可以先把窗口调整好大小，这样截出来的图无需再去裁剪。

![Sizer](https://cdn.jsdelivr.net/gh/duzyn/img/images/2020-06-12-windows-apps/sizer.png)
