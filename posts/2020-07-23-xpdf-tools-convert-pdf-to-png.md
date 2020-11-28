---
title: 使用 Xpdf 将 PDF 转为 PNG 图片
author: David Peng
date: 2020-07-23
---

[Xpdf](https://www.Xpdfreader.com/about.html) 是免费开源的 PDF 处理工具，本文介绍使用 pdftopng 将 PDF 转为 PNG 图片。

# 下载安装 Xpdf

Xpdf 是命令行工具，有两种安装方式：

1. 使用 Scoop 安装：`scoop install xpdf-tools`。推荐使用此方法。
2. 手动安装：在 [Xpdf 下载页面](https://www.xpdfreader.com/download.html) 下载 Windows 32/64 位的版本，下载的文件名为类似 xpdf-tools-win-4.02.zip，解压缩到一个路径下即可，例如解压缩到 C:\

# 配置 Xpdf

Xpdf 的配置都在 [xpdfrc 文件](https://www.xpdfreader.com/xpdfrc-man.html) 中，官网有详细的介绍。

在上一步下载的压缩包中的 doc 目录下有个 sample-xpdfrc 文件，将此文件复制到 xpdf 可执行文件的路径下（pdftopng.exe 所在的路径下），并复制一份重命名为 xpdfrc，原有的 sample-xpdfrc 文件留做备用。可以发现样例文件中的所有项都是注释掉的。我们找到需要修改的地方，取消注释，并修改配置即可。

需要做的配置有两项：

一、配置 Type 1 字体 Symbol 和 Zapf Dingbats。

在 [Xpdf 下载页面](https://www.xpdfreader.com/download.html) 下载 Symbol 和 Zapf Dingbats 字体，下载的文件名为类似 xpdf-t1fonts.tar.gz，使用 7Zip 将文件解压缩到 xpdf 可执行文件的路径下。例如解压到 xpdf-t1fonts 目录下。

找到设置 Symbol 和 Zapf Dingbats 两行，取消注释，并修改字体文件的路径

```
# Before
#fontFile Symbol            /usr/local/share/ghostscript/fonts/s050000l.pfb
#fontFile ZapfDingbats      /usr/local/share/ghostscript/fonts/d050000l.pfb

# After
fontFile Symbol             ./xpdf-t1fonts/s050000l.pfb
fontFile ZapfDingbats       ./xpdf-t1fonts/d050000l.pfb
```

二、配置中文语言支持包。

在 [Xpdf 下载页面](https://www.xpdfreader.com/download.html) 下载中文语言支持包，下载的文件名为类似 xpdf-chinese-simplified.tar.gz，使用 7Zip 将文件解压缩到 xpdf 可执行文件的路径下。例如解压到 xpdf-chinese-simplified 目录下。

将 add-to-xpdfrc 文件中的内容拷贝到 xpdfrc 的最下方，并修改文件的路径。取消 fontFileCC 行的注释，下载 [NotoSansCJKsc-Regular.otf](https://github.com/googlefonts/noto-cjk/raw/master/NotoSansCJKsc-Regular.otf) 字体到 xpdf-chinese-simplified 目录下，并修改文件的路径。

```
# Before
#----- begin Chinese Simplified support package (2011-sep-02)
#cidToUnicode  Adobe-GB1     /usr/local/share/xpdf/chinese-simplified/Adobe-GB1.cidToUnicode
#unicodeMap    ISO-2022-CN   /usr/local/share/xpdf/chinese-simplified/ISO-2022-CN.unicodeMap
#unicodeMap    EUC-CN        /usr/local/share/xpdf/chinese-simplified/EUC-CN.unicodeMap
#unicodeMap    GBK           /usr/local/share/xpdf/chinese-simplified/GBK.unicodeMap
#cMapDir       Adobe-GB1     /usr/local/share/xpdf/chinese-simplified/CMap
#toUnicodeDir                /usr/local/share/xpdf/chinese-simplified/CMap
#fontFileCC   Adobe-GB1      /usr/..../NotoSansCJKsc-Regular.otf
#----- end Chinese Simplified support package

# After
#----- begin Chinese Simplified support package (2011-sep-02)
cidToUnicode  Adobe-GB1      ./xpdf-chinese-simplified/Adobe-GB1.cidToUnicode
unicodeMap    ISO-2022-CN    ./xpdf-chinese-simplified/ISO-2022-CN.unicodeMap
unicodeMap    EUC-CN         ./xpdf-chinese-simplified/EUC-CN.unicodeMap
unicodeMap    GBK            ./xpdf-chinese-simplified/GBK.unicodeMap
cMapDir       Adobe-GB1      ./xpdf-chinese-simplified/CMap
toUnicodeDir                 ./xpdf-chinese-simplified/CMap
fontFileCC    Adobe-GB1      ./xpdf-chinese-simplified/NotoSansCJKsc-Regular.otf
#----- end Chinese Simplified support package
```

完整的 xpdfrc 文件可查看 [xpdfrc](https://cdn.jsdelivr.net/gh/duzyn/img/xpdfrc)。

# 使用 pdftopng 将 PDF 转换为 PNG

pdftopng 的 [官网手册](https://www.xpdfreader.com/pdftopng-man.html) 对使用有详细的介绍。基本的使用方法是

```
pdftopng example.pdf example
```

假如 example.pdf 文档有两页，则会将其转换为 example-000001.png 和 example-000002.png 两个图片，分别是 PDF 文件的两页。
