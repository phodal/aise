# 单元测试生成


```shire
---
name: "Auto Test"
description: "AutoTest"
interaction: RunPanel
actionLocation: ContextMenu
when: $fileName.contains(".java") && $filePath.contains("src/main/java")
fileName-rules:
  /.*Controller.java/: "When testing controller, you MUST use MockMvc and test API only."
variables:
  "extContext": /build\.gradle\.kts/ { cat | grep("org.springframework.boot:spring-boot-starter-jdbc") | print("This project use Spring Framework")}
  "testTemplate": /\(.*\).java/ {
    case "$1" {
      "Controller" { cat(".shire/templates/ControllerTest.java") }
      "Service" { cat(".shire/templates/ServiceTest.java") }
      default  { cat(".shire/templates/DefaultTest.java") }
    }
  }
onStreamingEnd: { parseCode | saveFile }
---
Write unit test for following ${context.language} code.

${context.frameworkContext}

#if($context.relatedClasses.length() > 0 )
Here is the relate code maybe you can use
${context.relatedClasses}
#end

#if($context.currentClassName.length() > 0 )
This is the class where the source code resides:
${context.currentClassCode}
#end

${context.extContext}

Here is the imports to help you understand:

${context.imports}

Here is the source code to be tested:

```${context.language}
${context.selection}
```

#if($context.isNewFile)
Start method test code with Markdown code block here:
#else
Start ${context.targetTestFileName} test code with Markdown code block here:
#end
```

