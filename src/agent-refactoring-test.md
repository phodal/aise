# 编码智能体：测试智能体与 IDE 插件结合

## 示例

### AutoDev

https://ide.unitmesh.cc/custom/extension-context-agent

```json
{
    "name": "@autodev.ext-context.test",
    "description": "AutoTest",
    "url": "http://127.0.0.1:8765/api/agent/auto-test",
    "responseAction": "Direct"
}
```

对应的模板文件如下：

```Velocity
Write unit test for following ${context.lang} code.

${context.frameworkContext}

#if( $context.relatedClasses.length() > 0 )
Here is the relate code maybe you can use
${context.relatedClasses}
#end

#if( $context.currentClass.length() > 0 )
This is the class where the source code resides:
${context.currentClass}
#end
${context.extContext}
Here is the source code to be tested:

${context.imports}
${context.sourceCode}

#if($context.isNewFile)
Should include package and imports. Start method test code with Markdown code block here:
#else
Should include package and imports. Start ${context.testClassName} test code with Markdown code block here:
#end
```

对应的 Kotlin 代码：

```Kotlin
private fun getCustomAgentTestContext(testPromptContext: TestCodeGenContext): String {
    if (!project.customAgentSetting.enableCustomRag) return ""

    val agent = loadTestRagConfig() ?: return ""

    val query = testPromptContext.sourceCode
    val stringFlow: Flow<String> = CustomAgentExecutor(project).execute(query, agent) ?: return ""

    val responseBuilder = StringBuilder()
    runBlocking {
        stringFlow.collect { string ->
            responseBuilder.append(string)
        }
    }

    return responseBuilder.toString()
}
```