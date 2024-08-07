# AI 辅助场景：构建团队 AI


> Team AI 是一个加速器，旨在协助团队构建轻量级 AIGC 辅助效能提升机制。它可充当任务助手，以简化和加快日常事务中频繁执行的任务；它也可充当知识增强工具，协助团队进行头脑风暴，并更早地在交付过程中发现问题；此外，它还可以充当团队的"合作伙伴"，将团队的约定规范与生成式AI相融合。
>

在这篇文章里，我将介绍我对于 Team AI 的理解，以及如何构建 Team AI，加速团队的研发效率。

## 为什么我们需要 Team AI?

不同的团队，可能需要根据其特定需求和业务领域，定制自己的 AIGC 助手。作为一个曾经担任过后端、移动端、前端的 Tech Lead，我深深地理解这一样。特别是不同类型的团队，对于 AIGC 所需要提升的点是大为不同的。

诸如，我们在 Chocolate Factory 构建的**自然语言生成  UI 代码**的示例里，是会根据团队的规范、组件库、业务信息等来生成 UI 代码的。也因此，在不同的场景之下，我们所需要的这种能力也是颇为不同的。哪怕是在金融企业里，不同部门所处的业务领域也会有所差异的。

而会影响构建统一 AIGC 的原因，还包含了（由 ChatGPT 辅助生成）：

- 不同类型的任务和工作流程。一些团队可能需要处理大量数据分析，而其他团队可能更关注客户服务或生产流程。
- 团队规模和组成。不同团队的规模和成员组成也会有所不同。一些团队可能由少数成员组成，而其他团队可能是大规模的企业部门。
- 不同的战略目标和优先级。一些团队可能更关注成本削减，而其他团队可能更关注创新和增长。
- ……

而从另外一个层面来讲，我们在团队拓扑中所定义的不同类型的团队，也会在使用 Team AI 场景上有所差异。诸如于，我们更建议赋能型团队、平台型平台，应该拥有自己的 AIGC 知识聊天助手。

## 什么是 Team AI？

让我们再回到先前的定义：

> Team AI 是一个加速器，旨在协助团队构建轻量级 AIGC 辅助效能提升机制。它可充当任务助手，以简化和加快日常事务中频繁执行的任务；它也可充当知识增强工具，协助团队进行头脑风暴，并更早地在交付过程中发现问题；此外，它还可以充当团队的"合作伙伴"，将团队的约定规范与生成式AI相融合。
>

尽管我们落地 Team AI 的场景更多的是在软件研发上，但是结合我们的 AIGC 应用场景来看，Team AI 可以适用于所有的团队 —— 诸如营销团队，可以构建用户画像，根据用户画像来生成不同的营销方案、营销内容等等。

### Team AI 能做什么？

我们设计 Team AI 的初衷是，构建适用于**团队**的**轻量级、高频/高价值场景**下的 AI 辅助工具。

**轻量级**意味着我们能快速构建和应用我们的 Prompt 或者 AIGC 功能，诸如于 AutoDev 的 Team Prompts 功能，可以直接读取项目中的 promtp，并作为 IDE 功能的一部分。

**高频/高价值场景**。高频场景只是一个相对的值，只要一个任任务相对频繁或者相对比较繁杂，我们就可以考虑结合 AIGC 来辅助提升。

而团队就意味着，要由团队协作来完成自己的 AI 辅助工具。

### 构建 Team AI 所需要的能力

它需要什么样的能力：

- 快速访问不同大模型的能力。除了文本、图像、音频等的大模型，同一类型的模型在能力上也是有所差异的。
- 团队共享的 prompt 空间。根据不同团队的组织目标，创建、存储和组织自定义的 prompt 库。
- 团队协同的 prompt 设计。在内部持续优化和完善提示词，允许存在个人的分支，以确保在内部更好的交流、分享。
- 知识辅助增强能力。即内部可以快速上传文档，并从中检索出关键信息，以生成关键的洞见信息。

应对于这些需求，从我们现有的探索来看，有三种方式能构建我们的 Team AI。

## 如何因地制宜构建 Team AI？

在今天，构建 Team AI 已经变得非常的简单，从我们的案例里找到了三种方式：结合现有工具、定制端到端应用、基于平台能力构建。

### 1. 轻量级方式：结合现有工具

从 Team AI 的角度来说，最简单的方式是结合已有的工具。在有了这个思考之后，我们在 AutoDev 里构建了 Team Prompts。它可以集成到代码库中，以用便于：

- 在团队里，共享你的 prompt，而不再是个性化的配置。
- 可以在各自的团队里分享自己的 AI 经验。
- 不再需要定制更多的 IDE 需求，只需要提供接口能力即可。

那么，对于软件开发团队来说，它就是一种非常简单的 Team AI 方式。当然了，市面上也有非常多的这一类的工具。

### 2. 定制化 Team AI：构建端到端应用

如开头所说，Team AI 从已经构建的内部工具作为起点。它与现有工具相比，更适合于定制团队所需要的端到端方案。

诸如于，在我们的 Team AI 基础代码库中，提供的 SQL 生成示例里，你需要填入一些基础的 SQL 信息。而在多数场景下，我们可以直接使用对应的 Java 对象，或者结合现有的数据库表。在具备了更准确上文的情况下，生成的内容质量更加准确，那么对于开发团队的提升就更高。

而在我们具备了 LLMOps 平台之后，要构建这一类的应用就更加简单。

### 3. 基于平台能力：快速可复用的 AI

今天，我们可以看到有大量的组织构建了自己 LLMOps 平台，并且也有一系列的开源平台，诸如 Dify 等。当然了，我们内部也有一个类型的 LLMOps 平台：GluonMeson，正在计划开源中。

回到这些平台来说，它们都能快速创建应用、生成式应用、会话式应用等等。围绕于这些能力（诸如于 API、多模态），我们能快速构建属于团队的 Team AI。

### 其它

除此，我们也可以从搜索引擎中发现，一些 AI 初创公司也在这个点上发力。通过构建经典的 Team Workspace 方式，来提供这种协作能力，并将不同能力集成在一起。

## 总结

最后，让 ChatGPT 来总结这篇文章：

> Team AI 是一个旨在协助团队提高工作效率的项目，通过简化任务、知识增强和合作伙伴支持。它可以根据不同团队的需求和应用领域，采用不同的构建方式，从结合现有工具到定制化端到端应用，以加速团队的工作流程。 Team AI 的关键目标是为高频、高价值的场景提供轻量级AI辅助工具，以满足团队的特定需求。
