# AI4SE 度量

- 更好：开发体验
    - SPACE Framework，如上手时间、构建时间、代码检视时间、开发者心情指数
- 更快：价值交付。
    - 如价值交付周期/反馈周期
    - 如需求/变更Lead time等
- 更好：交付质量
    - 如更高测试覆盖率
    - 更高的稳定性和可用性
    - 更好的代码质量和可维护性等
- 更多：技能成长
    - 如掌握更多的技能如后端掌握前端开发，Dev掌握Ops等
    - 如更低的团队经验水平，1个TL能更多Junior团队成员等

## 金融行业案例：Ebay

链接：![Cutting Through the Noise: Three Things We've Learned About Generative AI and Developer Productivity](https://innovation.ebayinc.com/tech/features/cutting-through-the-noise-three-things-weve-learned-about-generative-ai-and-developer-productivity/)

### 目标

提升开发者生产力，提高软件开发效率和质量。

### 投资

1. 商业产品投资：扩展使用GitHub Copilot。
2. 微调和后训练LLM：开发eBayCoder，基于Code Llama 13B进行微调。
3. 内部知识库：创建内部GPT，整合企业内部文档和数据源。

### 举措

1. **利用商业产品（GitHub Copilot）**

- **A/B测试**：
    - **测试组和对照组**：300名开发者分为两组，一组使用Copilot，另一组不使用。
    - **结果**：
        - 代码接受率提高27%。
        - 生成文档准确率70%，代码准确率60%。
        - Pull Request（PR）创建到合并时间减少17%。
        - 变更Lead Time减少12%。
        - 代码质量保持不变。
    - **优势**：自动生成代码、生成测试、自动填充重复代码。
    - **劣势**：提示大小有限，处理大量代码时存在困难。

2. **微调和后训练的LLM（eBayCoder）**

- **模型选择和微调**：
    - 使用Code Llama 13B作为基础模型，结合eBay代码库和文档进行微调。
- **效果**：
    - 简化软件维护工作，如升级内部基础库和框架。
    - 减少代码重复，提供更多上下文。
    - **优势**：处理更多内部数据，减少代码重复。
    - **劣势**：需要大量内部数据进行微调。

3. **内部知识库（内部GPT）**

- **系统架构**：
    - 使用检索增强生成（RAG）系统创建嵌入向量，并存储在向量数据库中。
    - 用户查询时，系统生成查询向量并与已知内容向量进行比较，找到最相关的内容和链接。
    - 使用LLM实例回答问题，若无法回答则返回“不知道”。
- **效果**：
    - 提高任务完成速度。
    - 减少支持和会议请求。
    - **优势**：提供高效和相关的答案，减少搜索时间。
    - **劣势**：偶尔会生成无意义的答案，需要通过用户反馈（RLHF）不断改进。
