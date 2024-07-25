# AI 辅助软件工程：AI 辅助软件质量


## 示例

### 案例：TestSpark

[TestSpark](https://github.com/JetBrains-Research/TestSpark) 是一个用于生成单元测试的插件。TestSpark 能够在 IDE 中原生集成多种基于 AI 的测试生成工具和技术。

Paper: [TestSpark: IntelliJ IDEA’s Ultimate Test Generation Companion](https://arxiv.org/html/2401.06580v1)

![](images/llm-based-test-gen.png)

TestSpark 目前支持两种测试生成策略：

1. 基于大语言模型（LLM）的测试生成（使用 OpenAI 和 JetBrains 内部的 AI Assistant 平台）
2. 基于局部搜索的测试生成（使用 EvoSuite）

### 基于大语言模型的测试生成

对于这种测试生成方式，TestSpark 向不同的大语言模型发送请求。此外，它会在向用户展示测试之前自动检查测试是否有效。

此功能需要从 OpenAI 平台或 AI Assistant 平台获取一个 token。

- 支持任何版本的 Java。
- 生成用于捕获故障的单元测试。
- 为 Java 类、方法和单行代码生成测试。

### 基于本地搜索（search-based）的测试生成

对于此类测试生成方法，TestSpark 采用了 EvoSuite，这是目前最强大的基于搜索的本地测试生成工具。

- 它只支持 Java 11 **及以下**版本。
- 根据多样的测试标准生成测试用例，包括行覆盖率、分支覆盖率、I/O 多样性、异常覆盖率和变异得分。
- 能够生成用于检测故障的单元测试。
- 为 Java 中的类、方法以及单行代码提供测试生成服务。

### 案例：UnitTestBot

[UnitTestBot](https://github.com/UnitTestBot)

Java 版本：[UnitTestBot](https://github.com/UnitTestBot/UTBotJava)


我们是一支分布式的研究人员和工程师团队🙋‍。

我们所有人都对数学和编程充满热情。我们热衷于参加软件测试[比赛](https://ieeexplore.ieee.org/document/9810769)并在[研究文章](https://www.utbot.org/research)中描述我们的成就。

我们的主要项目是我们的旗舰产品——[UnitTestBot](https://www.utbot.org/)，它支持Java/Kotlin、C/C++、Python、JavaScript和Go语言。

为了保持与前沿科学的联系，我们与顶尖大学合作。作为校际团队的一部分，我们开发了根本技术，以增强UnitTestBot以及其他一系列软件产品。以下是其中一些：

#### 🤓 SAT求解技术

SAT求解器是一种计算机程序，用于确定给定布尔公式的变量是否可以一致地替换为_True_或_False_，从而使公式的结果为_True_。SAT求解器经常被用作程序验证应用程序的“引擎”。
- [KoSAT](https://github.com/UnitTestBot/kosat)是一个基于MiniSat核心的纯Kotlin CDCL SAT求解器。它解决以DIMACS格式给定的布尔可满足性问题，并支持增量求解。
- 我们还研究了与SAT求解相关的[更广泛的理论问题](https://www.utbot.org/research)，例如评估给定SAT问题的计算难度。

#### 🧐 SMT求解技术

可满足性模理论（SMT）研究领域涉及确定逻辑公式是否可满足。

[KSMT](https://github.com/UnitTestBot/ksmt)是各种SMT求解器的Java/Kotlin门面。目前，它支持Z3和Bitwuzla SAT求解器。

#### 😎 符号执行

利用SAT和SMT求解器，我们开发了符号执行技术，以为我们的精确代码分析和自动化测试生成工具提供有效的引擎。在这个研究领域，我们有三个主要解决方案。

- [UnitTestBot Java](https://github.com/UnitTestBot/UTBotJava)有自己的动态符号执行引擎，已在[SBST比赛](https://ieeexplore.ieee.org/document/9810769)中表现出色。
- 我们为KLEE定制的补丁是[UnitTestBot C/C++](https://github.com/UnitTestBot/UTBotCpp)的核心。KLEE是一个基于LLVM编译器基础架构的符号虚拟机。我们通过实现补丁来[贡献给KLEE](https://github.com/UnitTestBot/klee)，提高引擎的代码覆盖率和速度。我们提出了_懒初始化改进_，并向主KLEE分支提交了_未定义行为检测补丁_以及_内联汇编支持补丁_。
  我们将KLEE转换为_双向属性导向符号执行_引擎。此外，补丁后的KLEE引擎能够自动推导方法摘要。
- 我们还计划通过[V#](https://github.com/VSharp-team/VSharp)支持.NET基础架构——这是一个完全自动化测试生成的符号执行引擎。

符号执行是我们的主要关注点，因此我们进行了[一系列研究](https://www.utbot.org/research)，涉及该领域的应用和基础问题。

#### 🤪 模糊测试

在开发UnitTestBot产品系列的过程中，我们开发了适用于所有支持语言（Java/Kotlin、C/C++、Python、JavaScript和Go）的[模糊测试和动态程序分析技术](https://github.com/UnitTestBot/UTBotJava/tree/pelevin/UnitTestBot_Family_Fuzzer_Platform/utbot-fuzzers)。

#### 🙂 程序分析

UnitTestBot及其符号执行引擎和模糊测试技术是[现成的](https://github.com/UnitTestBot/UTBotJava/wiki/Static-code-analysis-with-UTBotJava-action)用于[代码分析](https://github.com/UnitTestBot/UTBotCpp/wiki/CodeAnalyzer)的工具。除了这一端到端解决方案外，我们还实现了一个开发自定义静态代码分析器的基本框架。

[Java编译数据库（JacoDB）](https://github.com/UnitTestBot/jacodb)受到了[Soot](https://github.com/soot-oss/soot)框架的启发，用于分析和转换Java代码。

JacoDB是一个纯Java数据库，存储关于编译后的Java字节码的信息——类、层次结构、注释、方法、字段及其用法。使用JacoDB，可以分析JVM进程外的字节码。这使得UnitTestBot能够支持最新的JDK，并在重启之间重用数据。

#### 🙃 程序合成

我们研究合成代码以解决实际问题的方法。
例如，UnitTestBot能够基于公共API而不是反射[生成人类可读的测试方法体](https://github.com/UnitTestBot/UTBotJava/pull/1030)。

我们还开发了**genui**项目——一个自动化UI生成工具。在我们的研究中，我们[探讨](https://icfp22.sigplan.org/details/minikanren-2022-papers/3/On-a-Declarative-Guideline-Directed-UI-Layout-Synthesis)了根据指定的设计指南自动排列用户界面元素的方法。下一步是合成能够实现此布局的代码。
