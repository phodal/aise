# 理解 RAG 的应用

## 分词

- WordNet, [Chinese WordNet](https://github.com/lopentu/CwnGraph)
- Jieba
- TF-IDF

## RAG 示例

```shire
---
name: "Search"
variables:
  "testTemplate": /.*.java/ { caching("disk") | splitting | embedding | searching("comment") }
---

根据如下的代码，回答用户的问题：博客创建的流程

$testTemplate
```

