# 代码文档生成


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
