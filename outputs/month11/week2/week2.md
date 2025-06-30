# week 2 (20250616 - 20250622)

-   合并上个月提的 v0.2.0 版本重构 PR ([#96](https://github.com/255doesnotexist/lintestor/pull/96))
    -   废弃基于 Shell 脚本的测试执行器、聚合器和报告生成器。
    -   引入基于 Markdown 模板 (`.test.md`) 的测试定义和执行引擎，包含解析器、依赖管理器、变量系统和报告生成器。
    -   重写 CLI 接入，支持模板发现、测试筛选（按单元、标签、目标）和执行控制。
    -   实现连接管理器 (`ConnectionManager`)，支持本地、SSH、串口等执行方式，并引入连接池。
-   增加 MUSL 静态编译支持 ([`c42e31a`](https://github.com/255doesnotexist/lintestor/commit/c42e31a), [`eb55bf1`](https://github.com/255doesnotexist/lintestor/commit/eb55bf1), [`af69fa6`](https://github.com/255doesnotexist/lintestor/commit/af69fa6))
    -   更新 `Dockerfile`，增加 `musl-tools` 和 `musl-dev`，并添加 MUSL 编译目标。
    -   在 Cargo 配置和 CI 工作流中添加静态链接配置。
-   代码清理和缺陷修复
    -   升级到 Rust 2024 Edition 并清理无用依赖 ([`f863086`](https://github.com/255doesnotexist/lintestor/commit/f863086))。
    -   修复因模板文件名相同导致的模板 ID 冲突问题 ([`ba15cad`](https://github.com/255doesnotexist/lintestor/commit/ba15cad))。
    -   修复摘要报告文件名中的错误 ([`66a28aa`](https://github.com/255doesnotexist/lintestor/commit/66a28aa))。
-   重构 CI/CD 流程
    -   将构建环境从 self-hosted runner 迁移到 GitHub-hosted runner ([`cff8967`](https://github.com/255doesnotexist/lintestor/commit/cff8967))。
    -   将发布流程（crates.io 和 Release）改为手动触发 ([`b280b7c`](https://github.com/255doesnotexist/lintestor/commit/b280b7c), [`a7ac8f2`](https://github.com/255doesnotexist/lintestor/commit/a7ac8f2))。
    -   新增 `pre-commit` 钩子，用于自动格式化 Rust 代码 ([`4b7d54b`](https://github.com/255doesnotexist/lintestor/commit/4b7d54b))。
-   更新项目文档
    -   更新 `README.md` 和 `USAGE.md` 以匹配 v0.2.0 架构和用法 ([`98b2b0c`](https://github.com/255doesnotexist/lintestor/commit/98b2b0c))。