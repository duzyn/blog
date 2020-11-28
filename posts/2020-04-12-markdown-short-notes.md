---
title: Markdown 简明笔记
author: David Peng
date: 2020-04-12
---

Markdown 是一种轻量级的文本标记语言，使用简单的纯文本格式的语法编写文档，然后转换成 HTML 和其他格式的文档。Markdown 由 John Gruber 和 Aaron Swartz 在 2004 年创造，这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。目前已经广泛地使用在 README 文件、发帖或使用纯文本格式生成富文本格式的文字编辑器中。

# Markdown 介绍

Markdown 的主旨是尽可能的可读性，文本应该能直接被阅读，而不需要使用格式化指令来标记（像 RTF 与 HTML）。Markdown 同时是一个 Perl 软件，用来转换 Markdown 格式的文本为 HTML，你可以在 John Gruber 的博客查看[初始的 Markdown 语法](https://daringfireball.net/projects/markdown/)。

# Markdown 语法

Markdown 语法最关注的是可读性，其借鉴了很多已存在的文本转 HTML 的格式语法：Setext, atx, Textile, reStructuredText, Grutatext 和 EtText。

Markdown 文档就是普通的文本文档，只是以 Markdown 的语法标记了一些特殊排版段落。Markdown 的语法并不复杂，网上有很多介绍，读者可以参考以下地方学习 Markdown 更多语法：

- [Mastering Markdown(HTML 版本)](https://guides.github.com/features/mastering-markdown/)
- [Mastering Markdown(PDF 版本)](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)
- [Markdown 速查](https://www.markdownguide.org/cheat-sheet/)

# Markdown 扩展语法

Markdown 语法实现的基本的文档元素的标记，但部分元素例如表格、数学公式、交叉引用、定义列表等没有实现。所以出现了各种 Markdown 变体，比较知名的变种有以下几种：

- [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/)
- [Github Flavored Markdown](https://github.github.com/gfm/)：依靠 Github 的流行，GFM 可能是最流行的 Markdown 扩展语法了。
- [CommonMark](http://spec.commonmark.org/)：CommonMark 是 Pandoc 的作者 John MacFarlane 创造的语法，其融合了 PHP Markdown Extra、GFM、MultiMarkdown 等各种 Markdown 扩展语法，可谓集大成者。Github 也要转向 CommonMark。

# 使用 Pandoc 转换 Markdown 文档

[Pandoc](http://pandoc.org) 是一个在多种标记语言间相互转换的通用工具，可以在常见的 Markdown、HTML、PDF、EPUB、DOCX 等格式间相互转换。

Pandoc 的基本用法为：

```sh
pandoc FILE [OPTIONS]
```

Pandoc 有很多选项，完整用法可以参加其 [用户手册](http://pandoc.org/MANUAL.html)。

# 使用 pp 预处理 Markdown 文档

[pp](https://github.com/CDSoft/pp) 是一个预处理工具，我们可以用它来预处理Markdown 文档，扩充 Markdown 的功能。然后用 Pandoc 转换预处理过后的 Markdown 文档。

pp 是以宏的方式扩展语法的，我们可以自定义一些宏，把 Markdown 各种扩展语法中不支持的语法加入。

如果我们要加入下划线的语法，可以定义一个这样的 HTML 的宏：`!define(u)(<u>!1</u>)` 和 LaTeX 的宏 `!define(u)(\underline{!1})`，例如 `!u(下划线的文字)` 的输出结果为 <u>下划线的文字</u>。

更多用法可以参考：

- [pp 官网](https://cdsoft.fr/pp/index.html)
- [Tufte Markdown](https://github.com/duzyn/tufte-markdown)：一个使用 pp 来定义 Tufte 样式的宏的项目。

# Markdown 编辑器

学会了 Markdown 的语法后，需要用文本编辑器编辑 Markdown。可以直接用记事本来编辑 Markdown 文档，但是有一个支持语法高亮的文本编辑起来会顺手一些，我尝试过很多 Markdown 编辑器，以下是我推荐的几个。

- [Visual Studio Code](https://code.visualstudio.com/)：严格来说，Code 是代码编辑器，并非是专门编辑 Markdown的。但是其对 Markdown 非常好的支持，外加丰富的插件，绝对可以替代很多收费的编辑器。
- [iA Writer](https://ia.net/writer/)：付费的 Markdown 编辑器中，iA Writer 是功能强大又设计简洁的典范。支持 Windows、macOS、iOS、Android 四大平台，完善的文档管理、云同步、Markdown 键盘、美观的主题，值得拥有。

使用 Code 的话，推荐装上这两个插件：

- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)：Markdown 语法检查，提醒自己时刻书写正确、规范、一致的 Markdown。也适合用于团队共同维护 Markdown 文档资料时。
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)：Markdown 的瑞士军刀，帮助你提高应用语法、插入列表、生成目录、粘贴链接、格式化表格的速度。

# Markdown 相关资源

- [awesome-markdown](https://github.com/mundimark/awesome-markdown)：收集了一系列 Markdown 相关的资源。
