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
