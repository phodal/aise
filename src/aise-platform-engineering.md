# AI 辅助平台工程

## 案例

### 项目协作工具：GenPen.AI

https://genpen.ai/

GenPen.AI 是一个项目协作与代码生成工具。它可以将设计提示转化为REST
API，并自动生成文档。核心功能包括：代码生成、基于AI的多模式VLLM转换器、OpenAPI集成、自动化Git、代码和文档管理、多个AI代理用于响应汇总。它的目标是加快调试速度，减少开发时间，并简化项目管理。GenPen
AI自动化重复任务，利用AI转换器，并根据模型生成代码，从而减少开发时间。
图片

### AI工作流程编排：LangBase

LangBase 为用户提供了一站式的 AI 应用管理和运维服务，降低用户创建 AI 应用的成本。因此 LangBase
不仅在底层提供提供了模型和应用的管理，也在应用平台之上多提供了一层业务接入层，最大化的降低用户创建和使用 AI 应用的成本。

### Neon 文档问答

[Mistral 7B and BAAI on Workers AI vs. OpenAI Models for RAG](https://neon.tech/blog/mistral-7b-and-baai-on-workers-ai-vs-openai-models-for-rag)

- Embedding 模型：[BAAI/bge-base-en-v1.5](https://huggingface.co/BAAI/bge-base-en-v1.5)
- Chat 模型：[mistralai/Mistral-7B-Instruct-v0.1](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1)
- 环境：[Cloudflare Workers AI](https://developers.cloudflare.com/workers-ai/)

#### RAG 过程

**生成 Embedding**：

- **目的**：通过 Embedding 模型，将用户的查询转换成查询向量。
- **功能**：Embedding 模型将文本转化为数值形式，便于系统据此搜寻相关信息。

**上下文检索**：

- **目的**：利用相似性搜索技术，在文档或数据库中寻找与查询相关的信息。
- **功能**：系统会从外部资源中搜索，寻找与查询向量高度一致的数据。

**完成（或文本生成）**：

- **目的**：结合用户查询和检索到的上下文信息，生成回答。
- **功能**：生成模型运用查询及附加上下文，形成既详尽又准确的回答。

#### 对比与总结

上下文生成质量：

- `bge-base-en-v1.5` 和 `text-embedding-ada-002` 模型生成的上下文在一定程度上相似，特别是在小规模文本块（k=3）时相似度更高。
- 随着文本块数量增加，相似度下降。

生成文本质量：

- `gpt-3.5-turbo` 在文本生成质量上的评分显著高于 `mistral-7b-instruct-v0.1`。
- 尽管上下文相似，生成文本会因模型的随机性设置而有所不同。

评价方式：

- 上下文质量主要通过相似度分析进行评估。
- 文本生成质量通过主观调查进行评估，反映了用户实际体验。


