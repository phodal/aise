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

## 工具列表


* **Functionize**:  
  * **核心AI功能**: Functionize的核心是其ML引擎和testGPT。testGPT利用生成式AI，允许用户通过自然语言提示创建测试 10。其ML引擎通过学习实际用户在应用中的操作流程来理解应用行为，并在此基础上自主生成和维护测试 14。该引擎据称已在过去十年间积累了大量全球部署应用的测试数据进行训练 14。其他关键AI特性包括视觉AI（用于验证页面元素的视觉正确性）、异常检测（减少误报）、强大的自我修复能力和智能截屏（可分层查看元素）2。Functionize采用基于代理（agent-based）的测试方法，旨在实现更高级别的自主性 10。  
  * **技术原理**: Functionize将待测应用视为一个庞大的状态机图（state machine graph）或马尔可夫决策过程 14。它为页面上的每个元素（而非仅仅是测试步骤中的目标元素）收集数百个属性，包括位置、结构、滚动数据、时序、代码关系、CSS属性、视觉样式、网络指标和截图等 14。一个普通的Web应用每页约有3500个元素，Functionize为每个元素收集约200个属性，这意味着每个测试步骤可能产生约70万个数据点 14。这些海量数据被用于训练其深度学习模型，使其能够理解应用的交互性、页面元素及其属性（DOM），并进行类似人类的逻辑判断（如是否需要滚动到某个元素）14。其自我修复机制基于对整个页面多维状态的捕捉，而非依赖脆弱的选择器（如ID或XPath），从而实现了亚秒级的自我修复决策和高达99.95%的元素追踪准确率 14。  
* **TestRigor**:  
  * **核心AI功能**: TestRigor以其“用平白英语编写测试”的核心理念著称 11。它利用生成式AI，允许用户通过自然语言提示或用户故事来创建测试用例 11。其“AI视觉”（AI Vision）功能使其能够测试图像、图表等视觉元素，而不仅仅是检查元素是否存在 27。TestRigor还具备自我修复能力，并能通过“using ai”命令实现上下文感知测试 11。一个独特的特性是它能够根据应用在生产环境中的实际用户行为来生成测试 11。  
  * **技术原理**: TestRigor的核心是将高级的、人类可读的英语指令（如“购买一个Kindle”）翻译成一系列具体的、可执行的测试步骤 11。它整合了NLP、生成式AI和机器学习技术，其测试方法侧重于从最终用户的视角进行，而非依赖于底层的元素定位器（如XPath或CSS选择器）11。这种方法旨在创建“超稳定”的测试，减少因UI细微变化导致的脚本维护工作 11。  
* **Mabl**:  
  * **核心AI功能**: Mabl在其整个平台中深度集成了AI能力。其GenAI功能包括：GenAI测试创建（根据意图或需求自动生成结构化测试）、GenAI断言（使用自然语言验证复杂的应用行为，如视觉、AI特性、聊天机器人等）、GenAI数据库与脚本生成（从自然语言生成数据库查询和JavaScript代码片段）13。在测试执行方面，Mabl提供GenAI测试失败摘要（快速定位根本原因）、视觉变化检测（利用计算机视觉）和性能异常检测（利用聚类算法）13。其维护能力核心是GenAI自动修复（通过理解页面含义来适应复杂更新，如“添加到购物车”与“添加到购物篮”之间的文本变化）和智能等待（通过监督式机器学习模型学习应用时序，动态调整测试执行速度）13。  
  * **技术原理**: Mabl的自动修复机制结合了生成式AI对页面语义的理解、专家系统、概率模型以及监督式机器学习 13。例如，其智能等待功能通过学习应用的响应时间来动态调整等待，以提高测试的稳定性和执行效率。GenAI断言则允许用户用自然语言描述期望的验证行为，AI将其转化为具体的检查点。Mabl还致力于综合各种数据源，为用户提供关于应用质量的整体洞察 31。  
* **AccelQ Autopilot**:  
  * **核心AI功能**: AccelQ Autopilot提供所谓的“代理式自动化”（Agentic Automation），旨在超越基本的脚本生成，提供跨越整个自动化生命周期的GenAI能力 18。其关键特性包括：场景发现与测试步骤生成器（根据业务输入自动创建API和UI测试）、AI设计器（将测试逻辑转化为可复用的模块化组件）、测试用例生成器（创建多样化的测试组合以保护业务逻辑）、逻辑洞察（提供智能优化建议）以及自主修复（自动适应应用更新并提供AI辅助故障排除）18。  
  * **技术原理**: AccelQ Autopilot基于一个AI代理架构，该代理能够学习待测应用，并从一开始就生成完全可执行的测试用例 18。它旨在覆盖从智能测试用例生成到验证、变更管理、维护和结果分析的整个测试生命周期 32。其AI驱动的方法确保了跨平台和技术的端到端覆盖，减少了人工干预的需求 18。  
* **LambdaTest KaneAI**:  
  * **核心AI功能**: KaneAI被定位为“GenAI原生测试代理”，是一个基于现代大型语言模型（LLM）的AI原生QA代理即服务平台 36。它允许用户通过自然语言输入来规划、编写和演进端到端测试 1。主要功能包括：从自然语言生成测试、多语言代码导出（支持Selenium、Playwright、Cypress、Appium等主流框架）、智能测试规划器（根据高级目标自动生成测试步骤）、API测试集成、双向测试编辑（自然语言与代码同步）、智能版本控制、GenAI原生调试与根本原因分析（RCA），以及与HyperExecute平台的集成以实现大规模并行测试 33。  
  * **技术原理**: KaneAI的核心是利用LLM来理解高级别的测试目标和自然语言指令，并将其转化为可执行的测试工件 36。它强调通过高级目标而非详细步骤来驱动测试生成。其GenAI原生调试功能利用AI对错误进行分类并推荐修复方案 36。  
* **Katalon Studio**:  
  * **核心AI功能**: Katalon Studio集成了一系列AI功能以提升测试效率。其StudioAssist是基于OpenAI GPT API构建的AI助手，能够根据用户的代码注释或提示生成测试脚本和解释现有代码 40。平台还提供AI驱动的测试用例创建建议（基于应用的UI和用户行为）、AI视觉测试（比较不同构建版本的截图以检测视觉差异）以及智能测试维护（当应用发生变化时，AI引擎能检测到这些变化并自动建议对测试用例进行修改）30。  
  * **技术原理**: StudioAssist直接利用OpenAI GPT API的能力进行代码生成和解释 42。其AI引擎通过分析应用的UI结构和用户交互模式来提供测试用例建议和维护支持 40。视觉测试功能则依赖AI算法比较截图，自动标记视觉差异 40。  
* **Tricentis Testim (包括 Testim Copilot)**:  
  * **核心AI功能**: Testim的核心AI能力在于其智能定位器（Smart Locators），这些定位器通过AI/ML技术来稳定地识别Web元素，并能在元素属性变化时自动更新，从而提高测试的稳定性并减少维护 6。Testim Copilot是其GenAI能力的体现，它能够根据文本描述自动生成JavaScript测试步骤、解释现有代码的意图以方便复用，以及识别和修复测试代码中的问题 44。  
  * **技术原理**: Testim的智能定位器利用多种算法来识别元素，并在应用变化时通过AI进行评估和自我改进，以防止测试中断 44。Testim Copilot利用生成式AI，通过交互式提示帮助用户创建、理解和修复定制化的JavaScript测试代码 46。  
* **Applitools**:  
  * **核心AI功能**: Applitools以其强大的视觉AI（Visual AI）技术闻名，专注于UI层面的视觉验证和回归测试 30。它能够检测出人眼可感知的所有视觉差异，而不仅仅是像素级别的比较，有效处理动态内容并减少误报 48。Applitools还提供NLP Builder，允许用户通过纯英文描述来创建无代码的端到端测试 49。其平台还支持AI增强的录制功能，并能与Selenium、Cypress、Playwright等主流测试框架集成 50。  
  * **技术原理**: Applitools的视觉AI引擎由包含数百种算法的网络构成，从基于规则的算法到深度学习模型不等 48。该引擎据称已分析超过10亿张图像，并利用这些海量数据进行训练，从而能够智能地识别有意义的视觉变化，区分真实缺陷和预期的动态内容更新 48。其NLP Builder则利用自然语言处理技术将用户的英文测试描述转化为可执行的测试步骤 50。  
* **Parasoft (Jtest, SOAtest, Selenic)**:  
  * **核心AI功能**: Parasoft将其AI和ML技术应用于多个测试领域。对于Java单元测试（Jtest），AI能够辅助生成包含mock对象和断言的JUnit测试用例，以提高代码覆盖率并减少手动创建工作 52。在静态分析方面，AI能够辅助分类分析结果，并通过LLM生成代码修复建议 52。对于API测试（SOAtest），AI可以根据记录到的UI或API流量自动生成API测试场景 53。对于UI测试（Selenic），AI提供测试脚本的自我修复能力和优化建议 52。  
  * **技术原理**: Parasoft的AI/ML技术通过分析现有Java代码的结构和行为来生成单元测试 52。它利用机器学习对静态分析发现的违规进行分类和优先级排序，并集成OpenAI等LLM来提供代码修复建议 52。API测试生成则基于对应用交互流量的监控和分析。UI测试的自我修复依赖于AI对元素变化的适应能力 53。  
* 其他提及工具:  
  市场上还有其他一些值得关注的GenAI测试工具，包括Testsigma（提供自动修复和AI建议引擎）30、Eggplant（AI测试建模）30、TestCraft（基于ML的算法去除误报）30、UiPath（AI自动生成测试用例）30、OpenText（AI辅助测试创建和维护）22、Harness（AI测试创建和自我修复）22、Autify（AI辅助测试创建和维护）22、Reflect（AI辅助测试创建，维护能力相对有限）22、Meticulous（监控应用使用情况以自主创建测试）22、ProdPerfect（分析用户行为以自动创建E2E测试）22、TestGrid CoTester（理解用户意图生成测试）33、TestCollab – QA Copilot 33、Test.ai（基于用户交互自动生成测试）33以及GitHub Copilot在测试脚本生成方面的应用 33。

当前GenAI测试工具市场呈现出多样化的特点。不同的工具在AI应用的侧重点上有所不同，例如一些工具专注于视觉测试（如Applitools），一些强调基于自然语言的测试创建（如TestRigor），还有一些则提供全面的自我修复和广泛的AI集成（如Functionize、Mabl）。此外，这些工具也面向不同技术水平的用户，提供了从无代码、低代码到专业代码的多种选择。这意味着不存在一个普适性的“最佳”GenAI测试工具；企业在选择时，需要根据自身的具体痛点（例如UI稳定性、测试创建速度、视觉正确性等）以及团队的技术能力进行综合评估。

* **表格：领先的生成式AI测试工具对比概览**  
  为了更清晰地展示主要工具的GenAI特性，下表提供了一个对比概览：

| 工具名称                  | 关键GenAI特性                                                             | 主要AI技术                      | 支持的测试类型               | 目标用户         |
|:----------------------|:----------------------------------------------------------------------|:----------------------------|:----------------------|:-------------|
| **Functionize**       | testGPT（自然语言测试生成）、ML引擎（用户行为学习）、视觉AI、异常检测、自我修复、智能截屏                    | LLM、ML、深度学习、计算机视觉           | UI、API、移动、端到端         | 低代码/专业代码     |
| **TestRigor**         | 自然语言测试创建、GenAI测试用例生成（来自提示/用户故事）、AI视觉（图像/图表测试）、自我修复、上下文理解、基于用户行为生成测试   | NLP、GenAI、ML                | Web、移动、API、桌面、视觉、端到端  | 无代码/低代码      |
| **Mabl**              | GenAI测试创建（来自意图/需求）、GenAI断言、GenAI数据库/脚本生成、GenAI自动修复、视觉变化检测、性能异常检测、智能等待 | GenAI、ML（监督式）、概率模型、计算机视觉    | Web UI、API、移动（通过集成）   | 低代码          |
| **AccelQ Autopilot**  | 代理式自动化、AI测试管理、场景发现与步骤生成、AI设计器（模块化）、测试用例生成、逻辑洞察、自主修复                   | AI代理架构、GenAI、ML             | Web、API、移动、桌面、ERP、大型机 | 无代码/低代码      |
| **LambdaTest KaneAI** | GenAI原生测试代理、自然语言测试生成、多语言代码导出、智能测试规划、API集成、双向编辑、GenAI原生调试与RCA          | LLM、NLP                     | Web、移动、API            | 自然语言/代码      |
| **Katalon Studio**    | StudioAssist（代码生成/解释）、AI测试用例建议、AI视觉测试、智能测试维护、NLP测试脚本生成                | OpenAI GPT API、ML、NLP、计算机视觉 | Web、API、移动、桌面         | 无代码/低代码/专业代码 |
| **Tricentis Testim**  | Testim Copilot（GenAI测试步骤生成/代码解释/修复）、AI/ML智能定位器、视觉编辑器、失败诊断             | GenAI、ML                    | Web、移动（Salesforce重点）  | 低代码/专业代码     |
| **Applitools**        | 视觉AI（UI验证）、NLP Builder（自然语言测试创建）、AI增强录制、处理动态内容                        | 深度学习、ML、NLP、计算机视觉           | 视觉、功能（UI）、API（通过集成）   | 无代码/专业代码     |
| **Parasoft**          | AI单元测试生成（Jtest）、AI静态分析辅助与修复建议（LLM）、API测试生成（来自流量）、UI测试自我修复（Selenic）    | AI/ML、LLM                   | 单元、API、UI、静态分析、安全、合规  | 专业代码         |
