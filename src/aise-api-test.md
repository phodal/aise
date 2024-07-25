# AI 辅助软件工程：AI  生成 API 测试

## 示例

### Checksum: 模拟行为生成测试

[Why We Built A System of AI Agents to Automate E2E Testing](https://checksum.ai/blog/the-engineering-of-an-llm-agent-system)

![](images/llm-system-for-autotest-.webp)

客户将一个 JavaScript SDK 集成到他们的 HTML 中，Checksum 会收集匿名的使用模式数据。然后，我们利用这些数据训练一个模型，该模型能够高效完成以下三个任务：

- 检测测试流程，包括标准路径和边缘情况，以匹配真实使用模式。
- 在实时环境中执行测试流程，并生成 Playwright 或 Cypress 代码。
- 在测试运行过程中维护这些测试，确保随着软件的更新，测试套件也能持续更新。

LLM 智能体是连接到不同功能并能够执行代码的 LLM，它们已经相对成熟。然而，我们的洞察力更进一步。在 Checksum，我们并没有训练一个单独的
LLM 模型来生成完整的测试。我们的解决方案是将多个模型集成在一起，构成一个系统，旨在在线上执行流程并将其转换为端到端的测试代码。

整个系统由我们的主 Checksum LLM 进行协调，这个模型在系统中扮演着最为关键的角色。

代码：https://github.com/checksum-ai/checksum-ai-runtime

相关文章：

* [Pix2Struct](https://arxiv.org/abs/2210.03347)
* [OS-Copilot: Towards Generalist Computer Agents with Self-Improvement](https://arxiv.org/abs/2402.07456)
* [CoVA: Context-aware Visual Attention for Webpage Information Extraction](https://arxiv.org/abs/2110.12320)

