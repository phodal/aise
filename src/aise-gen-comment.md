# 代码注释生成

## Prompt 示例

```shire
---
name: "生成注释"
interaction: InsertBeforeSelection
actionLocation: ContextMenu
when: $fileName.contains(".java") && $filePath.contains("src/main/java")
onStreamingEnd: { insertNewline | formatCode }
---

为如下的代码编写注释，使用 javadoc 风格：

```$language
$selection
```

只返回注释
```
