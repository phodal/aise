# 编码智能体分析：Copilot Workspace

## 示例

### Copilot Workspace 提示词示例：

对应的 Workspace 构建过程如下：

```markdown
1. Deciding which workspace information to collect
2. Determining workspace structure…
3. Asking the model to update the user question and provide queries…
     - keywords
     - workspaceChunkIndex
4. Running all tools…
    - xxxx
5. Collecting workspace information
```

模型策略：

```markdown
2024-04-15 11:46:05.940 [info] [chat fetch] url https://api.githubcopilot.com/chat/completions
2024-04-15 11:46:05.940 [info] [chat fetch] modelMaxPromptTokens 3072
2024-04-15 11:46:05.940 [info] [chat fetch] modelMaxResponseTokens 4096
2024-04-15 11:46:05.940 [info] [chat fetch] chat model gpt-4
2024-04-15 11:46:07.735 [info] [chat fetch] request.response: [https://api.githubcopilot.com/chat/completions], took 1795 ms
2024-04-15 11:46:19.135 [info] [streamMessages] message 0 returned. finish reason: [stop]
2024-04-15 11:46:19.136 [info] [streamChoices] request done: requestId: [xxx] responseId: xxx] model deployment ID: []
2024-04-15 11:46:19.153 [info] [chat fetch] url https://api.githubcopilot.com/chat/completions
2024-04-15 11:46:19.153 [info] [chat fetch] modelMaxPromptTokens 7168
2024-04-15 11:46:19.153 [info] [chat fetch] modelMaxResponseTokens 4096
2024-04-15 11:46:19.153 [info] [chat fetch] chat model gpt-3.5-turbo
2024-04-15 11:46:19.785 [info] [chat fetch] request.response: [https://api.githubcopilot.com/chat/completions], took 631 ms
2024-04-15 11:46:19.785 [info] [streamMessages] message 0 returned. finish reason: [stop]
2024-04-15 11:46:19.786 [info] [streamChoices] request done: requestId: [xxx] responseId: [xxx] model deployment ID: [x4dff5e5d11fc]
```

#### 理解阶段提示词

```markdown
You are a coding assistant who helps the user answer questions about code in their workspace by providing a list of relevant keywords they can search for to answer the question.
The user will provide you with potentially relevant information from the workspace. This information may be incomplete.

DO NOT ask the user for additional information or clarification.
DO NOT try to answer the user's question directly.

**Additional Rules**
Think step by step:
1. Read the user's question to understand what they are asking about their workspace.
2. If the question contains pronouns such as 'it' or 'that', try to understand what the pronoun refers to by looking at the rest of the question and the conversation history.
3. If the question contains an ambiguous word such as 'this', try to understand what it refers to by looking at the rest of the question, the user's active selection, and the conversation history.
4. Output a precise version of the question that resolves all pronouns and ambiguous words like 'this' to the specific nouns they stand for. Be sure to preserve the exact meaning of the question by only changing ambiguous pronouns and words like 'this'.
5. Then output a short markdown list of up to 8 relevant keywords that the user could try searching for to answer their question. These keywords could be used as file names, symbol names, abbreviations, or comments in the relevant code. Put the most relevant keywords to the question first. Do not include overly generic keywords. Do not repeat keywords.
6. For each keyword in the markdown list of related keywords, if applicable add a comma-separated list of variations after it. For example, for 'encode', possible variations include 'encoding', 'encoded', 'encoder', 'encoders'. Consider synonyms and plural forms. Do not repeat variations.

**Examples**
User: Where's the code for base64 encoding?

Response:
Where's the code for base64 encoding?

- base64 encoding, base64 encoder, base64 encode
- base64, base 64
- encode, encoded, encoder, encoders
```


### 使用Copilot Workspace的实现步骤

[Copilot Workspace: What It Is, How It Works, Why It Matters](https://zilliz.com/blog/what-is-copilot-workspace-and-why-it-matters)

以下是如何利用 Copilot Workspace 来实现该功能的方法：

1. **任务创建**：首先创建一个GitHub issue，任务是将应用程序改为多语言版本。具体任务是将(BGE-M3)多语言模型集成到现有的RAG系统中。
2. **规范**：Copilot Workspace分析任务并生成高级规范，确定需要更新数据处理管道以处理多种语言，并修改RAG系统以利用BGE-M3提供多语言支持。
3. **规划**：Workspace接着生成详细的计划。包括以下步骤：
    - 更新数据摄取过程以包含多语言数据。
    - 修改现有的Milvus设置以支持BGE-M3。
    - 调整RAG系统以利用BGE-M3的多语言功能。
    - 测试系统以确保其能够支持多种语言。
4. **编码**：基于验证后的计划，Copilot Workspace生成必要的代码：
    - 更新数据摄取脚本以预处理和索引多语言数据到Milvus中。
    - 配置Milvus代码以使用BGE-M3嵌入进行多语言的相似性搜索。
    - 修改RAG系统以使用多语言模型查询Milvus并检索相关结果。
5. **审查和测试**：审查生成的代码，进行必要的调整并测试更改。
6. **拉取请求和合并**：满意后，打开一个拉取请求与团队审查更改。最终验证后，合并更改，使应用程序支持多语言功能。
