# 编码智能体基础设施

## 向量数据存储

### 示例：JetBrains + Local Storage



### 示例：Sweep + Redis

[Our simple vector database implementation](https://docs.sweep.dev/blogs/vector-db-implementation)

优势：

- 管理多个索引的复杂性：
    - 标准的向量数据库在处理单个索引时表现良好，但在管理多个索引、频繁更新和自托管时变得复杂。
    - 使用 Redis 可以简化这一过程，无需管理多个索引和重建索引的问题。
- 基础设施和依赖管理：
    - 使用外部存储（如 Pinecone）会引入额外的依赖和潜在的故障点。
    - Redis 是一个流行的开源内存数据库，可以轻松自托管，减少了对外部服务的依赖。
- 缓存机制：
    - Redis 非常适合缓存用途，可以快速读取和写入数据，这对于频繁访问的 Embedding 向量非常重要。
    - 通过使用 Redis，系统可以缓存 Embedding 结果，减少对 OpenAI API 的调用次数，降低成本和延迟。

缺点：

- 该方法速度较慢（每个查询大约1秒），但满足他们的需求。
- 系统在超过 100 万个嵌入向量时扩展性不佳，但符合他们当前的需求（通常每个代码库文件少于30k）。
