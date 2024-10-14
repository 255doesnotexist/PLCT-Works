## week 1 (1007 - 1013)
### lintestor 主仓库部分：

1. **CI/CD 改进**:  主要集中在发布流程的自动化和修复交叉编译问题。
    - [d9ced98] `ci(publish): add auto-publish`
      -  实现自动发布：版本变更时触发自动发布流程。
    - [35dfba4] `ci(release): fix action Cross Compilation error no 29`
      - 修复交叉编译错误：移除 `powerpc64` 架构。
    - [36aaf0a] `ci(release): fix release workflow #28 & pull only`
      -  修复 release workflow，移除 docker 构建过程，更新 action。
    - [820c5c7] `ci(fix): try to fix cross compilation workflow`
      - 尝试修复交叉编译 workflow，使用自定义 Dockerfile。
    - [8c43420] `ci(release): give each architecture binaries different names`
      -  为不同架构的二进制文件赋予不同的名称。
    - [50bd2f9] `ci(all): move to self-hosted runners`
      - 将 CI 流程迁移到自托管的 runner 上。
    - [ea48aca] `ci(release): make it nightly`
      - 实现 nightly build，并添加日期到二进制文件名中。
    - [16bf14a] `ci(release): use ubuntu-lastest`
      - 使用 ubuntu-latest 以避免 docker in docker 问题。
    - [14c1658] `ci(release): replace raw release api to action-gh-release`
      - 替换原始的 release API 为 action-gh-release，以解决之前发布工作流的随机崩溃问题。
    - [86724b6] `ci(release): listing artifacts & targets`
      - 列出构建产物和目标。
    - [333c6a7] `ci(release): fix artifacts uploading name...`
      - 修复构建产物上传的命名问题。
    - [f0ebf48] `ci(test): fetch config from dirty branch & download release binary`
      - 从 dirty 分支获取配置并下载发布二进制文件。
    - [d227c02] `ci(test): recursively find release binary`
      - 递归查找发布二进制文件。
    - [7860d65] `ci(test): install lintestor from crates.io`
      - 从 crates.io 安装 lintestor。

2. **元数据更新**: 添加了许可证、描述和仓库信息。
    - [add1881] `metadata: add lincense, description, repository`
      - 添加 LICENSE 文件，项目描述和仓库信息。

3. **文档改进**:  添加了更多注释和更新了 README。
    - [53c93e7] [4f18892] - 都是添加更多注释。
    - [18c9daa] `docs(readme): update summary url`
      - 更新 README 中的摘要 URL。

4. **代码风格**: 应用了自动格式化。
    - [19b3045] `style: apply automatic formatting`
      - 应用自动格式化。

5. **可能可复用的 Rust for rv64gc(etc.) 交叉编译用 Docker 镜像**
   - [docker hub](https://hub.docker.com/r/255doesnotexist/lintestor-cross-compile)
   - [docker file](https://github.com/255doesnotexist/lintestor/blob/main/Dockerfile)
   - 主要解决的是 cross-rs 内建的 gcc 工具链版本实在太老无法编译 openssl 的问题。

6. **代码重构和组织**:
    - [0d58d0d] `refactor: move all configurations & tests to dirty branch`
      - 将所有配置和测试移动到 dirty 分支。

7. **其他改进**:
    - [f67a405] `ci(clippy): add clippy component directly in workflow`
      - 在工作流中直接添加 clippy，以修复自托管 Debian 上的 action 错误。
      - 原本在 ubuntu-latest 下的 rust-minimal 环境就有 clippy 不知道为什么 Debian runner 上就需要显式指定

8. **发布管理**:
    - 添加了 `release-2024-10-13` 和 `release-2024-10-14` 标签，在这两天进行了成功的自动发版。
