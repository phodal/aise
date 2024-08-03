# AI 辅助软件工程：系统迁移

## 示例

### Ebay：定期维护和升级基础设施

《[Cutting Through the Noise: Three Things We've Learned About Generative AI and Developer Productivity](https://innovation.ebayinc.com/tech/features/cutting-through-the-noise-three-things-weve-learned-about-generative-ai-and-developer-productivity/)》

现有的开源大型语言模型有时会达到生产力的上限；毕竟，从一个不包含我们内部数据的模型中，我们能学到的东西是有限的。因此，第二条路径是使用我们组织预处理后的数据对开源的LLMs进行后期训练和微调。

在这个练习中，我们使用了Code Llama 13B作为基础LLM，不过如果有需要，也可以轻松替换成其他模型。为了看看后期训练和微调的现有
LLM 效果如何，
我们创建了一个我们称之为eBayCoder的模型：这是一个基于eBay代码库和相关文档训练的Code Llama。

那么效果如何呢？我们发现，eBayCoder能够显著简化一些之前劳动密集型且耗时的任务。例如，软件维护在所有技术组织中都至关重要。和其他大型公司一样，eBay
也有自己基于开源软件构建的基础库和框架，覆盖服务器、消息队列、批处理作业、iOS和Android等。这些系统需要定期升级，
以改进开发人员的工作体验并解决安全漏洞（例如升级到最新的Spring或Spring Boot版本）。这种工作量视当前应用栈的版本而定，有时甚至会非常庞大。
即使使用eBay现有的迁移工具，我们仍需投入大量工程资源进行软件维护。而这是我们认为微调后的LLM在短期内已经能够产生巨大影响的一个领域。

对于像eBay这样庞大且多样的代码库，我们有时也会遇到一个问题，即现有的商业LLM产品只能访问与当前问题直接相关的数据和代码，通常是周围的文件、
当前的代码库以及一些依赖库。它可能无法察觉到其他团队维护的不同内部服务或非依赖库中提供的相同功能。这往往导致大量的代码重复。
但一个微调后的LLM可以访问我们希望的尽可能多的上下文，从而有可能减少代码重复的数量。

### Amazon 遗留基础设施改造

许多组织面临维护关键遗留Java应用程序的挑战，这些应用程序由于框架过时、代码无文档和安全漏洞而变得难以维护。现代化这些应用程序是必要且具有挑战性的任务。Amazon
Q Developer简化并加速了这一过程。

**使用Amazon Q Developer的现代化过程**

1. **升级Java版本：**
    - 从Java 8升级到Java 17，以提高性能、安全性并利用新功能。
    - Amazon Q Developer代码转换代理通过分析代码、生成转换计划并更新框架和库以兼容Java 17来自动化这一过程。

2. **减少技术债务：**
    - 识别并解决代码库中的技术债务，以提高代码质量和可维护性。
    - 使用Amazon Q Developer生成技术债务问题列表并提出改进建议。
    - 实施建议，如改进日志记录和模块化，以减少技术债务。

3. **云原生部署：**
    - 将应用程序迁移到云原生架构并部署到AWS。
    - 步骤包括将应用程序容器化，使用Amazon Elastic Container Registry（ECR），在AWS Fargate上部署到Amazon Elastic Container
      Service（ECS），并设置Amazon CloudWatch进行监控。
    - Amazon Q Developer帮助生成用于容器化的Dockerfile和用于基础设施部署的CloudFormation模板。

