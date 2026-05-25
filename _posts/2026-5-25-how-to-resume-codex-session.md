在 WSL 里面继续之前的 Codex CLI 对话，通常直接用下面几个命令即可：

```bash
codex resume
```

会打开历史会话选择器，你可以选之前的对话继续。 ([Verdent AI][1])

如果想直接继续最近一次会话：

```bash
codex resume --last
```

或者新版也支持：

```bash
codex continue
```

继续当前目录最近的会话。 ([Verdent AI][1])

如果发现“看不到之前的会话”，尤其是在 WSL 下，通常是下面几个原因：

### 1. 当前目录不对（最常见）

新版 Codex 会按当前工作目录过滤历史会话。

解决：

```bash
codex resume --all
```

这样会显示所有历史会话，不管在哪个目录创建的。 ([GitHub][2])

---

### 2. Windows 和 WSL 的会话不共享

Windows 原生安装的 Codex 和 WSL 中安装的 Codex：

* 会话目录不同
* 配置不同
* 登录状态也可能不同

WSL 默认会话目录：

```bash
~/.codex/sessions/
```

里面保存了所有聊天记录（jsonl 文件）。 ([CSDN博客][3])

你可以查看：

```bash
ls ~/.codex/sessions/
```

---

### 3. 指定 session id 继续

如果你知道 session id：

```bash
codex continue <session-id>
```

或者：

```bash
codex resume <session-id>
```

session id 可以在：

```bash
~/.codex/sessions/
```

里找到。 ([Verdent AI][1])

---

### 推荐工作流（WSL）

平时建议：

```bash
cd 你的项目目录
codex
```

下次继续：

```bash
cd 同一个项目目录
codex continue
```

这样最稳定。

---

<!-- 另外，如果你想，我还可以教你： -->

* 如何让 VS Code + WSL 共用 Codex 会话
* 如何把 Windows 的 Codex 会话迁移到 WSL
* 如何搜索历史聊天内容
* 如何导出 Codex 对话为 markdown
* 如何自动恢复上次 session

这些在 WSL 开发里都挺实用。

[1]: https://www.verdent.ai/zh-CN/guides/codex-cli-resume-continue-save-chat?utm_source=chatgpt.com "Codex CLI Resume, Continue, and Save Chat Explained ..."
[2]: https://github.com/openai/codex/issues/6927?utm_source=chatgpt.com "Resume a previous session not working on WSL Ubuntu #6927"
[3]: https://blog.csdn.net/m0_63223824/article/details/160217414?utm_source=chatgpt.com "Windows 通过 WSL 配置 Codex CLI - CSDN博客"
