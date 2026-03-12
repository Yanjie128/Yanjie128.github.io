---
title: 使用 Latex 解决毕业设计问题
date: 2026-03-12
layout: single
author_profile: true
categories:
  - Blog
tags:
  - Latex
  - Thesis
---

2026.03.12

最近准备使用Latex完成本科毕业设计。但是发现学校提供的开源Latex模板不太容易入门，因此通过这一篇博客讲述一下如何初始化毕设模板。

需要准备的内容有:

- VScode
- 下载[清华源texlive2026.iso](https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/Images/)
- VSCode的插件[Latex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- 获取学校的Latex模板，这里采用[HEU-Latex-主题](https://github.com/Li-Wenhui/HeuThesis.git)

关于texlive2026.iso的安装，网上有很多参考资料，这里不过多赘述。需要注意:

- 修改安装根目录，我选择的是D盘
- 取消勾选安装TeXwords前端
- 在Advance中，选择中文，英文或者你需要的其他语言

希望这一篇博客对你的毕业设计有所帮助

为了在VScode中配置LaTex设置,需要在setting中打开.json, 输入以下内容:

```text

  "latex-workshop.latex.autoBuild.run": "never",
  "latex-workshop.showContextMenu": true,
  "latex-workshop.intellisense.package.enabled": true,
  "latex-workshop.message.error.show": false,
  "latex-workshop.message.warning.show": false,
  "latex-workshop.latex.tools": [
      {
          "name": "xelatex",
          "command": "xelatex",
          "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOCFILE%"
          ]
      },
      {
          "name": "pdflatex",
          "command": "pdflatex",
          "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "%DOCFILE%"
          ]
      },
      {
          "name": "latexmk",
          "command": "latexmk",
          "args": [
              "-synctex=1",
              "-interaction=nonstopmode",
              "-file-line-error",
              "-pdf",
              "-outdir=%OUTDIR%",
              "%DOCFILE%"
          ]
      },
      {
          "name": "bibtex",
          "command": "bibtex",
          "args": [
              "%DOCFILE%"
          ]
      }
  ],
  "latex-workshop.latex.recipes": [
      {
          "name": "XeLaTeX",
          "tools": [
              "xelatex"
          ]
      },
      {
          "name": "PDFLaTeX",
          "tools": [
              "pdflatex"
          ]
      },
      {
          "name": "BibTeX",
          "tools": [
              "bibtex"
          ]
      },
      {
          "name": "LaTeXmk",
          "tools": [
              "latexmk"
          ]
      },
      {
          "name": "xelatex -> bibtex -> xelatex*2",
          "tools": [
              "xelatex",
              "bibtex",
              "xelatex",
              "xelatex"
          ]
      },
      {
          "name": "pdflatex -> bibtex -> pdflatex*2",
          "tools": [
              "pdflatex",
              "bibtex",
              "pdflatex",
              "pdflatex"
          ]
      },
  ],
  "latex-workshop.latex.clean.fileTypes": [
      "*.aux",
      "*.bbl",
      "*.blg",
      "*.idx",
      "*.ind",
      "*.lof",
      "*.lot",
      "*.out",
      "*.toc",
      "*.acn",
      "*.acr",
      "*.alg",
      "*.glg",
      "*.glo",
      "*.gls",
      "*.ist",
      "*.fls",
      "*.log",
      "*.fdb_latexmk"
  ],
  "latex-workshop.latex.autoClean.run": "onFailed",
  "latex-workshop.latex.recipe.default": "lastUsed",
  "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click"

```

---

#### HeuThesis 模板初始化与编译教程

在下载并解压 **HeuThesis LaTeX 论文模板**之后，需要进行一次初始化操作，才能正常编译毕业论文。下面介绍完整的初始化流程。

---

#### 1 解压模板并打开项目

首先下载 HeuThesis 模板压缩包，并将其解压到本地目录。

解压完成后，使用 VSCode 打开该文件夹：

```css
File → Open Folder
```

选择解压后的 `heuthesis-master` 目录。

---

#### 2 打开终端

在 VSCode 中打开终端：

```css
Terminal → New Terminal
```

此时终端的工作目录应该位于项目根目录：

```css
heuthesis-master
```

---

#### 3 生成模板类文件

在项目根目录中可以看到一个文件：

```css
heuthesis.ins
```

该文件用于生成论文模板的核心类文件 `heuthesisbook.cls`。

首先,新建一个terminal,在终端中输入:

```bash
cd heuthesis-master
```

进入跟文件夹后, 在终端中运行:

```bash
xelatex heuthesis.ins
```

执行完成后，会生成如下文件：

```css
heuthesisbook.cls
```

该 `.cls` 文件是论文模板正常编译所必需的。

---

#### 4 进入示例论文目录

模板中提供了示例论文，路径为：

```css
examples/book/bachelor
```

在终端中进入该目录：

```bash
cd examples/book/bachelor
```

---

#### 5 编译论文示例

在该目录下可以看到论文主文件：

```css
main.tex
```

使用 `xelatex` 进行编译：

```bash
xelatex main.tex
```

如果编译成功，会生成以下文件：

```css
main.pdf
```

此时即可打开 PDF 预览论文效果。

---

#### 6 预览论文

生成 PDF 后，可以直接在 VSCode 或 PDF 阅读器中打开：

```css
main.pdf
```

查看论文模板的排版效果。

---

#### 7 初始化完成

至此，HeuThesis 模板的初始化步骤基本完成。后续只需要在 `main.tex` 及相关章节文件中修改内容，即可开始撰写自己的毕业论文。

---

#### 总结

整个初始化流程可以总结为以下几个步骤：

1. 下载并解压 HeuThesis 模板
2. 使用 VSCode 打开项目目录
3. 在终端执行 `latex heuthesis.ins` 生成模板类文件
4. 进入 `examples/book/bachelor` 示例目录
5. 使用 `xelatex main.tex` 编译示例论文
6. 打开生成的 PDF 进行预览

完成以上步骤后，LaTeX 论文模板即可正常使用。

---

### VSCode 编译 HEUThesis 论文模板报错：`I can't find file main.tex` 解决方法

在使用HeuThesis时，很多人在 VSCode 终端编译会遇到类似报错😡:

```text
! I can't find file 'main.tex'.
```

或者

```text
! I can't find file 'heuthesis.ins'.
```

本文记录问题原因及解决方案。

---

#### 1、问题现象

在 VSCode 终端运行：

```bash
xelatex main.tex
```

终端报错：

```text
! I can't find file 'main.tex'.
```

或者：

```text
! I can't find file 'heuthesis.ins'.
```

如下图所示：

![alt text](/assets/blog_picture/image.png)

---

#### 2、问题原因

问题 **几乎 100% 是因为当前终端路径不正确**。

HeuThesis 模板的目录结构如下：

```text
HeuThesis-master
│
└─ heuthesis-master
    │
    ├─ heuthesis.ins
    │
    └─ examples
        ├─ art
        └─ book
            └─ bachelor
                ├─ main.tex
                ├─ thesis.tex
                ├─ reference.bib
                └─ figures
```

可以看到：

#### main.tex 实际位置

```text
heuthesis-master/examples/book/bachelor/main.tex
```

如果你在 **上层目录执行编译**：

```bash
xelatex main.tex
```

LaTeX 自然找不到文件。

---

#### 3、解决方案

#### 方法一：进入正确目录（推荐）

先进入 `main.tex` 所在目录：

```bash
cd examples/book/bachelor
```

然后编译：

```bash
xelatex main.tex
```

完整示例：

```bash
cd D:\Mi Yanjie\Documents\HeuThesis-master\heuthesis-master\examples\book\bachelor
xelatex main.tex
```

参考这个terminal界面就是成功编译的状态

![参考这个terminal界面就是成功编译的状态](/assets/blog_picture/image1.png)

---

#### 方法二：直接指定路径

也可以直接编译指定路径：

```bash
xelatex examples/book/bachelor/main.tex
```

但不推荐这种方式。

---

#### 4、HEUThesis 正确编译流程

论文模板一般需要 **多次编译**：

```bash
xelatex main
biber main
xelatex main
xelatex main
```

原因：

| 命令      | 作用     |
| ------- | ------ |
| xelatex | 生成基础文档 |
| biber   | 处理参考文献 |
| xelatex | 更新引用   |
| xelatex | 最终排版   |

---

#### 5、VSCode 推荐配置（一键编译）

如果你安装了 **LaTeX Workshop 插件**，可以直接一键编译。

快捷键：

```text
Ctrl + Alt + B
```

默认流程：

```text
xelatex → biber → xelatex → xelatex
```

这样就不用每次手动输入命令。

---

#### 6、常见错误总结

| 错误                                | 原因         | 解决                  |
| --------------------------------- | ---------- | ------------------- |
| `I can't find file main.tex`      | 终端路径不对     | 进入 main.tex 所在目录    |
| `I can't find file heuthesis.ins` | 不在模板根目录    | 进入 heuthesis-master |
| 中文乱码                              | 没用 xelatex | 使用 xelatex 编译       |
| 参考文献不显示                           | 没运行 biber  | 按完整流程编译             |

---

#### 7、最佳实践（推荐流程）

1️⃣ 进入论文目录

```bash
cd examples/book/bachelor
```

2️⃣ 编译

```bash
xelatex main
biber main
xelatex main
xelatex main
```

3️⃣ 或使用 VSCode

```text
Ctrl + Alt + B
```

---

#### 8、总结

HEUThesis 模板编译失败，大多数情况下不是 LaTeX 问题，而是 **终端路径错误**。

只要保证：

```text
在 main.tex 所在目录执行 xelatex
```

基本都可以正常编译。

---

#### 9、参考

- [HeuThesis 官方仓库](https://github.com/Li-Wenhui/HeuThesis.git)

- LaTeX Workshop 插件文档