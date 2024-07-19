# AI 辅助软件工程：代码注释生成

## Prompt 示例

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

## 示例

### JetBrains

```kotlin
enum class WdRiderEntity {
    ClassContextEntry,
    StructContextEntry,
    InterfaceContextEntry,
    PropertyContextEntry,
    MethodContextEntry,
    VariableContextEntry,
    EnumContextEntry,
    EnumEntryContextEntry;
}

fun StringBuilder.renderContext(options: WdPromptOptions.Rider) {
    when (options.entity) {
        WdRiderEntity.ClassContextEntry -> append("Write documentation for given class ${options.name}.")
        WdRiderEntity.StructContextEntry -> append("Write documentation for given struct ${options.name}.")
        WdRiderEntity.InterfaceContextEntry -> append("Write documentation for given interface ${options.name}.")
        WdRiderEntity.PropertyContextEntry -> append("Write documentation for given property ${options.name}.")
        WdRiderEntity.MethodContextEntry -> renderMethodContext(this, options)
        WdRiderEntity.VariableContextEntry -> append("Write documentation for given variable ${options.name}.")
        WdRiderEntity.EnumContextEntry -> append("Write documentation for given enum ${options.name}.")
        WdRiderEntity.EnumEntryContextEntry -> append("Write documentation for given enum member ${options.name} of enum ${options.enumName}.")
    }
}
```


