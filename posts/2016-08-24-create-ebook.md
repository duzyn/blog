---
title: 制作电子书
author: David Peng
date: 2016-08-24
---

# Pandoc 转换电子书

Pandoc 转换电子书的命令：

    pandoc FILE -o FILE.epub \
        -f markdown+east_asian_line_breaks \
        -t epub \
        --template=ebook.html \
        --toc --toc-depth=2 \
        --epub-stylesheet=ebook.css \
        --epub-cover-image=cover.jpg

# 排版格式

封面：以 JPEG 或 PNG 格式，大小为 1600x2560，350 PPI。这样的封面在 PPI 较大的设备上也能清晰显示。图片大小不应大于 5M。

字体：不要使用自定义的中文字体，使用阅读器自带的字体就好。中文字体一般很大，不适合嵌入电子书。英文字体较小，则可以考虑嵌入，以创造更好的阅读体验。

行距：不要自定义行距。阅读器可以设置全局行距，用户可以根据自己的偏好调节。

字体大小：不要自定义字体大小。阅读器可以设置字体大小。

背景色、前景色：不要自定义。阅读器来控制就好。

间距：不要设置 `body` 的外间距。阅读器来控制就好。

段落间距：段后间距一行或不留。

首行缩进：中文段落首行缩进两字，用中文空格表示。英文段落缩进用 `text-indent:2`

目录：应同时包含逻辑目录和 HTML 目录。逻辑目录用于阅读器的导航，HTML 目录用于在电子书的开头。使用 Pandoc 的 `--toc` 选项可以生成 HTML 目录。目录应在书首而不是书尾。

# 元数据

电子书的元数据一般有以下几个：

- 标题：title，电子书的标题。
- 副标题：subtitle，电子书的副标题。
- 作者：author，书籍作者。
- 创建者：creator，电子书创建者。
- 出版者：publisher，电子书的出版者。
- 版权：rights，电子书的版权。

校验电子书：使用 EpubCheck 来校验 EPUB 电子书。

使用默认的正文字体、字体大小、行距、字体颜色、背景色等，因为自定义的正文字体会覆盖阅读器的设置。

使用 CSS `page-break-before` 和 `page-break-after` 来断页。例如：

    h1 {
      page-break-after: always;
    }

使用 `text-indent` 来首行缩进。例如：

    p {
      text-indent: 2em;
      margin: 1em 0;
    }

不要使用绝对单位，比如点或像素，而应使用相对单位，比如 % 或 em。行距要大于 1.2 或 120%。

字体应在 `body` 级别设置。

图片：300 PPI，GIF、BMP、JPEG、PNG、SVG 格式，RGB 色。最大 5 MB。照片用 JPEG 格式。矢量图片或文字图片用 GIF 或 PNG 格式，最大 127 KB。
