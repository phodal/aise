#  AI 辅助软件工程：AI 辅助流水线

## 问题修复

[Safely repairing broken builds with ML](https://research.google/blog/safely-repairing-broken-builds-with-ml/)


## 示例

### prompt 示例：AutoDev

GitHub Action 生成

```Velocity
Create build.yml YAML file for GitHub Action for build project and runs tests

- ${context.buildContext}
- OS: latest ubuntu version
```

Dockerfile 示例：

```Velocity
Please write a Dockerfile with minimal steps.

${context.buildContext}
- I need the building to be done in separate base image than running the build
- I need the application port to be 3000

Output only the Dockerfile content without any explanation.
```

