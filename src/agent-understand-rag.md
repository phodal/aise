# 编码智能体：理解 RAG 的应用

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

#### TreeSitter 语法树

结合后续更新：《[Improving LlamaIndex’s Code Chunker by Cleaning Tree-Sitter CSTs](https://docs.sweep.dev/blogs/chunking-improvements)》

1. **Span 数据结构**：引入用于高效表示字符串片段的 Span 数据结构，有助于管理和连接代码块。
2. **处理语法树中的间隙**：通过调整语法树节点的结束字节，使其与下一个节点的开始字节匹配，从而解决语法树中节点之间的间隙问题，提高了代码块的准确性。
3. **改进的代码块化算法**：使用 Span 改进了代码块化算法，使代码更清晰，更好地处理代码块的大小，确保代码块大小合适并能正确连接。
4. **转向基于行的代码块**：从字节索引转向行号，处理编码问题并消除空代码块，提升了代码块化结果的兼容性和可读性。
5. **应对速率限制**：通过分批处理文件和有选择性地重新索引活跃用户和付费用户的方法，有效管理 Modal 平台的速率限制，优化了代码库更新时的资源使用。

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

## 相关资源

### 相似度

Netflix 相关研究：[Is Cosine-Similarity of Embeddings Really About Similarity?](https://arxiv.org/abs/2403.05440)

>
余弦相似度是两个向量之间夹角的余弦值，等价于它们归一化后的点积。一个常见的应用是通过将余弦相似度应用于学习得到的低维特征嵌入，来量化高维对象之间的语义相似性。在实践中，这种方法有时比未归一化的嵌入向量之间的点积效果更好，但有时也可能更差。为了深入理解这一经验观察，我们研究了基于正则化线性模型导出的嵌入，闭式解法有助于进行分析。我们从理论上推导了余弦相似度如何可能产生任意的、因此无意义的"相似性"。对于某些线性模型而言，这些相似性甚至不是唯一的，而对于其他模型，则受正则化的隐式控制。我们讨论了超出线性模型的影响：在学习深度模型时结合了不同的正则化技术；当对结果嵌入进行余弦相似度计算时，这些技术具有隐含的、非预期的影响，使结果变得难以理解且可能是任意的。基于这些见解，我们警告不要盲目使用余弦相似度，并概述了一些替代方法。

## 业内案例

- Codium: [RAG for a Codebase with 10k Repos](https://www.codium.ai/blog/rag-for-large-scale-code-repos/)
- Sweep AI: [Chunking 2M+ files a day for Code Search using Syntax Trees](https://docs.sweep.dev/blogs/chunking-2m-files)
