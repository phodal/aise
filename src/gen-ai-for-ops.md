# AI 辅助软件工程：AI 运维

## 行业趋势与发展

在当今快速发展的技术环境中，AI 技术正在逐步渗透到各行各业，尤其是在软件工程和运维领域。企业对于系统的可观测性、异常处理和自动化运维的需求不断增加，这为
AI 在 DevOps 领域的应用提供了广阔的空间。多个领先的技术平台已经开始探索并推出 AI 驱动的运维工具，如 New
Relic、PagerDuty、Dynatrace 和 Datadog 等。通过整合生成式 AI、自然语言处理和预测分析技术，这些工具能够有效提升运维效率和系统稳定性。

### New Relic 的生成式 AI 应用

New Relic 通过集成大型语言模型（LLMs）和其统一遥测数据平台，推出了针对可观测性的生成式 AI
助手。这个助手能够帮助用户通过简单的自然语言查询，获得系统状态的深度洞察。例如，开发和运维团队可以迅速定位系统异常并获取修复建议，从而减少停机时间并提升开发效率。此外，New
Relic 的 AI 助手还具备自动化代码级错误识别和修复建议功能，这大大简化了系统运维的复杂性。

### PagerDuty 的 AI 驱动运维

PagerDuty 引入了 PagerDuty Copilot，这是一款专为关键业务运营工作设计的生成式 AI 工具。Copilot
通过实时响应和自动化功能，能够帮助运维团队快速应对系统问题并生成事故回顾报告。它不仅能够自动化生成 Runbook
任务代码，还可以通过自然语言处理技术，辅助用户进行日常运维任务，如问题总结、用户通知等。通过 PagerDuty
Copilot，企业能够在运维过程中显著提升响应速度和决策准确性。

### Dynatrace 的 Davis CoPilot™

Dynatrace 推出了 Davis CoPilot™，这是其 Davis® AI 平台上的一项新功能，标志着业界首个超模态 AI 平台的诞生。Davis CoPilot™
结合了预测 AI、因果 AI 和生成式 AI
技术，能够自动化处理从根因分析到工作流代码生成的各类运维任务。通过自然语言查询，用户可以轻松生成数据仪表板、撰写数据笔记本，并获取代码建议，这些功能极大地简化了系统的管理和配置过程。

### Datadog 的 Bits AI

Datadog 的 Bits AI 是一款基于生成式 AI 的 DevOps 辅助工具，旨在通过一个统一的对话式界面，帮助用户从多个数据源中获取和关联关键信息。Bits
AI 提供了环境监控、自然语言数据查询、事件响应和问题预防等功能。在生产环境中，运维团队可以利用 Bits AI
快速诊断问题，自动化执行响应流程，并生成事件总结和修复指南。此外，Bits AI 还支持与 Datadog 平台的深度集成，进一步增强了用户在问题诊断和解决方面的能力。

## AI 运维 Copilot 的实际应用

AI 运维 Copilot 的核心在于通过智能问答和自动化操作，辅助运维人员高效处理日常任务和突发事件。以下是一些常见的应用场景：

- **告警分析**：AI 能够自动识别告警来源，并提供相关服务的状态信息，帮助运维人员快速定位问题。
- **事件追踪**：在过去的24小时内系统发生的变化可以通过自然语言查询直接呈现，方便问题的溯源和分析。
- **历史事件对比**：AI 可以检查相似事故的历史记录，以确定当前问题是否曾经发生，并提供相应的解决方案。
- **自动化操作**：通过简单的指令，如“将 @用户名 添加为响应者”或“运行工作流 {工作流名称}”，AI 能够自动执行这些任务，减少人为操作失误。
- **实时更新**：运维人员可以随时询问系统的最新状态，确保对问题的处理始终处于最新进展中。

## 运营驱动的 AI 运维落地

在 AI 运维工具的实际应用中，确保其准确性和可用性至关重要。为此，企业需要搭建完善的运营机制，以确保 AI 的输出结果能够满足业务需求。

### 冷启动运营

在系统初期，AI 需要从大量文档中抽取 FAQ，以建立基本的知识库。通过运营团队的审核，这些 FAQ 被不断补充和完善，形成一个可靠的数据库，支持
AI 在早期阶段的应用。

### 日常检视运营

在日常运营过程中，团队需要定期审查 AI 的输出结果，评估是否需要补充更多的材料数据，以及哪些高频问题可以通过 FAQ
通道解决。此外，对于一些复杂的查询或任务，可能需要进一步结构化处理，以确保 AI 的回答能够更加精准。

### 模型持续运营

为了保持 AI 的高效性，企业需要持续对模型进行迭代和优化。这包括对意图识别数据的标注、向量相似召回的数据标注，以及模型的持续更新。通过不断的运营和优化，AI
运维工具能够在实际应用中发挥更大的价值。

## 结论

AI 辅助软件工程和运维的应用正在迅速改变着企业的运营方式。通过生成式 AI、自然语言处理和自动化技术的结合，企业能够显著提升系统的可观测性和稳定性。随着技术的不断发展，这些
AI 工具将在更多场景下得到应用，推动软件工程和运维领域的进一步革新。

## 相关资料

- [Introducing Bits AI, your new DevOps copilot](https://www.datadoghq.com/blog/datadog-bits-generative-ai/)
- [Dynatrace expands Davis AI with Davis CoPilot, pioneering the first hypermodal AI platform for unified observability and security](https://www.dynatrace.com/news/blog/hypermodal-ai-dynatrace-expands-davis-ai-with-davis-copilot/)
- [PagerDuty Announces the Latest Capability from PagerDuty Copilot, a Set of Generative AI-Enabled Use Cases Available Across the PagerDuty Operations Cloud ](https://www.pagerduty.com/newsroom/pagerduty-copilot/)
- [Meet the first GenAI assistant for observability](https://newrelic.com/blog/nerdlog/new-relic-ai-assistant)
