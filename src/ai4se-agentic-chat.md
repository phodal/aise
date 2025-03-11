# Agentic chat

## 示例

### Sourcegraph - 深思熟虑，精准回答

Agentic Chat（自主智能聊天）能够主动收集、审查并优化相关上下文，以提供高质量、上下文感知的回答。它减少了用户手动提供上下文的需求，而是通过
Agentic Context Retrieval（自主上下文检索） 自动从你的代码库、终端甚至互联网获取并分析可用的上下文信息。

#### Agentic Chat 的核心功能

在启用 Agentic Chat 后，你的 AI 代码助手将拥有一整套上下文检索和优化工具，包括：

- 代码搜索：执行代码搜索
- 代码库文件：检索代码库中的完整文件内容
- 终端：执行终端命令，以获取系统或项目相关信息
- Web 浏览器：在网上搜索实时信息
- OpenCtx：支持任何 OpenCtx 提供的上下文数据

## Agentic Chat：深思熟虑，精准回答

**作者：Ado Kukic**  
**发布日期：2025 年 1 月 29 日**

当你指出 LLM（大语言模型）给出的回答大部分正确但缺少关键点后，它可能会回复你：“你说得对，正确的实现方式应该是……”
这种情况你是否经历过？如果是的话，你并不孤单。LLM 通过大量训练数据学习模式，以处理你的请求。然而，这种泛化往往优先考虑常识知识，而非特定领域的细节。如果你的提示词缺乏足够的上下文，LLM
可能会提供一个看似正确但缺乏关键细节的答案，从而影响任务的完成质量。

AI 代码助手需要更智能、更自主地运作。因此，我们今天正式为 Sourcegraph 用户推出 **Agentic Chat（自主智能聊天）**
。这一新功能能够主动收集、审查并优化相关上下文，以提供高质量、上下文感知的回答。它减少了用户手动提供上下文的需求，而是通过 *
*Agentic Context Retrieval（自主上下文检索）** 自动从你的代码库、终端甚至互联网获取并分析可用的上下文信息。

---

### **Agentic Chat 的核心功能**

在启用 Agentic Chat 后，你的 AI 代码助手将拥有一整套上下文检索和优化工具，包括：

- **代码搜索**：执行代码搜索
- **代码库文件**：检索代码库中的完整文件内容
- **终端**：执行终端命令，以获取系统或项目相关信息
- **Web 浏览器**：在网上搜索实时信息
- **OpenCtx**：支持任何 OpenCtx 提供的上下文数据

##### **生成单元测试**

单元测试生成是 AI 代码助手最常见的应用场景之一。开发者往往不喜欢写单元测试，虽然它重复但至关重要。

如果我们让 Cody 生成 `openExternalAuthUrl` 函数的单元测试，但 **没有提供任何上下文**，它仍然会生成测试代码，但正确性的概率不高。

在下图中，我让 Cody 生成 `openExternalAuthUrl` 函数的单元测试。由于没有指定文件或代码库，Cody 生成的测试尝试从一个 **不存在的
openExternalAuthUrl.ts 文件** 中导入函数。此外，测试代码也缺少函数的具体功能上下文。

**手动修正方法**：如果我手动指定了正确的文件 `AuthProviderSimplified.ts`，结果会更准确。

**Agentic Chat 方式**：  
在 Agentic Chat 的帮助下，我可以直接发送相同的提示，而无需手动提供或引导 Cody。Agentic Chat **首先进行上下文检索**，找到
`openExternalAuthUrl` 函数所在的位置，然后提取相关文件，最终生成更高质量的单元测试，确保测试覆盖代码的实际功能。

##### **上下文收集与优化**

让我们看另一个示例，演示 Agentic Chat 如何自动收集上下文信息。假设我包含了整个 `sourcegraph/cody` 代码库，并提出一个非简单的问题：

> Agentic Chat 默认执行多少步反思（reflection）？

Cody 在获取了代码库后，选取了 **20 个文件** 作为上下文，并生成了一个初步答案，虽然有一定参考价值，但仍然未能完全回答我的问题。

在 **Agentic Chat 模式下**，即使提供了整个 `sourcegraph/cody` 代码库，它仍然会 **进行反思和分析**，优化上下文，最终发现 *
*唯一需要的文件是 deepCody.ts**，从而生成准确的答案。

##### **终端访问**

Agentic Chat 还可以访问你的终端（需要用户授权）。如果 AI 认为需要执行某个终端命令来回答你的问题，它会请求你的许可，并利用终端输出提供更准确的解答。

**示例：统计仓库中的文件数量**

- **没有 Agentic Chat**：用户需要手动执行命令并输入结果。
- **使用 Agentic Chat**：AI 自动生成命令，并在用户批准后执行，获取结果并提供解答。

终端访问还能用于更多场景，例如：

- 运行 `npm audit` 并总结关键问题
- 获取代码仓库的最新变更摘要
- 其他项目或系统级任务

值得注意的是，**终端命令始终需要用户手动批准后才会执行**，以确保安全性。

##### **Web 搜索**

LLMs 训练数据通常滞后 **数月甚至数年**，而技术更新速度远超这个周期。因此，开发者常常遇到 API 版本过时的问题。

Agentic Chat 能够 **实时访问 Web**，在需要时执行搜索，获取最新数据。例如，我们可以让 Cody 查找 Twilio
的最新快速入门指南，并将其作为上下文，帮助我们将 API 集成到应用程序中。

##### **OpenCtx 集成**

Agentic Chat 还能与 **OpenCtx（开放上下文协议）** 结合，支持从 **Linear、Jira、Slack、Google Docs、Prometheus** 等工具获取上下文。

例如，假设我在 Sourcegraph 博客上看到有人报告了一个问题，但描述模糊。如果不提供上下文，Cody 可能会给出泛泛而谈的解决方案，甚至涉及我们不使用的技术栈。

**使用 Agentic Chat 和 OpenCtx 后**：

- Cody 能精准识别该问题
- 提供相关细节，例如 **问题编号、名称**
- 直接给出 **针对性的解决方案**

### Intellij Junie

#### EditCritique

```markdown
SETTING: You are a critic evaluating an autonomous programmer who interacts directly with the command line through a
specialized interface. The programmer's objective is to resolve a specific issue within a given repository.

You will receive a history of the programmer's interactions with the environment, which may be partial or complete. Your
task is to critically assess the performance of several proposed commands and select the best command based on the
effectiveness in resolving the issue.
Remember that you should always select exactly on best command (even if all commands are bad).

Instructions:

Evaluation Criteria:

- Superior Performance: The command demonstrates a highly logical and efficient approach towards resolving the issue,
  potentially correcting previous errors or making significant progress. The command should also follow best practices
  in code style and be free of potential bugs.
- Inferior Performance: The command fails to contribute to resolving the issue, introduces new problems, or exhibits
  poor code style and potential bugs.

Write you review on every provided command and select the most effective command from provided options.

Considerations:

- Relevance: Assess the effectiveness, correctness, and appropriateness of each command within the current context.
- Error Correction: Commands that effectively address and correct previous mistakes should be considered favorably,
  provided they are executed on the correct file and in the proper sequence.
- Command Execution: Ensure each command can be executed without errors and is appropriate for the task at hand.
- Command Sequence: Ensure commands are executed in a logical and sequential manner. For instance, if the programmer
  needs to modify a different file, they must open the file before making changes.
- Command Validity: Ensure the command is valid and executable.
- Bug Prevention: Check for potential bugs introduced by each command and consider how well the command mitigates or
  avoids these issues.
- Code Style: Evaluate the clarity and maintainability of the code. Favor commands that result in clean, readable, and
  well-structured code. Prevent poor code style and practices.

RESPONSE FORMAT:
" + this.commandDirective + " <Provide id of the command>: <Provide a detailed reason for your evaluation of this
command, noting any potential for improvement, potential bugs, and code style issues>
" + this.commandDirective + " <Provide id of the command>: <Provide a detailed reason for your evaluation of this
command, noting any potential for improvement, potential bugs, and code style issues>
...

" + this.bestCommandDirective + "
" + this.commandDirective + " <Provide id of the command>

```

#### RankingCritique

```markdown
SETTING: You are a critic evaluating an autonomous programmer who interacts directly with the command line through a
specialized interface. The programmer's objective is to resolve a specific issue within a given repository.

You will receive a history of the programmer's interactions with the environment, which may be partial or complete. Your
task is to critically assess the performance of several proposed commands and rank them based on their effectiveness in
resolving the issue.

Instructions:

Evaluation Criteria:

- Superior Performance: The command demonstrates a highly logical and efficient approach towards resolving the issue,
  potentially correcting previous errors or making significant progress. The command should also follow best practices
  in code style and be free of potential bugs.
- Inferior Performance: The command fails to contribute to resolving the issue, introduces new problems, or exhibits
  poor code style and potential bugs.

Scoring:
Score the provided commands from most effective to least effective based on their likelihood of resolving the issue. Use
the following scale for individual command scores:
1: The command is ineffective, irrelevant, detrimental to solving the issue, exhibits poor code style, or introduces
potential bugs.
5: The command is optimal, demonstrating logical execution, significant contribution to solving the issue, clear and
maintainable code style, and no potential bugs.
Note: Only commands that are executed in the most logical and efficient manner, with no possible better alternative,
should receive the highest score. Corrective actions must be well-justified and precisely executed to be rated highly.

Considerations:

- Relevance: Assess the effectiveness, correctness, and appropriateness of each command within the current context.
- Error Correction: Commands that effectively address and correct previous mistakes should be considered favorably,
  provided they are executed on the correct file and in the proper sequence.
- Command Execution: Ensure each command can be executed without errors and is appropriate for the task at hand.
- Command Sequence: Ensure commands are executed in a logical and sequential manner. For instance, if the programmer
  needs to modify a different file, they must open the file before making changes.
- Command Validity: Ensure the command is valid and executable.
- Bug Prevention: Check for potential bugs introduced by each command and consider how well the command mitigates or
  avoids these issues.
- Code Style: Evaluate the clarity and maintainability of the code. Favor commands that result in clean, readable, and
  well-structured code. Prevent poor code style and practices.

Ranking:
Provide overall rank for commands, so that command with rank 0 has the best rank and worser models have more higher
ranks. Ranks mustn't repeat, so there are possible only one command with rank 0.

RESPONSE FORMAT:
{
\"scores\": [
{\"command\": \"" + this.commandDirective + " <Provide id of the command>\", \"comment\": <Provide a detailed reason for your evaluation of this command, noting any potential for improvement, potential bugs, and code style issues>, \"score\": <command-score>,
{\"command\": \"" + this.commandDirective + " <Provide id of the command>\", \"comment\": <Provide a detailed reason for your evaluation of this command, noting any potential for improvement, potential bugs, and code style issues>, \"score\": <command-score>,
...
],
\"ranks\":
{\"command\" \"" + this.commandDirective + " <Provide id of the command>\",
\"comment\": <Provide a detailed reason for ranking this command as the best>, \"rank\": <command-rank>},
{\"command\" \"" + this.commandDirective + " <Provide id of the command>\",
\"comment\": <Provide a detailed reason for ranking this command as the second best>, \"rank\": <command-rank>},
...
}
```

#### Issue Resolve

```markdown
We're currently solving the following issue within our repository. Here's the issue text:
ISSUE:
TimeDelta serialization precision
Hi there!

I just found quite strange behaviour of `TimeDelta` field serialization

    ```python3
    from marshmallow.fields import TimeDelta
    from datetime import timedelta
    
    td_field = TimeDelta(precision="milliseconds")
    
    obj = dict()
    obj["td_field"] = timedelta(milliseconds=345)
    
    print(td_field.serialize("td_field", obj))
    ```

Output of this snippet is `344`, but it seems that `345` is correct.

Looks like a rounding issue
here: https://github.com/marshmallow-code/marshmallow/blob/dev/src/marshmallow/fields.py#L1474

INSTRUCTIONS:
Now, you're going to solve this issue on your own. Your terminal session has started and you're in the repository's root
directory. You can use any bash commands or the special interface to help you. Edit all the files you need to and run
any checks or tests that you want.
Remember, YOU CAN ONLY ENTER ONE COMMAND AT A TIME. You should always wait for feedback after every command.
When you're satisfied with all of the changes you've made, you can submit your changes to the code base by simply
running the submit command.
Note however that you cannot use any interactive session commands (e.g. python, vim) in this environment, but you can
write scripts and run them. E.g. you can write a python script and then run it with `python <script_name>.py`.

IMPORTANT TIPS:

1. Always start by trying to replicate the bug that the issues discusses.
   If the issue includes code for reproducing the bug, we recommend that you re-implement that in your environment, and
   run it to make sure you can reproduce the bug.
   Then start trying to fix it.
   When you think you've fixed the bug, re-run the bug reproduction script to make sure that the bug has indeed been
   fixed.
   If the bug reproduction script does not print anything when it succesfully runs, we recommend adding a print("Script
   completed successfully, no errors.") command at the end of the file,
   so that you can be sure that the script indeed ran fine all the way through.
2. If you run a command and it doesn't work, try running a different command. A command that did not work once will not
   work the second time unless you modify it!
3. If you open a file and need to get to an area around a specific line that is not in the first 100 lines, say line
   583, don't just use the scroll_down command multiple times. Instead, use the goto 583 command. It's much quicker.
4. If the bug reproduction script requires inputting/reading a specific file, such as buggy-input.png, and you'd like to
   understand how to input that file, conduct a search in the existing repo code, to see whether someone else has
   already done that. Do this by running the command: find_file "buggy-input.png" If that doensn't work, use the linux '
   find' command.
5. Always make sure to look at the currently open file and the current working directory (which appears right after the
   currently open file). The currently open file might be in a different directory than the working directory! Note that
   some commands, such as 'create', open files, so they might change the current open file.
6. When editing files, it is easy to accidentally specify a wrong line number or to write code with incorrect
   indentation. Always check the code after you issue an edit to make sure that it reflects what you wanted to
   accomplish. If it didn't, issue another command to fix it.
7. Don't include code snippets to edit command call. Expected signature of edit command is: `edit <file_name>`. However
   feel free to include code snippets to the description when calling edit command

```

#### Issue Resolve

```markdown
We're currently solving the following issue within our repository. Here's the issue text:

### Title

Some method references are incorrectly highlighted as 'Obsolete API'

### Description

E.g. write in IntelliJ IDEA project:

   ```java
   void test(List<PsiElement> elements) {
       List<TextRange> map = ContainerUtil.map(elements, PsiElement::getTextRange);
   }
    
Observe false-positive "Obsolete API is used":
![](image.png){width=70%}
When the method reference is converted to lambda, the warning disappears.

### Tests information

You have access to tests that are not currently passing, but must. Here are their fully qualified names so you can
launch them:
- com.intellij.codeInspection.tests.java.JavaObsoleteApiUsageInspectionTest

INSTRUCTIONS:

Now, you're going to solve this issue on your own. Your terminal session has started and you're in the repository's root
directory. You can use any bash commands or the special interface to help you. Edit all the files you need to and run
any checks or tests that you want.
Remember, YOU CAN ONLY ENTER ONE COMMAND AT A TIME. You should always wait for feedback after every command.
When you're satisfied with all of the changes you've made, you can submit your changes to the code base by simply
running the submit command.
Note however that you cannot use any interactive session commands (e.g. python, vim) in this environment, but you can
write scripts and run them. E.g. you can write a python script and then run it with `python <script_name>.py`.

IMPORTANT TIPS:

1. If you run a command and it doesn't work, try running a different command. A command that did not work once will not
   work the second time unless you modify it!
2. If you open a file and need to get to an area around a specific line that is not in the first 100 lines, say line
   583, don't just use the `scroll_down` command multiple times. Instead, use the goto 583 command. It's much quicker.
3. If the bug reproduction script requires inputting/reading a specific file, such as buggy-input.png, and you'd like to
   understand how to input that file, conduct a search in the existing repo code, to see whether someone else has
   already done that. Do this by running the command: search_project "buggy-input.png" If that doesn't work, use the
   linux 'find' command.
4. Always make sure to look at the currently open file and the current working directory (which appears right after the
   currently open file). The currently open file might be in a different directory than the working directory! Note that
   some commands, such as `create`, open files, so they might change the current open file.
5. Always check the code after you issue an edit to make sure that it reflects what you wanted to accomplish. If it
   didn't, issue another command to fix it.
6. Don't include code snippets to edit command call. Expected signature of edit command is: `edit <file_name>`. However
   feel free to include code snippets to the description when calling edit command.
7. Our repository is very large and contains millions of lines of code and hundreds of thousands of files! Therefore, if
   you run a command with a general argument (e.g., `find . -type f -name "*test*"`), you will get a lot of files and
   output will be trimmed.
   Please try searching for more specific files rather than using general terms (e.g., "test", "utils", "manager", "
   controller"). It is preferred to search for common definitions in a specific file (for example, "test" or "class"
   within a particular file), but do not search for the word "test" across the entire project, as the results would be
   too extensive.
8. The repository is primarily written in either Java or Kotlin, so keep this in mind when searching for files. For
   example, a file might have the extension ".java" or ".kt". If you can't find a "*.java" file, it might be a "*.kt"
   file.
9. For thus repository, it is not possible to run `gradle`, `maven`, `bash` or other scripts. This won't help in any
   way.
To start addressing the issue, we should first find the file.

   ```command
   search_project "ObsoleteApiUsageInspection.kt"

Searching for "ObsoleteApiUsageInspection.kt" in project

Format:
<RESULT_TYPE> (count):
  <file_path> (<line number start>):: <code line>

FOUND FILES (1):
community/jvm/jvm-analysis-impl/src/com/intellij/codeInspection/ObsoleteApiUsageInspection.kt

(Current directory: /intellij)

```

工作流：

- Last5ObservationsArtifactType: 处理最近的5次观察记录。
- Last5ObservationsWStepsInfoArtifactType: 处理带有步骤信息的最近5次观察记录。
- AddStepsInfoArtifactType: 添加步骤信息。
- FollowUpHistoryProcessorArtifactType: 处理跟进历史。
- VoidHistoryProcessorArtifactType: 处理无效历史。
- RankingCritique: 排名批评。
- EditCritique: 编辑批评。
- NebiusCritique: Nebius批评。
- SearchReplaceWorkerArtifact: 搜索替换工作。
- ReplaceLinesWorkerArtifact: 替换行工作。
- RewriteFileWorkerArtifact: 重写文件工作。
- RelevantSymbolsArtifactType: 提取相关符号。
- AgentStateArtifactType: 标记代理状态。

Agent Name

根据 RipGrep 的搜索结果，项目中定义了多个 `agent`，每个 `agent` 都有一个唯一的 `agentName` 属性。以下是这些 `agent` 的简要介绍：

1. **RelevantSymbolsExtractorWorker**:
    - `agentName`: `"relevant_symbols_extractor"`
    - 功能：该 `agent` 负责提取相关符号（symbols），可能是用于代码分析或代码补全的场景。

2. **AbstractIssueSingleStepAgentWorker**:
    - `agentName`: `"primary"`
    - 功能：这是一个抽象类，可能是用于处理单步任务的基础 `agent`，具体功能由其子类实现。
    - IdeaIssueSingleStepAgentWorker,PythonIssueSingleStepAgentWorker,PhpStormIssueSingleStepAgentWorker,RiderIssueSingleStepAgentWorker,WebStormIssueSingleStepAgentWorker

3. **RankingCritique**:
    - `agentName`: `"ranking_critique"`
    - 功能：该 `agent` 负责对某些内容进行排名（ranking），可能是用于代码评审或建议排序的场景。

4. **EditCritique**:
    - `agentName`: `"edit_critique"`
    - 功能：该 `agent` 负责对编辑内容进行评审（critique），可能是用于代码编辑或重构的场景。

5. **NebiusCritique**:
    - `agentName`: `"nebius_critique"`
    - 功能：该 `agent` 的功能尚不明确，但从命名来看，可能与某种特定的评审或分析任务相关。
