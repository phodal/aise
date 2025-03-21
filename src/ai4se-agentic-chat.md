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
