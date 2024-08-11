## week 0 (0805 - 0811)

### lintestor 主仓库代码部分：

1. 添加了[本地测试选项](https://github.com/255doesnotexist/lintestor/commit/fac680ab80458e3bffd5a5e09bd5baa2dd5902d8)，现在可以用 --locally 参数指定测试不利用 QEMU，而在本地直接执行。适用于测试机器本身就属于 RISC-V 的情况。
2. 重写了测试调度相关的代码：
   移除了 [scheduler](https://github.com/255doesnotexist/lintestor/commit/840124755c050c7d5ceba1330159aecdd4b9be07) 相关部分。改用 [TestRunner](https://github.com/255doesnotexist/lintestor/commit/fac680ab80458e3bffd5a5e09bd5baa2dd5902d8#diff-236af404cd9308bec00c074ce8b289151f87376a938e17c321603e50ce6aecd7) 执行测试。
   抽象出 [TestRunner trait](https://github.com/255doesnotexist/lintestor/commit/fac680ab80458e3bffd5a5e09bd5baa2dd5902d8#diff-236af404cd9308bec00c074ce8b289151f87376a938e17c321603e50ce6aecd7)，更灵活些。
3. 现在定期测试的 Actions 使用[自托管在 Infra 上的 Action runner](https://github.com/255doesnotexist/lintestor/commit/2c9084d6c1f47fe9201146b46af19c6e8b8faf63)。使用 myoung34/github-runner:latest 的 GitHub Runner docker 镜像，定期在 Infra 上拉取 GitHub Actions 执行。

### 测试脚本部分：

1. 为 Debian 补上新的软件包测试：：

   1. [ZooKeeper](https://github.com/255doesnotexist/lintestor/commit/44e2d6bf3f010ec9f9adca9e89c4b93531a008cd)（分布式协调服务）

   2. [Varnish](https://github.com/255doesnotexist/lintestor/commit/415fceaf5bd9217ec6df66d716cf1026b9c513dc)（HTTP加速器）

   3. [Squid](https://github.com/255doesnotexist/lintestor/commit/eab4663044402aa14660526d7ac421779ea737bf)（代理缓存服务器）

   4. [SQLite](https://github.com/255doesnotexist/lintestor/commit/3d0d643584a645d23b7ce26e89b38b41fddc947f)（轻量级数据库）

   5. [SciPy](https://github.com/255doesnotexist/lintestor/commit/0d9512b05c50dc593314859ec2a006e293e28ea6)（Python科学计算包）

   6. [Rust](https://github.com/255doesnotexist/lintestor/commit/a5b05075387de94534d09170ea162e33c77c511b)（系统编程语言）

   7. [runc](https://github.com/255doesnotexist/lintestor/commit/42c8014b4cd50ad3007c7f15936df96d80db2d09)（容器运行时）

   8. [Ruby](https://github.com/255doesnotexist/lintestor/commit/ffd1c207ba5db641768768664835697b14c805fb)（动态编程语言）

   9. [Redis](https://github.com/255doesnotexist/lintestor/commit/f0fb47429a78129fb10580e6f70f65fe818184a9)（内存数据结构中间件）

   10. [Python](https://github.com/255doesnotexist/lintestor/commit/539d4ee134d35faf07325a3f6f699d83b9121015)（高级编程语言）

   11. [PostgreSQL](https://github.com/255doesnotexist/lintestor/commit/5b74a052c4adfe622fd981bebef2208af9166473)（关系型数据库）

   12. [Perl](https://github.com/255doesnotexist/lintestor/commit/0d6490896b9708967b2c0528cf1e2370051711d4)（通用脚本语言）

   13. [OpenSSL](https://github.com/255doesnotexist/lintestor/commit/9194be9b582f2de2f13d75c6b279f05706a73c3d)（加密库）

   14. [OpenJDK](https://github.com/255doesnotexist/lintestor/commit/ccf9369fa41964efb9c518e4a46e91f7bcda45ef)（Java开发工具包）

2.  针对 Clang、Erlang 依赖安装过程中的问题，需要指定非交互式安装环境变量，避免了安装过程卡住从而导致 runner 超时的情况。

### 未来计划：

1. 在 BPI-F3 上尝试本地部署 riscv github runner 尝试本地测试。
2. 添加 Bianbu 的自动化测试？
3. 支持 VNC 或 KVM 的图形化测试？
4. 也许试着接测试任务？只做 lintestor 有些怪。