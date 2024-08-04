# 编码智能体分析：Copilot Workspace

## 示例

### 使用Copilot Workspace的实现步骤

[Copilot Workspace: What It Is, How It Works, Why It Matters](https://zilliz.com/blog/what-is-copilot-workspace-and-why-it-matters)

以下是如何利用 Copilot Workspace 来实现该功能的方法：

1. **任务创建**：首先创建一个GitHub issue，任务是将应用程序改为多语言版本。具体任务是将(BGE-M3)多语言模型集成到现有的RAG系统中。
2. **规范**：Copilot Workspace分析任务并生成高级规范，确定需要更新数据处理管道以处理多种语言，并修改RAG系统以利用BGE-M3提供多语言支持。
3. **规划**：Workspace接着生成详细的计划。包括以下步骤：
    - 更新数据摄取过程以包含多语言数据。
    - 修改现有的Milvus设置以支持BGE-M3。
    - 调整RAG系统以利用BGE-M3的多语言功能。
    - 测试系统以确保其能够支持多种语言。
4. **编码**：基于验证后的计划，Copilot Workspace生成必要的代码：
    - 更新数据摄取脚本以预处理和索引多语言数据到Milvus中。
    - 配置Milvus代码以使用BGE-M3嵌入进行多语言的相似性搜索。
    - 修改RAG系统以使用多语言模型查询Milvus并检索相关结果。
5. **审查和测试**：审查生成的代码，进行必要的调整并测试更改。
6. **拉取请求和合并**：满意后，打开一个拉取请求与团队审查更改。最终验证后，合并更改，使应用程序支持多语言功能。
