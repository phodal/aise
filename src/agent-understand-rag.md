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

### 代码切割

Code Splitter 模块是一个代码分割模块，用于将代码分割成多个片段，以便进行各种代码相关任务，如代码相似度计算、代码分类、代码聚类等。

### 拆分策略

根据《[Chunking 2M+ files a day for Code Search using Syntax Trees](https://docs.sweep.dev/blogs/chunking-2m-files)》 的建议：

1. 代码的平均 Token 到字符比例约为1:5（300 个 Token），而嵌入模型的 Token 上限为 512 个。
2. 1500 个字符大约对应于 40 行，大致相当于一个小到中等大小的函数或类。
3. 挑战在于尽可能接近 1500 个字符，同时确保分块在语义上相似且相关上下文连接在一起。

#### 常规的代码分词

- TF-IDF
- 基于 AST
- 基于行数

多种不同方式：

- 基于关键字分割：LangChain
- 经典语法分析
    - Antlr
- 基于规则 DSL的语法分析：LlamaIndex
    - TreeSitter: [https://tree-sitter.github.io/tree-sitter/](https://tree-sitter.github.io/tree-sitter/)

#### 中文文档分词

分词

- WordNet, [Chinese WordNet](https://github.com/lopentu/CwnGraph)
- Jieba

#### 混合方式

Chunk/Document 拆分策略

1. 如果代码类少于 1500 个字符，则将整个代码类作为一个代码块。
2. 如果代码类大于 1500 个字符，则将代码类分成多个函数代码块。

代码块逻辑

1. 代码块的第一部分是上下文相关的注释，诸如包名、类名等。
2. 代码块的第二部分是代码块的内容。

示例：

```chunk
// canonicalName: com.google.common.collect.ImmutableList

public static <T> ImmutableList<T> of(T... elements) {
    List<T> list = new ArrayList<>();
    Collections.addAll(list, elements);
    return new ImmutableList<>(list);
}
```

### 向量化（Embedding）

向量化模型

#### 模型选择

> Sentence Transformers 是一个自然语言处理工具，用于将文本句子嵌入到一个高维向量空间中，以便进行各种文本相关任务，如文本相似度计算、
> 文本分类、聚类等。它是通过预训练的深度学习模型实现的，通常使用诸如BERT、RoBERTa、DistilBERT等预训练模型作为其基础架构。

在这里，我们使用的 SentenceTransformers
模型是：[sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)，
在体积上只有 22M，因此被 Bloop、GitHub Copilot 作为本地向量化模型，也因此是 ChocoBuilder 的默认的本地矢量化模块。

- all-MiniLM-L6-v2 支持转为 384 维稠密向量空间（dimensional dense vector space），即 384

可以使用 [optimum](https://github.com/huggingface/optimum) 优化模型，将模型转换为 ONNX 格式，以便于在本地进行推理。

#### 模型训练

OnnxRuntime

### Searching

存储与搜索

#### 存储介质

#### 搜索算法



