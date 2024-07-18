# DevOps 驱动的 AI4SE

工具示例：

| 环节        | 头部                  | 工具                                           | 特点                                                                                | 典型工具                                                          |
|-----------|---------------------|----------------------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------|
| 需求/项目管理   | Atlassian           | Jira AI Assistant, Atlassian Intelligence    | 构建交互式 AI 需求编辑器，提升需求编写效率。扩大生成式 AI 使用触点，提供 AI 跨工具链能力。                               | Jira AI Assistant, Atlassian Intelligence                     |
| 代码与 CI/CD | GitHub              | GitHub Copilot, Copilot X, Copilot Workspace | 围绕代码开发、协作、构建为核心，以开发者体验作为度量体系；                                                     | GitHub Copilot, Copilot X, Copilot Workspace, Dynatrace Davis |
| 测试        |                     | Testim Copilot                               | 生成式 AI 测试工具，提供测试用例生成、自动化测试、测试报告等功能。                                               | Testim                                                        |
| 文档与协作     | Atlassian           | Atlassian Rovo                               | 通过生成式 AI 解锁企业知识的工具，内建和自定义知识管理智能体。                                                 | Atlassian Rovo                                                |
| 基础设施      | AWS/Sysdig          | Amazon Q, Sysdig Sag                         | 在云平台上，关注在 AI 重新定义"安全左迁"。结合生成式 AI 与传统 AI 工具，进行云基础设施排错、问答、网络诊断等。结合云平台，提供对应 AI 辅助能力。 | Amazon Q, Sysdig Sag                                          |
| 可观测性      | New Relic/Dynatrace | NewRelic Grok, Dynatrace Davis               | 结合传统判别式 AI 工具，无缝辅助问题定位和修复，与问题回顾。围绕新兴 AI 技术栈构建 AI 应用可观测性。                          | NewRelic Grok                                                 |
| 开发者工具     | JetBrains           | AI Assistant, Grazie                         | 围绕开发人员日常活动，构建全面的 AI 辅助；在 IDE 构建精确的上下文，以获得高质量生成内容。                                 | AI Assistant, Grazie                                          |

## 示例

### AI 助手 + 源码管理

[Tabnine + Atlassian](https://www.tabnine.com/blog/tabnine-atlassian-ai-enabled-software-development-built-around-you/)

从 DevOps 和 AI 的角度来看， Tabnine 与 Atlassian 产品的集成展示了如何利用人工智能增强开发运维（DevOps）流程的效率和质量。以下是一些关键点的总结：

1. **全面的代码感知和个性化建议**：通过与 Bitbucket 和其他 Git 仓库的集成，能够在开发者 IDE
   中提供高度个性化的代码完成建议。这不仅仅是静态的代码补全，还包括变量类型、注释、已打开文件和项目的上下文信息，从而显著提升了开发者的工作效率和代码质量。
2. **全局代码感知和团队协作**：通过与 Bitbucket 的全局连接， Tabnine
   扩展了其能力，使得整个工程团队能够共享和利用更丰富的代码上下文。这对于大型企业和跨部门协作的团队尤为重要，可以加强对代码库的理解和重用，从而提升整体的开发效率和协作水平。
3. **AI 模型定制和性能优化**： Tabnine 通过定制 AI 模型，利用 Bitbucket 中存储的代码库进行优化，特别是针对不常见的编程语言或框架。这种个性化和优化能力提高了
   AI 在软件开发过程中的表现，为开发团队提供更精准和高质量的代码生成和支持。
4. **提升团队生产力的工具和平台支持**： Atlassian 和 Tabnine 的集成不仅仅是工具级别的整合，更是为工程团队提供了全方位的工具和平台支持，帮助团队在
   DevOps 实践中更有效地运用人工智能技术，从而加速交付周期、提高软件质量和团队的整体生产力。

综上所述， Tabnine 与 Atlassian 产品的结合展示了如何从 DevOps
和人工智能的融合中获得多方面的利益，为软件开发团队提供了强大的工具和平台支持，推动团队在敏捷开发和持续交付中取得更大的成功。
