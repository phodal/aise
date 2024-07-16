# GitHub：AI 平台工程赋能开发者

## 示例：GitHub

> 围绕代码的开发、协作、构建为核心，以开发者体验作为度量体系

[GitHub AI 驱动的开发者平台](https://github.blog/2023-11-08-universe-2023-copilot-transforms-github-into-the-ai-powered-developer-platform/)

### 工具、平台驱动

### [AI 增强的安全左移](https://github.blog/2023-11-08-ai-powered-appsec/)

![Images](images/github-security-shift.png)

- 自动修复（autofix）静态代码问题 (结合 CodeQL 静态代码分析）
- 密码扫描检测泄露的密码
- 生成自定义模式 - 正则表达式

相关文章：

- [CodeQL team uses AI to power vulnerability detection in code](https://github.blog/2023-09-12-codeql-team-uses-ai-to-power-vulnerability-detection-in-code/)
- [Multi-repository variant analysis: a powerful new way to perform security research across GitHub](https://github.blog/2023-03-09-multi-repository-variant-analysis-a-powerful-new-way-to-perform-security-research-across-github/)

### AI 辅助研发决策框架

[A developer’s second brain: Reducing complexity through partnership with AI](https://github.blog/2024-01-17-a-developers-second-brain-reducing-complexity-through-partnership-with-ai/)

- 发现 1：认知负担确实存在，开发人员通过两种方式体验它。（太乏味了和这伤害了我的大脑”）
- 发现 2：开发者渴望 AI 协助完成复杂任务，但我们必须把握好界限
- 发现 3：复杂任务由四个部分组成：理解（建构感知）、决策、行动计划、执行
- 发现 4：开发者对于在理解和制定行动计划方面，接受 AI 的协助。
- 发现 5：开发者对 AI 在决策或执行方面的自主性持谨慎态度。

[Social Integration of Artificial Intelligence: Functions, Automation Allocation Logic and Human-Autonomy Trust](https://link.springer.com/article/10.1007/s12559-018-9619-0)

形态框架：

1. **建构感知**。收集和综合形成任务背景的所有相关信息。
2. **制定行动**。定义执行任务的具体步骤和步骤的顺序。
3. **制定决策**。提出应该针对这个任务采取的措施。
4. **实现任务**。执行按照定义的顺序进行的步骤。

### 度量框架 [Space](https://queue.acm.org/detail.cfm?id=3454124)
|    | 满意度和幸福感                  | 效率             | 活动               | 沟通和协作             | 效率和流程       |
|----|--------------------------|----------------|------------------|-------------------|-------------|
| 个体 | - 开发者满意度                 | - 代码检视速度       | - 检视速度完成数量       | - 代码检视评分（质量或思考深度） | - 代码检视时长    |
|    | - 留存                     |                | - 编码时长           | - PR 合并次数         | - 生产力感知     |
|    | - 分配的代码检视满意度             |                | - # 代码提交次数       | - 会议质量            | - 不受打扰      |
|    | - 代码审查的                  |                | - 代码行数           | - 知识分享，可发现性（文档质量） |             |
| 团队 | - 开发者满意度                 | - 代码检视速度       | - # 完成的用户故事/需求点数 | - PR 合并次数         | - 代码检视时长    |
|    | - 留存                     | - 交付的用户故事/需求点数 |                  | - 会议质量            | - 交接时长      |
| 系统 | - 平台工程的满意度（如 CI、CD 流水线等） | - 代码检视速度       | - 部署频率           | - 知识分享，可发现性（文档质量） | - 代码检视时长    |
|    |                          | - 代码检视接受率      |                  |                   | - 系统中的速度/流动 |
|    |                          | - 平台用户满意度      |                  |                   |             |
|    |                          | - 可靠性（正常运行时间）  |                  |                   |             |

