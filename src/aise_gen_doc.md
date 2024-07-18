# 代码文档生成


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

