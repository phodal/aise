# AI 辅助软件工程：遗留系统重构与迁移

## 安全守护的遗留系统迁移

《[系统重构与迁移指南](https://github.com/phodal/migration)》

从模式上来说，遗留系统重构的过程可以简单分为：

1. **理解现有业务**  
   理解现有业务是遗留系统重构的第一步。这需要分析现有代码库，以获取系统的业务逻辑和结构。
    - **[Sourcery](https://sourcery.ai/)**: 用于代码分析和重构的工具，能够自动建议代码改进，并提供理解代码的上下文。
    - **[Semgrep](https://semgrep.dev/)**: 基于语义搜索的静态代码分析工具，可以快速查找和理解关键业务逻辑。
2. **设计与拆分模块**  
   在理解现有系统的基础上，设计新的架构并拆分为更小的模块。
3. **构建测试防护网**  
   构建测试用例和覆盖率，以确保重构过程中的系统功能不被破坏。
4. **代码重构以迁移**  
   代码重构是将系统从旧平台或语言迁移到新的平台或语言时的重要步骤。
    - **[sqlc](https://sqlc.dev/)**: 将 SQL 查询生成 Golang 代码的工具，有助于将数据库操作集成到现代代码中。
    - **[Jooq](https://www.jooq.org/)**: Java 库，从 SQL 生成 Java 代码，实现从 SQL 到 Java 的迁移。
5. **验证与测试**  
   迁移后的系统需要经过充分的验证与测试，以确保其行为与原系统一致。
    - **[Testcontainers](https://www.testcontainers.org/)**: 开源 Java 库，支持在 Docker 容器中运行集成测试，以确保系统在不同环境下的一致性。
    - **[Applitools](https://applitools.com/)**: 利用 AI 进行视觉回归测试，确保 UI 在代码变更后的视觉一致性。
    - **[RestQA](https://restqa.io/)**: 开源测试框架，支持记录和复用 API 请求，简化测试数据管理。

## 代码理解与分析

遗留系统的一大痛点是没有知道业务知识，所以在生成式 AI 的加持下，问题域可以变为：

- 如何结合从现有的代码中知道业务的实现。即结合语义化搜索与 RAG，将用户的查询转换为代码搜索，最后交由 AI 来总结。
- 如何可视化业务逻辑。在不同的场景之下，实现功能的要求也是不一样的。从可视化的角度来说，我们可以将代码转换为
  DSL，再结合可视化工具来展示。

### 代码理解：基于 AI 的代码解释

遗留系统往往缺乏完整的文档和注释，理解这些代码对于开发者来说是一个巨大的挑战。AI工具能够通过代码解析与可视化技术，帮助开发者快速理解代码结构与逻辑。例如，IBM
Watsonx Code Assistant for Z通过AI生成的解释和文档，帮助开发者更好地掌握系统的全貌。

### 代码可视化分析：基于活文档

如结合我们以往的工具，我们在 AutoDev 的文档生成功能中添加了活文档（Living Documentation）的功能，你可以结合注解从现有的逻辑中可视化业务。

如下是一个结合 AutoDev 生成活文档的示例：

```Java
@ScenarioDescription(
  given = "a file with name $filename and program text $programText",
  when = "the function tryFitAllFile is called with maxTokenCount $maxTokenCount, language $language, and virtualFile $virtualFile",
  then = "the function should return an ErrorScope object with the correct values"
)
```

随后，就可以清晰地呈现已有的逻辑实现。

### 代码重构与转换

由于不同语言间存在一些能力等的差异，所以我们需要考虑到不同的语言的场景。诸如于，在 AutoDev 中针对于 PL/SQL 构建了相似的功能：

- 从 SQL 代码生成 entity 代码。
- 从 SQL 代码生成 Java 测试。
- 从 SQL 代码生成 Java 代码。

考虑到对于语言的理解，能力还是有待进一步完善的。

### 中间表示：结合 AST 工具的代码重构

https://research.google/blog/accelerating-code-migrations-with-ai/

多年来，谷歌一直使用专门的基础设施来执行复杂的代码迁移。该基础设施使用静态分析和如 [Kythe](https://kythe.io/)
和 [Code Search](https://abseil.io/resources/swe-book/html/ch17.html)
等工具来发现需要更改的位置及其依赖关系。然后使用如 [ClangMR](https://clang.llvm.org/docs/RefactoringEngine.html) (Clang’s
refactoring engine)等工具进行更改。

ClangMR 示例：

```C++
class LocalRename final : public RefactoringAction {
public:
  StringRef getCommand() const override { return "local-rename"; }

  StringRef getDescription() const override {
    return "Finds and renames symbols in code with no indexer support";
  }

  RefactoringActionRules createActionRules() const override {
    ...
  }
};
```

Kythe, 这是一个可插拔的、（几乎）与语言无关的生态系统。它旨在帮助开发者构建与代码协同工作的工具。

```Bash
print_classes() {
  kythe ls --uris --files "kythe://kythe?path=$1" \
    | parallel kythe refs --format "'@target@ @edgeKind@ @nodeKind@ @subkind@'" \
    | awk '$2 == "/kythe/edge/defines" && $3 == "record" && $4 == "class" { print $1 }' \
    | xargs kythe edges --targets_only --kinds /kythe/edge/named \
    | awk '{ print substr($0, index($0, "#")+1) }' \
    | parallel python -c '"import urllib, sys; print urllib.unquote(sys.argv[1])"'
}

print_classes kythe/java/com/google/devtools/kythe/analyzers/java/
print_classes kythe/cxx/tools/fyi/
```

### 经典转换工具

JavaPoet, KotlinPoet

### 测试生成与验证

AI 生成单元测试

传统的 API 记录？工具，记录测试数据，让 AI 自动验证

## 示例

### IBM [Watsonx Code Assistant for Z](https://www.ibm.com/products/watsonx-code-assistant-z)

IBM watsonx™ Code Assistant for Z 是一款生成式人工智能辅助产品，旨在以低于当前替代方案的成本和风险，加速大型机应用的现代化进程。

![](images/ibm-watsonx-code-assistant-for-z.webp)

watsonx Code Assistant for Z 为开发者提供了一个端到端的应用开发生命周期，包括应用发现与分析、自动化代码重构、COBOL 到 Java
的转换、 自动化测试生成以及代码解释等功能。开发者可以自动重构应用中的选定元素，继续在 COBOL 中进行现代化，或者利用高度优化的先进大型语言模型，
通过生成式人工智能有选择地将代码转换为 Java。

1. 理解。深入了解您的主机应用程序，并可视化它们之间的关系与依赖。利用生成式人工智能对代码进行解释，自动记录您的COBOL应用程序，帮助新程序员快速上手。
2. 重构。发现程序及数据，以自动重构您的应用程序，将其转化为更独立业务服务，推动功能增强并提高可维护性，同时为COBOL的选转型至Java做好准备。
3. 转换。利用生成式人工智能，在几分钟内而非数月内加速高质量的COBOL至Java转换。
4. 验证。简化并加速新Java代码的测试过程，确保其与COBOL代码在语义上等效，以提高质量和降低风险。
5. 推荐。推荐并部署最适合的架构。
6. 观测。在混合应用/混合云环境中进行观测。

### Bloop

[State of Mainframe Modernization](https://www.kyndryl.com/us/en/campaign/state-of-mainframe-modernization)

#### 转换 HumanEval 数据集

构建评估工具：[COBOLEval](https://github.com/BloopAI/cobolEval)

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. HAS-CLOSE-ELEMENTS.

       ENVIRONMENT DIVISION.

       INPUT-OUTPUT SECTION.

       DATA DIVISION.

       LINKAGE SECTION.

       01 LINKED-ITEMS.
           05 L-NUMBERS OCCURS 100 TIMES INDEXED BY NI COMP-2.
           05 L-THRESHOLD COMP-2.
           05 RESULT PIC 9.

      * Check if in given list of numbers, are any two numbers closer to each other than
      * given threshold.
      * >>> has_close_elements([1.0, 2.0, 3.0], 0.5)
      * False
      * >>> has_close_elements([1.0, 2.8, 3.0, 4.0, 5.0, 2.0], 0.3)
      * True
      *

      * Complete the WORKING-STORAGE SECTION and the PROCEDURE DIVISION
      * Store the result in the RESULT variable and mark the end of your program with END PROGRAM

       WORKING-STORAGE SECTION.
```

- [Evaluating LLMs on COBOL](https://bloop.ai/blog/evaluating-llms-on-cobol)
- [GnuCOBOL](https://gnucobol.sourceforge.io/)

### SourceGraph Cody示例

资料来源：[A simpler way to understand legacy code](https://sourcegraph.com/blog/a-simpler-way-to-understand-legacy-code)

![](images/aise-legacy-cod.png)

这篇文章介绍了构建遗留系统重构的过程和策略，并提供了一些实用工具来帮助开发人员理解和改进遗留代码。

**主要流程和策略如下：**

1. **评估代码库：**
    - 设置开发环境并运行代码以确保其按预期工作。
    - 使用代码静态检查工具（如ESLint或Pylint）来识别语法错误和潜在问题。
    - 使用依赖关系分析工具和架构可视化工具来了解项目的依赖关系和结构。
2. **文档和注释：**
    - 利用现有的文档和注释来获取代码的原始目的、设计决策和潜在问题的洞察。
    - 对缺乏文档的遗留系统进行文档补充和注释更新。
3. **代码分析工具：**
    - 使用静态分析工具（如SonarQube、PMD、CAST）来识别代码问题、代码异味和安全漏洞。
    - 这些工具还能揭示代码依赖关系和结构，帮助开发人员确定重构的优先级。
4. **版本控制历史：**
    - 利用版本控制系统（如Git）来理解代码库的历史，通过分析提交日志来追踪代码的变更。
    - 使用`git blame`和`git log`命令来了解每行代码的最后修改情况及其原因。
5. **重构和清理：**
    - 在不改变外部行为的前提下对代码进行重构，以提高代码的可维护性和可读性。
    - 采用小规模、可管理的更改，使用特性分支并持续测试代码，以验证重构未影响功能。
6. **测试和验证：**
    - 编写单元测试、集成测试和端到端测试来验证更改，防止回归问题。
    - 在没有测试的遗留代码上编写测试，以确保代码可靠性。

**使用Cody的辅助工具：**

Cody是一款AI编程助手，旨在帮助开发人员理解、编写、审查和重构代码，并加速代码生成和软件开发。它的主要功能包括：

- **自动完成**：利用大语言模型（LLM）提供代码预测和建议，支持多种编程语言。
- **聊天功能**：回答与代码相关的技术问题，并提供上下文答案。
- **命令功能**：运行预定义操作并创建自定义命令以加速日常编码任务。

通过这些功能，Cody可以帮助开发人员理解遗留代码结构，识别潜在问题，并提出改进建议。

**使用Cody的实际示例：**

1. **重构代码**：Cody可以识别代码异味并建议改进。
2. **编写单元测试**：Cody可以生成单元测试代码，帮助验证代码的预期行为。
3. **生成文档**：Cody可以自动生成代码文档，帮助未来的协作者理解代码。

**总结：**

通过评估代码库、利用文档、使用代码分析工具、理解版本控制历史、谨慎重构和全面测试，开发人员可以有效地理解和改进遗留代码。AI编程助手如Cody能够进一步简化这些过程，提供有价值的见解和自动化支持，使处理遗留系统变得更容易和高效。

