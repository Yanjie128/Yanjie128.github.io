---
layout: post
title: "使用 LaTeX 完成本科毕业论文"
date: 2026-03-12
categories: blog
tags: [latex, thesis, vscode]
---

# 使用Latex 解决毕业设计头痛问题

2026.03.12

最近准备使用latex完成本科毕业设计。但是发现学校提供的开源latex模板不太容易入门，因此通过这一篇博客讲述一下如何初始化毕设。

你需要准备的软件，有vscode，从清华源下载的texlive2026.iso，还有一些VSCode的插件。希望这一篇博客对你的毕业设计有所帮助。

我给你整理成一篇 **结构完整、可直接发布的技术 Blog**（适合发在 CSDN / 博客园 / 知乎 / 个人博客）。内容包括问题、原因、解决方案和最佳实践。

---

# VSCode 编译 HEUThesis 论文模板报错：`I can't find file main.tex` 解决方法

在使用 **哈尔滨工程大学 LaTeX 论文模板（HeuThesis）** 时，很多人在 VSCode 终端编译会遇到类似报错：

```text
! I can't find file 'main.tex'.
```

或者

```text
! I can't find file 'heuthesis.ins'.
```

本文记录问题原因及解决方案。

---

# 一、问题现象

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

（这里可以放你的截图）

---

# 二、问题原因

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

### main.tex 实际位置

```
heuthesis-master/examples/book/bachelor/main.tex
```

如果你在 **上层目录执行编译**：

```bash
xelatex main.tex
```

LaTeX 自然找不到文件。

---

# 三、解决方案

## 方法一：进入正确目录（推荐）

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

---

## 方法二：直接指定路径

也可以直接编译指定路径：

```bash
xelatex examples/book/bachelor/main.tex
```

但不推荐这种方式。

---

# 四、HEUThesis 正确编译流程

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

# 五、VSCode 推荐配置（一键编译）

如果你安装了 **LaTeX Workshop 插件**，可以直接一键编译。

快捷键：

```
Ctrl + Alt + B
```

默认流程：

```
xelatex → biber → xelatex → xelatex
```

这样就不用每次手动输入命令。

---

# 六、常见错误总结

| 错误                                | 原因         | 解决                  |
| --------------------------------- | ---------- | ------------------- |
| `I can't find file main.tex`      | 终端路径不对     | 进入 main.tex 所在目录    |
| `I can't find file heuthesis.ins` | 不在模板根目录    | 进入 heuthesis-master |
| 中文乱码                              | 没用 xelatex | 使用 xelatex 编译       |
| 参考文献不显示                           | 没运行 biber  | 按完整流程编译             |

---

# 七、最佳实践（推荐流程）

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

```
Ctrl + Alt + B
```

---

# 八、总结

HEUThesis 模板编译失败，大多数情况下不是 LaTeX 问题，而是 **终端路径错误**。

只要保证：

```
在 main.tex 所在目录执行 xelatex
```

基本都可以正常编译。

---

如果需要，我还可以帮你再写一篇 **进阶版技术 Blog**：

* 《VSCode + LaTeX Workshop 配置 HEUThesis 模板完整指南》
* 《HEU Thesis 模板从下载到编译完整教程》
* 《LaTeX 论文写作环境 10 分钟搭建指南》

我可以帮你整理成 **一篇完整高质量技术文章（阅读量很高那种）**。
