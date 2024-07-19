# AI 辅助平台工程

## 案例

### Neon 文档问答

[Mistral 7B and BAAI on Workers AI vs. OpenAI Models for RAG](https://neon.tech/blog/mistral-7b-and-baai-on-workers-ai-vs-openai-models-for-rag)

- Embedding 模型：[BAAI/bge-base-en-v1.5](https://huggingface.co/BAAI/bge-base-en-v1.5)
- Chat 模型：[mistralai/Mistral-7B-Instruct-v0.1](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)
- 环境：[Cloudflare Workers AI](https://developers.cloudflare.com/workers-ai/)

RAG 过程：

1. **生成 Embedding**：
    - **目的**：使用 Embedding 模型将用户的查询转换为查询向量。
    - **功能**：Embedding 模型将文本翻译成数值格式，系统可以利用该格式来查找相关信息。
2. **上下文检索**：
    - **目的**：使用相似性搜索从文档或数据库中查找相关信息。
    - **功能**：系统通过外部来源进行搜索，以找到与查询向量高度匹配的数据。
3. **完成（或文本生成）**：
    - **目的**：使用用户查询和检索到的上下文生成回答。
    - **功能**：生成模型利用查询和额外的上下文来形成详细且准确的回答。

上下文生成质量：

- bge-base-en-v1.5和text-embedding-ada-002模型生成的上下文在一定程度上相似，特别是在小规模文本块（k=3）时相似度更高。
- 随着文本块数量增加，相似度下降。

生成文本质量：

- gpt-3.5-turbo在文本生成质量上的评分显著高于mistral-7b-instruct-v0.1。
- 尽管上下文相似，生成文本会因模型的随机性设置而有所不同。

评价方式：

- 上下文质量主要通过相似度分析进行评估。
- 文本生成质量通过主观调查进行评估，反映了用户实际体验。


