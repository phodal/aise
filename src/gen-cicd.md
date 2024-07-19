# CI/CD 流水线生成

## 示例

### Gitlab Build 修复
      
[Developing GitLab Duo: Blending AI and Root Cause Analysis to fix CI/CD pipelines](https://about.gitlab.com/blog/2024/06/06/developing-gitlab-duo-blending-ai-and-root-cause-analysis-to-fix-ci-cd/)

示例场景：

- Analyze a Python dependency error
- Analyze missing Go runtime

Scene:

- When you are running into Kubernetes deployment errors or timeouts.
- With OpenTofu or Terraform IaC pipelines failing to provision your cloud resources.
- When the Ansible playbook fails with a cryptic permission error in CI/CD.
- When the Java stack trace is 10 pages long.
- With a shell script highlighting an execution error.
- When a Perl script fails in a single line, which is the only line in the script.
- When the CI/CD job times out and it is unclear which section would cause this.
- When a network connection timeout is reached, and you think it cannot be DNS.


### Google Build 修复

[Safely repairing broken builds with ML](https://research.google/blog/safely-repairing-broken-builds-with-ml/)

我们在集成开发环境中展示了修复，并对这一功能进行了控制实验。这个实验显示，在多个生产力衡量指标上都取得了统计上显著的增益，包括代码更改数量增加了 2%。 
这些增益不仅仅是为了它们自身的好处，而且通过自动化消除了开发者的重复劳动，为他们提供更多时间进行创造性问题解决。这通过消除障碍促进了专注，
从而让开发者能够更长时间保持他们的工作流状态。实际上，我们现在观察到，在一个月内遇到构建中断的用户中，约有34%最终采纳了这种由 ML 建议的修复方案。

![Google Buildfix](images/google-build-fix.png)

为了评估通过我们的修复引入不正确甚至危险代码的风险，我们检查了回顾性的安全性和可靠性相关指标，包括：

- 变更列表回滚率：生产中的问题通常通过回滚引入错误的变更列表来解决。
- 新的检测工具失败率：谷歌运行的检测工具可以检测和标记单元测试和模糊测试中的内存损坏或泄漏问题；例如AddressSanitizer、MemorySanitizer和GWP-Asan。

我们在使用构建修复的变更列表和未使用的变更列表之间监测了这些指标，发现没有可检测的差异。

#### 结论

在集成开发环境中显示ML构建修复，并通过自动安全检查和人工审查加以保护，显著提高了开发者的生产力而不影响代码安全性。这支持了我们的直觉，
即在软件开发过程中，即使是在已知问题上使用ML，也能减少繁重工作并使开发者更高效地解决高阶问题。此外，类似的方法可能在整个开发周期中解决其他类型的
错误和工程任务时也同样有效。这些结果表明，ML有潜力有效且安全地提高开发者的生产力、专注度和代码质量。

