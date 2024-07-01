# AI 辅助软件研发

## Shire 快速入门

### 重构示例

如下是一个基础示例，展示了如何使用 Shire 插件来构建一个简单的 AI 辅助开发人员的指使。

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

随后，便是 AI 生成的结果：

在这次重构中，AI 将原始代码中的计算逻辑提取到了独立的方法中，提高了代码的可读性和可维护性。而在这个简单的示例中，由于产生了更多的方法、行数，代码的复杂度也有所增加。

### 转变为变量方式



```shire
请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。
    
$selection
```

### 优化 Prompt


### 添加到 IDE 中使用

```shire
---
name: "重构代码"
actionLocation: ContextMenu
---

请你这段代码建议适当的重构。提高代码的可读性、质量，使代码更加有组织和易懂。
    
$selection
```

### 丰富 prompt

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


