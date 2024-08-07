# AI 辅助软件工程：提交信息与研发数字化

## 理解

## 合理的提交信息

```shire
---
name: "Commit message"
description: "生成提交信息"
interaction: AppendCursor
actionLocation: CommitMenu
---

为给定的变更（Diff）编写一个连贯但具有描述性的代码提交信息。

- 确保包含修改了什么以及为什么。
- 以不超过 50 个字符的祈使句形式开头。
- 然后留下一个空行，如有必要，继续详细说明。
- 说明应该少于 200 个字符。

遵循常规提交规范，例如：

- fix(authentication): 修复密码正则表达式模式问题
- feat(storage): 添加对S3存储的支持
- test(java): 修复用户控制器的测试用例
- docs(architecture): 在主页添加架构图

Diff：

$currentChanges
```

### JetBrains 示例

提交信息：

    Your task is to generate a well-read summary of changes made in the project.
    The paragraph should have less than 10 sentences and less than 300 words. Summarize the following commit messages.

    Given the below code differences (diffs), please generate a concise, clear, and straight-to-the-point commit message.
    Make sure to prioritize the main action.
    Avoid overly verbose descriptions or unnecessary details.
    Start with a short sentence in imperative form, no more than 50 characters long.
    Then leave an empty line and continue with a more detailed explanation.
    Write only one sentence for the first part, and two or three sentences at most for the detailed explanation.


