---
title: Tufte 样式 Markdown
author: David Peng
date: 2020-04-11
---

Tufte 样式在 Edward Tufte 的书以及物理学家费曼的教科书很常见，它的一个显著特点就是边栏的使用。例如脚注和边栏附注，以及放在边栏里的小型插图。Tufte 样式在 LaTeX 和 HTML/CSS 中都有实现。

Tufte 样式 Markdown 使用了一系列工具，实现了用 Markdown 语法写作，并导出为 Tufte 样式排版的网页或印刷文章。

# 用法

先使用 Markdown 语法编辑文档，中间插入 [pp](https://github.com/CDSoft/pp) 宏，然后使用 pp 将带宏的 Markdown 转换为普通的 Markdown 文档，把结果管道输出给 [Pandoc](https://pandoc.org)，Pandoc 使用模板转换为 HTML 或 LaTeX 文档。

查看 Tufte 样式 Markdown 定义的宏列表：[tufte-markdown.pp](https://github.com/duzyn/tufte-markdown/blob/master/tufte-markdown.pp)。

查看将带宏的 Markdown 转换为 HTML 或 LaTeX 文档的示例：[build.sh](https://github.com/duzyn/tufte-markdown/blob/master/build.sh)

# 阅读更多

- [Tufte LaTeX](https://tufte-latex.github.io/tufte-latex/)
- [Tufte CSS](https://edwardtufte.github.io/tufte-css/)
- [RStudio Tufte Handout](https://rstudio.github.io/tufte/)
- [R Markdown Tufte Style](https://rstudio.github.io/tufte/cn/)
- [RStudio Pandoc template: tufte-handout.tex](https://raw.githubusercontent.com/rstudio/tufte/master/inst/rmarkdown/templates/tufte_handout/resources/tufte-handout.tex)
