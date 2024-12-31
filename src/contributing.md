# 贡献指南
确保你为项目做贡献时 git 分支管理清晰且规范：

1. **Fork 项目**：
   - 首先，打开 [https://github.com/phodal/aise.git](https://github.com/phodal/aise.git)，点击右侧的 "Fork" 按钮，将该项目 fork 到你的 Github 账户下。

2. **克隆项目到本地**：
   - 使用 `git clone` 命令将你 fork 的项目克隆到你的本地机器上。
     ```bash
       git clone https://github.com/你的账户名/aise.git # 克隆项目
       cd aise # 进入项目根目录
    ```

3. **添加上游远程仓库**：
   - 为了保持与原项目的同步，你需要添加原项目（上游仓库）的远程地址。
     ```sh
        # 添加上游仓库
        git remote add upstream https://github.com/原项目作者的用户名/aise.git
     ```

4. **创建新的分支进行开发**：
   - 切换到开发分支（通常是 `master`），并拉取最新的代码。
     ```sh
        git checkout master
        git pull upstream master # 拉取上游仓库的更新
     ```
   - 创建一个新的分支来进行你的修改，分支名最好具有描述性。
     ```sh
        git checkout -b feature/<功能描述>
     ```

5. **进行修改并提交**：
   - 在你的新分支上进行修改和开发。
   - 使用 `git add` 和 `git commit` 命令提交你的修改。
     ```sh
     git add .
     git commit -m "添加新功能描述"
     ```

6. **推送到你的远程仓库**：
   - 将你的分支先推送到你自己的 Github 仓库。
     ```sh
     git push origin feature/<功能描述>
     ```

7. **创建 Pull Request (PR)**：
   - 在 Github 上，导航到你的仓库，你会看到一个 "Pull request" 的按钮，点击它。
   - 确保分支对应正确：`左侧 base:master，右侧 compare:feature/<功能描述>`
   - 填写 PR 的描述和标题，确保描述清楚你做了哪些修改以及为什么这样做。
   - 提交 PR。

8. **等待反馈和合并**：
   - 项目维护者可能会对你的 PR 进行代码审查，并提出修改建议。
   - 根据反馈，在本地继续修改并提交到你的分支。
   - 确保你的分支与主分支保持同步，以减少合并冲突的可能性。
     ```sh
     git checkout master
     git pull upstream master
     git checkout feature/<功能描述>
     git merge master
     git push origin feature/<功能描述>
     ```

9. **合并**：
   - 一旦你的 PR 被接受，项目维护者会将它合并到主分支中。

   - 确保分支已经安全合并
   - 在您 fork 的源码上删除已完成的功能分支（目的是防止分支泛滥）
   ```bash
    # 删除本地分支
    git branch -D feature/<功能描述>

    # 删除远程分支
    git push origin --delete feature/<功能描述>

    # 拉取上游仓库的更新
    git pull upstream master
```

希望这些信息对你有帮助！