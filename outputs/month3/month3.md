# month 3

记录本月产出。

## 测试用例 / testcases

1. lintestor 项目
   - CI/CD 系统改进:
     - [实现版本变更时的自动发布流程](https://github.com/255doesnotexist/lintestor/commit/d9ced98)
     - [修复交叉编译错误，移除 powerpc64 架构](https://github.com/255doesnotexist/lintestor/commit/35dfba4)
     - [修复 release workflow，更新 action](https://github.com/255doesnotexist/lintestor/commit/36aaf0a)
     - [实现 nightly build，添加日期到二进制文件名](https://github.com/255doesnotexist/lintestor/commit/ea48aca)
     - [将 CI 流程迁移到自托管的 runner](https://github.com/255doesnotexist/lintestor/commit/50bd2f9)
     - [替换原始 release API 为 action-gh-release](https://github.com/255doesnotexist/lintestor/commit/14c1658)
     - [为不同架构的二进制文件设置不同名称](https://github.com/255doesnotexist/lintestor/commit/8c43420)
     - [从 crates.io 安装 lintestor](https://github.com/255doesnotexist/lintestor/commit/7860d65)
     - [在工作流中直接添加 clippy 组件](https://github.com/255doesnotexist/lintestor/commit/f67a405)
   
   - 配置和功能改进:
     - [进一步修复 connection_config 相关问题](https://github.com/255doesnotexist/lintestor/commit/61906c0)
     - [修复 ConnectionConfig 在解析时非可选的问题](https://github.com/255doesnotexist/lintestor/commit/859ac02)
     - [添加 LICENSE, 项目描述和仓库信息](https://github.com/255doesnotexist/lintestor/commit/add1881)
   
   - 代码重构和组织:
     - [将配置和测试移动到 dirty 分支](https://github.com/255doesnotexist/lintestor/commit/0d58d0d)
     - [53c93e7][4f18892] 添加更多注释说明
     - [应用自动格式化](https://github.com/255doesnotexist/lintestor/commit/19b3045)

   - 测试系统改进:
     - [为单元测试添加 CI workflow](https://github.com/255doesnotexist/lintestor/commit/b76c25c)
     - [实现测试报告的自动提交](https://github.com/255doesnotexist/lintestor/commit/6df46d3)
     - [合并 PR #30，优化 make 命令](https://github.com/255doesnotexist/lintestor/commit/63188e9)

2. boardtest 项目重要更新
   - 服务端功能实现:
     - [添加 /start_test 接口支持远程调用](https://github.com/255doesnotexist/boardtest/commit/20c71a0)
     - [实现基于 token 的身份验证机制](https://github.com/255doesnotexist/boardtest/commit/2f6c9eb)
     - [优化数据传输，实现逐字符推送](https://github.com/255doesnotexist/boardtest/commit/7017363)
     - [添加测试模式下的 prompt always yes 参数](https://github.com/255doesnotexist/boardtest/commit/50a3d85)
   
   - 系统测试:
     - [完成 Bianbu v2.0 在 BPI-F3 开发板上的系统测试](https://github.com/255doesnotexist/boardtest/commit/bb17fe4)
     - [测试报告合并入主分支](https://github.com/ruyisdk/support-matrix/commit/3630bd6)

3. 交叉编译环境改进
   - 创建了 Rust for rv64gc 交叉编译用 Docker 镜像
   - [发布到 Docker Hub](https://hub.docker.com/r/255doesnotexist/lintestor-cross-compile)
   - [Dockerfile 源码](https://github.com/255doesnotexist/lintestor/blob/main/Dockerfile)
   - 解决了 cross-rs 内建 gcc 工具链版本过旧导致无法编译 openssl 的问题

## 一点什么

1. lintestor 自动化体系显著增强:
   - 完成了 nightly build 系统
   - 实现了测试报告自动提交
   - 重构了 CI 隔离待测试的文件与代码

2. boardtest 抓回来改了:
   - 实现了远程测试接口
   - 建立了安全的远程调用机制
   - 完成了实时数据推送功能
   - 利用 boardtest 验证了 Bianbu v2.0 系统测试

3. 工具链改进:
   - 解决了 RISC-V 交叉编译环境问题
   - 建立了可复用的交叉编译用 Docker 镜像

## 未来计划

1. lintestor 进一步改进:
   - dirty 分支中加入 fedora 测试脚本
   - 适配接入 boardtest 系统
   - 配置 fedora riscv on qemu 测试环境

2. boardtest 功能扩展:
   - 研究米家 SDK 自动上下电控制
   - 完善远程测试接口

3. 测试覆盖扩展:
   - 扩大测试发行版范围
   - 增加自动化测试场景
