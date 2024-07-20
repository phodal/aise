# AI 辅助软件工程：重构代码示例

如下是[Tabnine 总结](https://www.tabnine.com/blog/ai-code-refactoring-7-ways-tabnine-transforms-refactoring/)的 AI
代码重构的优势：

1. **提高效率**：AI驱动的重构工具能够快速处理和分析大型代码库，比人类开发者更快地识别出需要改进的区域。
2. **提升代码质量**：通过一致地应用最佳实践和编码标准，AI重构工具有助于整体提升代码质量。它们可以发现并修复代码异味、冗余代码和其他在手动重构过程中可能被忽略的问题。
3. **改进可维护性**：AI重构可以持续进行，确保代码库保持干净和有序。这提高了代码的可读性，降低了新团队成员的学习曲线，并有助于项目的长期可持续性。
4. **减少错误**：自动化重构可以最大限度地减少手动重构过程中可能发生的人为错误。AI工具可以确保重构不会引入新的错误，从而维护代码的功能完整性。
5. **代码库的一致性**：AI驱动的重构工具可以在大型项目的不同部分或组织内的多个项目中强制执行一致的编码风格和实践。
6. **节约成本**：通过减少代码维护所需的时间和精力，AI重构工具可以带来显著的成本节约。这使公司能够更有效地分配开发资源，将资源从维护转向创新。

## 重构依赖的上下文

这些本地上下文包括：

- 你之前的问题或 prompt
- 当前文件中选定的代码块（或光标位置）
- 当前打开的文件及其他打开的文件
- 当前对话的聊天记录，包括所有之前的问题和答案
- 当前用户工作区中的相关文件或代码块
- 运行时错误
- 导入的库
- 编译/语法错误
- 非代码来源的信息
- 当前选定的代码
- 已连接的存储库
- 对话历史
- Git 历史
- 项目元数据和其他项目文件

诸如于 Tabnine，还提供了更高级的方式去获取上下文：

- Tabnine 的企业版还会从已连接的存储库中获取全局上下文。
- 你可以微调你的私人 Tabnine 模型，以获得更加个性化的 AI 重构工具。

## 重构 Shire 示例

### 步骤 1. 一个简单的示例

如下是一个基础示例，展示了如何使用 Shire 插件来构建一个简单的 AI 辅助开发人员的指令。只需要在 IDE 中新建一个 Shire 文件，然后将以下内容复制到文件中：

    请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。
    
    ```java
    public class Main {
        public static void main(String[] args) {
            int a = 5;
            int b = 10;
            int c = a + b;
            System.out.println("Sum: " + c);
            int d = a - b;
            System.out.println("Difference: " + d);
            int e = a * b;
            System.out.println("Product: " + e);
            int f = b / a;
            System.out.println("Quotient: " + f);
        }
    }
    ```

就可以直接在 IDE 中运行 Shire 插件，获取到 AI 重构的结果。如下是零一万物 API 返回的结果

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        
        int sum = add(a, b);
        System.out.println("Sum: " + sum);
        
        int difference = subtract(a, b);
        System.out.println("Difference: " + difference);
        
        int product = multiply(a, b);
        System.out.println("Product: " + product);
        
        int quotient = divide(b, a);
        System.out.println("Quotient: " + quotient);
    }
    
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static int subtract(int a, int b) {
        return a - b;
    }
    
    public static int multiply(int a, int b) {
        return a * b;
    }
    
    public static int divide(int a, int b) {
        return a / b;
    }
}
```

在上述示例中，AI 重构工具 Shire 对原始 Java 代码进行了以下改进：

- **提取方法**：将重复的计算逻辑提取到单独的方法中，提高了代码的可重用性和可读性。
- **命名改进**：为变量和方法提供了更有意义的名称，如 `sum`、`difference`、`product`、`quotient`
  ，以及 `add`、`subtract`、`multiply`、`divide`，使得代码意图更加清晰。
- **代码组织**：通过将计算逻辑放入单独的方法，使得 `main` 方法更加简洁，易于理解。

通过这些重构，代码变得更加模块化，易于维护，并且对于其他开发者来说也更加易于理解。这种重构不仅提高了代码的质量，也使得未来的修改和扩展变得更加容易。

### 步骤 2.将代码转变为变量方式

步骤 1 的代码是我们写死的，为了更加通用，我们可以将代码转变为变量方式：

```shire
请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。
    
$selection
```

随后，可以配置到右键菜单中，如下：

```shire
---
name: "重构代码"
actionLocation: ContextMenu
---

请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。
    
$selection
```

如此一来，我们就可以在 IDE 中右键选择代码，然后直接进行重构。

PS：当前的 Shire 插件为了确保性能，需要用户重新启动 IDE，才可在右键菜单中看到新的菜单项。 

### 步骤 3. 丰富我们的 prompt

如果你不熟悉如何针对代码进行重构，可以参考一些主流工具的重构提示词。如下是我们结合了 JetBrains AI Assistant 的提示词所构建的 prompt：

```shire
---
name: "Refactoring"
actionLocation: ContextMenu
interaction: ReplaceSelection
---

请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。你的回答应包含重构描述和一个代码片段，展示重构后的结果。
使用一些众所周知的重构技巧，比如以下列表中的一个：

- 重命名
- 修改签名、声明
- 提取或引入变量、函数、常量、参数、类型参数
- 提取类、接口、超类
- 内联类、函数、变量等
- 移动字段、函数、语句等
- 上移构造函数、字段、方法
- 下移字段、方法

请勿生成多个代码片段，尝试将所有更改都整合到一个代码片段中。
请勿生成包含虚构周围类、方法的代码。不要模拟缺失的依赖项。
提供的代码已经整合到正确且可编译的代码中，不要在其周围添加额外的类。

重构以下代码：

$selection
```

### 丰富上下文

这里有一些相关的 Code Smell

// - Method 'updatePost(java.lang.Long, com.phodal.shire.demo.entity.BlogPost)' is never used
// - String can be replaced with text block

## 其它

## 示例

### Tabnine 示例

[AI code refactoring: 7 ways Tabnine transforms refactoring](https://www.tabnine.com/blog/ai-code-refactoring-7-ways-tabnine-transforms-refactoring/)

1. **自动重构代码**：Tabnine可以根据需要自动重构代码，例如更换技术方法、简化复杂函数或处理错误。
2. **解释现有代码以规划重构**：Tabnine可以解释代码，并根据解释提供的上下文进行准确的重构建议。
3. **复杂项目的高层次概述**：通过Tabnine Onboarding Agent，可以快速获得项目的总体结构和关键依赖，减少上手时间。
4. **个性化的AI重构建议**：Tabnine利用本地工作区的信息提供个性化的重构建议，包括以前的问题、当前文件中的代码块、运行时错误、导入的库等。
5. **安全的重构建议**：Tabnine Protected Model只训练于许可开源库，确保重构建议不包含专有代码，保护组织免受知识产权风险。
6. **支持多种编程语言和IDE**：Tabnine支持80多种编程语言和框架，以及多种流行的IDE，提供全面的本地上下文感知和其他功能。
7. **使用首选的大语言模型进行AI重构**：Tabnine支持在多个大语言模型之间实时切换，用户可以根据项目需求选择不同的模型，以获得最佳的隐私保护和性能。

通过结合AI代码重构的优势和Tabnine的变革性功能，开发团队能够显著提升工作效率和代码质量，同时降低成本和错误率。

### JetBrains 示例

    You should suggest appropriate refactorings for the code. Improve code readability, code quality, make the code more organized and understandable. 
    Answer should contain refactoring description and ONE code snippet with resulting refactoring.  
    Use well-known refactorings, such as one from this list:
    - Renaming
    - Change signature, declaration
    - Extract or Introduce variable, function, constant, parameter, type parameter
    - Extract class, interface, superclass
    - Inline class, function, variable, etc
    - Move field, function, statements, etc
    - Pull up constructor, field, method
    - Push down field, method.
    Do not generate more than one code snippet, try to incorporate all changes in one code snippet. 
    Do not generate mock surrounding classes, methods. Do not mock missing dependencies. 
    Provided code is incorporated into correct and compilable code, don't surround it with additional classes. 
    Refactor the following code:
