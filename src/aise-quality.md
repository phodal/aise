# AI 辅助软件工程：AI 辅助软件质量


## 示例

### 案例：TestSpark

[TestSpark](https://github.com/JetBrains-Research/TestSpark) 是一个用于生成单元测试的插件。TestSpark 能够在 IDE 中原生集成多种基于 AI 的测试生成工具和技术。

TestSpark 目前支持两种测试生成策略：

1. 基于大语言模型（LLM）的测试生成（使用 OpenAI 和 JetBrains 内部的 AI Assistant 平台）
2. 基于局部搜索的测试生成（使用 EvoSuite）

### 基于大语言模型的测试生成

对于这种测试生成方式，TestSpark 向不同的大语言模型发送请求。此外，它会在向用户展示测试之前自动检查测试是否有效。

此功能需要从 OpenAI 平台或 AI Assistant 平台获取一个 token。

- 支持任何版本的 Java。
- 生成用于捕获故障的单元测试。
- 为 Java 类、方法和单行代码生成测试。

### 基于局部搜索的测试生成

对于这种测试生成方式，TestSpark 使用 EvoSuite，它是最强大的基于搜索的本地测试生成器。

- 支持 Java 11 及以下版本。
- 根据不同的测试标准生成测试：行覆盖率、分支覆盖率、I/O 多样性、异常覆盖率、变异得分。
- 生成用于捕获故障的单元测试。
- 为 Java 类、方法和单行代码生成测试。

TestSpark 最初由代尔夫特理工大学软件工程研究小组（CISELab at SERG @ TU Delft）实现，目前由 JetBrains 研究院的 ICTL 团队开发和维护。
