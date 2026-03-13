---
title: 在VScode中设置javascript和typescript项目环境
date: 2026-03-13
layout: single
author_profile: true
categories:
  - Blog
tags:
  - Typescript
  - Javascript
  - VScode
---

<!-- # Windows 下 JavaScript / TypeScript 开发环境配置（VSCode） -->

## 一、环境背景

在学习 **JavaScript / TypeScript** 时，需要配置以下开发环境：

* Node.js
* npm
* TypeScript
* VSCode

本文记录在 **Windows + VSCode** 环境下，从 **Node.js 安装到 TypeScript 项目创建与测试** 的完整过程。

---

# 二、安装 Node.js

首先安装 **Node.js**。

官网：

```
https://nodejs.org
```

安装完成后，在终端测试：

```bash
node -v
```

输出示例：

```
v24.14.0
```

再测试 npm：

```bash
npm -v
```

输出示例：

```
11.9.0
```

如果两个命令都能正常输出版本号，说明 Node 环境安装成功。

---

# 三、创建 TypeScript 项目
![alt text](/assets/blog_picture/image3.png)

在项目目录中创建一个 TypeScript 项目。

## 1 创建项目文件夹

```bash
mkdir ts_project
cd ts_project
```

目录结构：

```
ts_project
```

---

## 2 初始化 npm 项目

执行：

```bash
npm init -y
```

该命令会自动生成 `package.json`。

示例：

```json
{
  "name": "ts_project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "license": "ISC",
  "type": "commonjs"
}
```

`package.json` 是 Node 项目的配置文件。

---

## 3 本地安装 TypeScript

安装 TypeScript：

```bash
npm install typescript --save-dev
```

安装成功后终端显示：

```
added 1 package in 1s
```

项目目录变成：

```
ts_project
│
├── node_modules
│   └── typescript
│
├── package.json
└── package-lock.json
```

说明 **TypeScript 已经成功安装到当前项目中**。

---

# 四、验证 TypeScript 环境

## 1 查看 TypeScript 版本

运行：

```bash
npx tsc -v
```

输出示例：

```
Version 5.x.x
```

说明 TypeScript 编译器可用。

---

## 2 创建 TypeScript 测试文件

创建文件：

```
index.ts
```

写入代码：

```ts
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(2, 5));
```

---

## 3 编译 TypeScript

运行：

```bash
npx tsc index.ts
```

成功后会生成：

```
index.js
```

---

## 4 运行 JavaScript

运行：

```bash
node index.js
```

输出：

```
7
```

说明：

* TypeScript 编译正常
* Node.js 运行正常
* 项目环境配置成功

---

# 五、完整环境测试

如果以下命令全部运行成功，则说明环境配置完成：

```bash
node -v
npm -v
npx tsc -v
node index.js
```

测试结果示例：

```
v24.14.0
11.9.0
Version 5.x.x
7
```

---

# 六、最终项目结构

完成配置后，项目结构如下：

```
ts_project
│
├── node_modules
│
├── index.ts
├── index.js
│
├── package.json
├── package-lock.json
```

---

# 七 问题解决


你会在输入

```bash
npm install typescript --save-dev 
```

有时可能会出现 EPERM 权限错误，类似如下问题：
![alt text](/assets/blog_picture/image2.png)

出现该问题的原因通常是 当前用户没有 Program Files 目录的写入权限。
Windows 系统默认对该目录进行了权限限制，因此在安装 npm 依赖时可能会被拒绝访问。

以管理员模式打开powershell,进入 TypeScript 项目的目录,输入

```bash
cd D:\vscode_project\JavaScriptProject\jsLearning\ts_project
```

具体代码参考如下

```text

Windows PowerShell
版权所有（C） Microsoft Corporation。保留所有权利。

安装最新的 PowerShell，了解新功能和改进！https://aka.ms/PSWindows

加载个人及系统配置文件用了 1835 毫秒。
(base) PS C:\WINDOWS\system32> cd D:\vscode_project\JavaScriptProject\jsLearning\ts_project
(base) PS D:\vscode_project\JavaScriptProject\jsLearning\ts_project> npm install typescript

added 1 package in 1s


```



# 八、总结

本文完成了以下环境配置：

1. 安装 Node.js 和 npm
2. 创建 TypeScript 项目
3. 本地安装 TypeScript
4. 编译并运行 TypeScript 程序
5. 配置 VSCode 开发环境

通过这些步骤，可以搭建一个完整的 **JavaScript / TypeScript 开发环境**。

---

如果需要继续学习 TypeScript，可以进一步了解：

* TypeScript 类型系统
* ES6 模块
* Node.js + TypeScript 项目结构
* 前端框架（React + TypeScript）

---

