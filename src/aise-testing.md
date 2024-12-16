# AI 辅助软件工程：AI 辅助测试

### 自动化测试趋势
1. **人工智能和机器学习的兴起**
    - 自愈测试：机器学习算法能自动调整自动化测试以适应代码或UI元素的变化。
    - 智能测试用例生成：AI分析用户行为和应用程序使用数据，生成更全面和相关的测试用例。
    - 增强缺陷检测：ML算法能识别视觉异常和潜在的UI不一致性。

2. **左移测试方法**
    - 提早集成自动化测试，接近代码创建阶段，有助于及早发现和解决错误。
    - 降低开发成本：早期修复错误比后期修正成本低。
    - 提高软件质量：早期和持续的测试有助于确保更高的软件整体质量。
    - 增强协作：促进开发人员和测试人员之间的沟通和协作。

3. **API测试自动化的持续增长**
    - 执行全面的API测试：验证API在各种场景下的功能性、性能和安全性。
    - 提高开发速度：加快API测试周期，加速整个开发过程。
    - 减少手动工作：简化API测试，将资源用于其他任务。

4. **与CI/CD工具的集成：无缝工作流程**
    - 提早发现缺陷：在CI/CD管道中集成自动化测试，以便在整个开发周期中及早发现和解决问题。
    - 加快发布速度：在CI/CD管道中高效的测试促进了更快和更频繁的软件发布。
    - 提高质量和一致性：在CI/CD管道中自动化测试促进了测试的一致性，确保了软件的整体质量。

5. **基于云的测试：可扩展性和可访问性**
    - 按需扩展：云平台可根据项目和负载波动提供测试资源的扩展或缩减。
    - 可访问性和协作：基于云的测试工具可通过互联网访问，促进地理上分散的测试团队之间的协作。
    - 加快测试周期：云环境提供高性能计算能力，加快测试执行和开发过程中的反馈循环。

6. **低代码/无代码应用的测试**
    - 端到端（E2E）测试：在低代码应用支持的网络、移动等渠道进行自动化测试。
    - 启用非技术用户：允许业务团队在无需深厚技术知识的情况下进行测试，对采用至关重要。
    - 简化CI/CD管道集成：将测试解决方案高效地嵌入低代码平台青睐的持续交付管道。

7. **数据库测试：确保数据完整性**
    - 功能测试：验证数据库操作（如插入、更新和删除）是否按预期工作。
    - 性能测试：在重负载下评估数据库性能，识别潜在瓶颈和可扩展性问题。
    - 数据完整性测试：确保数据库中的数据准确性和一致性，防止数据损坏。

### 自动化测试工具
1. **qodo（原Codium）**
    - 自动生成准确的单元测试。
    - 行为覆盖：识别代码可能遇到的不同场景，自动创建覆盖这些行为的测试用例。
    - 支持多种编程语言和集成开发环境。

2. **Katalon Studio的AI测试工具**
    - TrueTest：AI驱动的回归测试，智能创建和更新测试，关注关键区域，避免手动创建和维护。
    - AI视觉测试：使用先进算法进行智能UI验证，减少误报，关注关键问题。

## 示例来源

[Key Trends in Automation Testing for 2024 and Beyond](https://www.codium.ai/blog/key-trends-in-automation-testing-for-2024-and-beyond/)

### 工具：QA.tech

#### QA.tech：AI驱动的测试创新

QA.tech以其AI驱动的测试工具而闻名，旨在通过智能代理和先进的算法来提高软件测试的效率和准确性。以下是QA.tech在AI辅助测试方面的几个亮点：

1. **多模态大型语言模型（Multimodal LLMs）的应用：**
    - QA.tech利用Multimodal LLMs来理解和解释网站用户界面（UI）元素。
    - 通过结合视觉和文本数据，其模型能够更准确地识别和解释UI元素。

2. **智能测试用例生成与自愈测试：**
    - AI分析用户行为和应用程序使用数据，生成更全面和相关的测试用例。
    - 自愈测试功能使机器学习算法能够自动调整自动化测试，以适应代码或UI元素的变化。

3. **与CI/CD工具的集成：**
    - QA.tech工具可以与持续集成和持续部署（CI/CD）流程无缝集成，提供更快的发布周期和更高的软件质量。

4. **实验性与实践性的结合：**
    - 提供了丰富的实验性功能，如使用DaViT和对比学习来提高模型识别网页动作的准确性。
    - 同时，QA.tech注重实践应用，如通过Live Deploy PR来增强部署管道的可见性和可控性。

> Ship faster with AI agents that create and run your QA tests

- [Using Multimodal LLMs to Understand UI Elements on Websites](https://qa.tech/blog/using-multimodal-llms-to-understand-ui-elements-on-websites/)
- [Building AI-Powered Web Agents: Identifying Actions with Vision and HTML Embeddings](https://qa.tech/blog/building-ai-powered-web-agents-identifying-actions-with-vision-and-html-embeddings/)
- [You Should Use a Live Deploy PR](https://qa.tech/blog/you-should-use-a-live-deploy-pr/)
- [How we’re approaching LLM prompt evaluation at QA.tech](https://qa.tech/blog/how-were-approaching-llm-prompt-evaluation-at-qa-tech/)
- [Building AI-Powered Web Agents: Identifying Actions with Vision and HTML Embeddings](https://qa.tech/blog/building-ai-powered-web-agents-identifying-actions-with-vision-and-html-embeddings/)
- [Understanding UIs Part II: Context and Content Matters](https://qa.tech/blog/understanding-uis-part-ii-why-contextual-content-matters/)
- [Spatial Memory: Why It Matters for UX Design](https://www.nngroup.com/articles/spatial-memory/)

```javascript
describe('@prompteval reasonActEvaluate - updateSteps - prompt evaluation - datapoints', async function () {
 it('evaluates datapoints', async function () {
    // Retrieve data points tagged for testing from the database
   const taggedDatapointsToEval = await getTypedAgentDatapointsByTags(
     toEvalDatapointTag,
     'UPDATE_STEPS',
   )
   // Test all tagged data points
   for (const dp of taggedDatapointsToEval) {
     await testDataPoint(dp, () => {
       return getExpectedOutputAsserts(dp.expectedOutput, 'UPDATE_STEPS')
     })
   }
 })
 ```

## 工具分析：Testim

https://www.testim.io/ai/

- AI 加速测试：使用生成式 AI，可以从文本中创建自定义测试步骤，解释和记录现有的测试代码，并快速识别和修复问题。
- 智能定位器：AI 和 ML 智能定位器可以跨移动和 Web 应用程序识别元素。通过一系列算法，即使应用程序发生变化，测试仍然可以正常运行。
- 更好的用户体验：AI 驱动的助手可以更轻松地定位文档、视频和最佳实践示例，让您更快地找到答案。

Testim平台将AI技术深度整合到测试自动化中，以下是Testim利用AI的一些关键方式：

1. **生成式AI与代码解释：**
    - Testim的AI Copilot可以从文本描述中生成自定义测试步骤，减少编码工作量。
    - 它还能解释现有代码，快速识别问题并提供解决方案。

2. **AI智能定位器：**
    - Testim使用AI和ML技术来智能定位Web和移动应用程序中的元素，即使应用程序发生变化，也能保持测试稳定性。

3. **用户体验优化：**
    - AI驱动的助手能够提供快速访问文档、视频和最佳实践示例，极大地提升了用户体验。

4. **测试稳定性与案例管理：**
    - Testim的AI智能定位器能够自我修复以适应应用程序的变化，同时与Jira等工具集成，自动化管理测试案例。

## 工具：Katalon Studio