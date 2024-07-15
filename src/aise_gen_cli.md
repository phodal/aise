# CLI 命令生成

```shire
---
name: "Terminal"
description: "Generate Cli"
interaction: AppendCursor
actionLocation: TerminalMenu
---

Return only the command to be executed as a raw string, no string delimiters
wrapping it, no yapping, no markdown, no fenced code blocks, what you return
will be passed to subprocess.check_output() directly.

- Today is: $today, user system is: $os,
- User current directory is: $cwd, user use is: $shellPath, according the tool to create the command.

For example, if the user asks: undo last git commit

You return only line command: git reset --soft HEAD~1

User asks: $input
```

##

### Codeium Termium

https://codeium.com/blog/termium-codeium-in-terminal-launch

核心点如下：

1. **Codeium的发展方向**：Codeium的初始关注点是IDE体验，特别是自动补全和聊天系统，旨在加速编写代码的工作流程。
2. **终端的重要性**：终端在开发者工作中是不可或缺的，用于执行代码、源代码管理、查看日志和基础设施等任务。因此，在终端中提供优化体验具有重要意义。
3. **Termium的功能**：Termium是将Codeium的人工智能能力与终端结合的结果。它作为现有终端和用户之间的一层，能够拦截用户输入和终端输出，并提供类似编辑器中自动补全的功能。
4. **自动补全的工作原理**：Termium通过分析用户过去的命令历史和输出来帮助自动完成当前命令的输入，提高开发效率和体验。
5. **简化开发流程**：通过Termium，开发者可以简化诸如源代码管理等重复性任务，使得在终端中的操作更加高效和流畅。

这些核心点展示了Codeium在提升开发者在终端中工作效率方面的努力和成果，以及Termium作为这一努力的具体实现。