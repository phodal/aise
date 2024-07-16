# 系统迁移

### 遗留基础设施改造

许多组织面临维护关键遗留Java应用程序的挑战，这些应用程序由于框架过时、代码无文档和安全漏洞而变得难以维护。现代化这些应用程序是必要且具有挑战性的任务。Amazon
Q Developer简化并加速了这一过程。

**使用Amazon Q Developer的现代化过程**

1. **升级Java版本：**
    - 从Java 8升级到Java 17，以提高性能、安全性并利用新功能。
    - Amazon Q Developer代码转换代理通过分析代码、生成转换计划并更新框架和库以兼容Java 17来自动化这一过程。

2. **减少技术债务：**
    - 识别并解决代码库中的技术债务，以提高代码质量和可维护性。
    - 使用Amazon Q Developer生成技术债务问题列表并提出改进建议。
    - 实施建议，如改进日志记录和模块化，以减少技术债务。

3. **云原生部署：**
    - 将应用程序迁移到云原生架构并部署到AWS。
    - 步骤包括将应用程序容器化，使用Amazon Elastic Container Registry（ECR），在AWS Fargate上部署到Amazon Elastic Container
      Service（ECS），并设置Amazon CloudWatch进行监控。
    - Amazon Q Developer帮助生成用于容器化的Dockerfile和用于基础设施部署的CloudFormation模板。

