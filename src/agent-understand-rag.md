# 理解 RAG 的应用


## RAG 应用开发过程

Shire RAG 示例

```shire
---
name: "Search"
variables:
  "testTemplate": /.*.java/ { caching("disk") | splitting | embedding | searching("comment") }
---

根据如下的代码，回答用户的问题：博客创建的流程

$testTemplate
```

### Chunking 

#### 常规的代码分词

- TF-IDF
- 基于 AST
- 基于行数

#### 中文文档分词

分词

- WordNet, [Chinese WordNet](https://github.com/lopentu/CwnGraph)
- Jieba

### 向量化（Embedding）

向量化模型

#### 模型选择

#### 模型训练

OnnxRuntime


### Searching

存储与搜索

#### 存储介质


#### 搜索算法



