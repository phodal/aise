# AI 辅助软件工程：AI 辅助根因分析生成

核心技术：

- 智能调度核心：体系链路完善的调度核心、多模式一键配置
- 代码整库分析：仓库级代码理解、项目文件级代码编写生成
- 文档分析增强：文档知识库结合知识图谱的检索、推理增强
- 垂类专属知识：DevOps 专属知识库、垂类知识库自助一键构建
- 垂类模型兼容：DevOp s领域小模型、DevOps 周边平台兼容

## 示例


### New Relic AI: observability assistant

[Meet New Relic AI, your observability assistant](https://docs.newrelic.com/docs/new-relic-solutions/new-relic-one/core-concepts/new-relic-ai/#synthetic)

New Relic AI 旨在通过将大型语言模型 (LLMs) 与 New Relic 的数据平台相结合，帮助用户理解和管理他们的系统。这个 AI
助手可以用简单的语言回答问题，提供见解，并协助完成诸如故障排除、创建 NRQL 查询、分析错误日志、管理警报和配置合成监控等任务。

**主要功能：**

1. **聊天界面：** 在 New Relic 平台的多数页面中，通过聊天功能与 New Relic AI 进行互动。提出问题，获取关于系统性能和故障排除的见解。
2. **NRQL 查询：** 使用AI助手创建 NRQL（ New Relic Query Language ）查询，以分析系统数据，无需手动编写查询语句。
3. **错误分析：** 从日志和堆栈跟踪中获取错误的摘要和详细信息。
4. **警报管理：** 识别警报覆盖的空白，确保所有实体和服务得到监控。
5. **合成监控：** 设置合成监控，以检查 URL 的可用性和性能。
6. **支持工单：** 汇总并检查支持工单的状态，以便快速解决。
7. **仪表板分析：** 从仪表板中获取摘要和见解，以了解和调查遥测数据。

#### [AI Monitoring](https://newrelic.com/platform/ai-monitoring)



#### NRQL 示例

### 应用数据 NRQL 查询示例

你可以使用 NRQL 查询从应用程序监控、浏览器监控和移动端监控中收集到的数据。通过这些数据，你可以回答各种问题。以下是一些基本的示例。

**唯一用户**。上周你有多少独立用户会话？

```sql
SELECT uniqueCount(session) FROM PageView SINCE 1 week ago
```

**唯一用户趋势**。与前一周相比，上周的独立用户会话数量是增加了还是减少了？

```sql
SELECT uniqueCount(session) FROM PageView SINCE 1 week ago COMPARE WITH 1 week ago
```

**页面浏览趋势**。如何绘制昨天与前天相比的独立用户数量图表？

```sql
SELECT count(*) FROM PageView SINCE 1 day ago COMPARE WITH 1 day ago TIMESERIES AUTO
```

**操作系统版本**。有多少移动端用户使用的是最新的操作系统版本？

```sql
SELECT uniqueCount(uuid) FROM MobileSession FACET osVersion SINCE 7 days ago
```

**关键账户的 Apdex**。某个重要客户的 Apdex 得分是多少？如果你定义了一些自定义属性，你可以查询以监控该客户在应用中体验的性能情况：

```sql
SELECT apdex(duration, t: 0.4) FROM Transaction WHERE customerName='ReallyImportantCustomer' SINCE 1 day ago
```