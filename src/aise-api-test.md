# AI 辅助软件工程：AI  生成 API 测试

## 示例

### Checksum

[ Why We Built A System of AI Agents to Automate E2E Testing ](https://checksum.ai/blog/the-engineering-of-an-llm-agent-system)

客户将一个 JavaScript SDK 集成到他们的 HTM 中，Checksum 收集匿名的使用模式数据。然后我们用这些数据训练一个模型，它可以很好地完成三件事：

- 根据真实使用模式检测测试流程，包括理想路径和边缘情况。
- 在实时环境中执行测试流程并生成 Playwright/Cypress 代码。
- 在运行测试时维护这些测试，因此随着软件的变化，测试套件不断更新。

LLM 智能体理是连接到不同功能并可以执行代码的 LLM，它们相对成熟。但我们的洞察力更深一步。

在 Checksum，我们并不训练一个生成完整测试的单一 LLM 模型。我们的解决方案是将多个模型组成一个系统，目标是在线上执行流程并将其转换为端到端测试代码。
整个系统由我们的主 Checksum LLM 协调，这个模型是系统中最重要的一个。

相关文章：

* [Pix2Struct](https://arxiv.org/abs/2210.03347)
* [OS-Copilot: Towards Generalist Computer Agents with Self-Improvement](https://arxiv.org/abs/2402.07456)
* [CoVA: Context-aware Visual Attention for Webpage Information Extraction](https://arxiv.org/abs/2110.12320)

