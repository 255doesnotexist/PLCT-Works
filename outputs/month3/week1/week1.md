## week 1 (1007 - 1013)

### lintestor 主仓库部分：

1. CI/CD 改进
   - [ci(publish): add auto-publish](https://github.com/255doesnotexist/lintestor/commit/d9ced98)
     - 实现自动发布：版本变更时触发自动发布流程
   - [ci(release): fix action Cross Compilation error no 29](https://github.com/255doesnotexist/lintestor/commit/35dfba4)
     - 修复交叉编译错误：移除 `powerpc64` 架构
   - [ci(release): fix release workflow #28 & pull only](https://github.com/255doesnotexist/lintestor/commit/36aaf0a)
     - 修复 release workflow，移除 docker 构建过程，更新 action
   - [ci(fix): try to fix cross compilation workflow](https://github.com/255doesnotexist/lintestor/commit/820c5c7)
     - 尝试修复交叉编译 workflow，使用自定义 Dockerfile
   - [ci(release): give each architecture binaries different names](https://github.com/255doesnotexist/lintestor/commit/8c43420)
     - 为不同架构的二进制文件赋予不同的名称
   - [ci(all): move to self-hosted runners](https://github.com/255doesnotexist/lintestor/commit/50bd2f9)
     - 将 CI 流程迁移到自托管的 runner 上
   - [ci(release): make it nightly](https://github.com/255doesnotexist/lintestor/commit/ea48aca)
     - 实现 nightly build，并添加日期到二进制文件名中
   - [ci(release): use ubuntu-lastest](https://github.com/255doesnotexist/lintestor/commit/16bf14a)
     - 使用 ubuntu-latest 以避免 docker in docker 问题
   - [ci(release): replace raw release api to action-gh-release](https://github.com/255doesnotexist/lintestor/commit/14c1658)
     - 替换原始的 release API 为 action-gh-release，以解决之前发布工作流的随机崩溃问题
   - [ci(release): listing artifacts & targets](https://github.com/255doesnotexist/lintestor/commit/86724b6)
     - 列出构建产物和目标
   - [ci(release): fix artifacts uploading name...](https://github.com/255doesnotexist/lintestor/commit/333c6a7)
     - 修复构建产物上传的命名问题
   - [ci(test): fetch config from dirty branch & download release binary](https://github.com/255doesnotexist/lintestor/commit/f0ebf48)
     - 从 dirty 分支获取配置并下载发布二进制文件
   - [ci(test): recursively find release binary](https://github.com/255doesnotexist/lintestor/commit/d227c02)
     - 递归查找发布二进制文件
   - [ci(test): install lintestor from crates.io](https://github.com/255doesnotexist/lintestor/commit/7860d65)
     - 从 crates.io 安装 lintestor

2. 元数据更新
   - [metadata: add lincense, description, repository](https://github.com/255doesnotexist/lintestor/commit/add1881)
     - 添加 LICENSE 文件，项目描述和仓库信息

3. 文档改进
   - [docs(readme): update summary url](https://github.com/255doesnotexist/lintestor/commit/18c9daa)
     - 更新 README 中的摘要 URL
   - [53c93e7] [4f18892] 
     - 添加更多注释

4. 代码风格
   - [style: apply automatic formatting](https://github.com/255doesnotexist/lintestor/commit/19b3045)
     - 应用自动格式化

5. 交叉编译 Docker 镜像
   - 创建了可能可复用的 Rust for rv64gc(etc.) 交叉编译用 Docker 镜像
   - [Docker Hub 链接](https://hub.docker.com/r/255doesnotexist/lintestor-cross-compile)
   - [Dockerfile 链接](https://github.com/255doesnotexist/lintestor/blob/main/Dockerfile)
   - 主要解决了 cross-rs 内建的 gcc 工具链版本过旧无法编译 openssl 的问题

6. 代码重构和组织
   - [refactor: move all configurations & tests to dirty branch](https://github.com/255doesnotexist/lintestor/commit/0d58d0d)
     - 将所有配置和测试移动到 dirty 分支

7. 其他改进
   - [ci(clippy): add clippy component directly in workflow](https://github.com/255doesnotexist/lintestor/commit/f67a405)
     - 在工作流中直接添加 clippy，以修复自托管 Debian 上的 action 错误
     - 原本在 ubuntu-latest 下的 rust-minimal 环境就有 clippy，但 Debian runner 上需要显式指定

8. 发布管理
   - 添加了 `release-2024-10-13` 和 `release-2024-10-14` 标签
   - 在这两天进行了成功的自动发版