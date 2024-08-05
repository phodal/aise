# AI 辅助软件工程：遗留系统重构与迁移

## 安全守护的遗留系统迁移

## 基于 AI 的遗留系统重构

## 代码理解与分析

### 代码理解：基于 AI 的代码解释

遗留系统往往缺乏完整的文档和注释，理解这些代码对于开发者来说是一个巨大的挑战。AI工具能够通过代码解析与可视化技术，帮助开发者快速理解代码结构与逻辑。例如，IBM
Watsonx Code Assistant for Z通过AI生成的解释和文档，帮助开发者更好地掌握系统的全貌。

### 代码可视化分析：基于活文档

### 代码重构与转换

### 中间表示：结合 AST 工具的代码重构

### 经典转换工具

JavaPoet, KotlinPoet

### 测试生成与验证

AI 生成测试，自动化测试生成

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

