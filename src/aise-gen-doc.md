# AI 辅助软件工程：代码文档生成


```shire
---
name: "Context Variable"
description: "Here is a description of the action."
interaction:  RunPanel
variables:
  "contextVariable": /ContextVariable\.kt/ { cat }
  "psiContextVariable": /PsiContextVariable\.kt/ { cat }
onStreamingEnd: { saveFile("docs/api.md")  }
---

根据如下的代码编写 API 文档：

/file:src/main/java/com/phodal/shire/demo/controller/BlogController.java
```

## JetBrains  示例

```kotlin
private fun renderTask(renderTask: StringBuilder, language: String) {
    val prompt = when (language) {
        "ObjectiveC" -> "Write doxygen."
        "kotlin" -> "Write KDoc."
        "C#" -> "Write C# doc."
        "F#" -> "Write F# doc."
        "go" -> "Write Go Doc."
        "C++" -> "Write doxygen, do not use @file tag."
        "PHP" -> "Write PHPDoc."
        "HTML" -> "Write JSDoc."
        "JAVA" -> "Write javadoc."
        "Ruby" -> "Write RDoc documentation."
        "TypeScript" -> "Write JSDoc."
        "JavaScript" -> "Write JSDoc."
        else -> ""
    }

    if (prompt.isNotEmpty()) {
        renderTask.append(prompt).append('\n')
    }
}
```

