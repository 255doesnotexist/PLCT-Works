# month 1

记录本月产出。

## 测试用例 / testcases

1. lintestor 项目
   - 重写了测试调度相关的代码：
     - [移除了 scheduler 相关部分](https://github.com/255doesnotexist/lintestor/commit/840124755c050c7d5ceba1330159aecdd4b9be07)
     - [抽象出 TestRunner trait，实现 RemoteTestRunner 和 LocalTestRunner](https://github.com/255doesnotexist/lintestor/commit/fac680ab80458e3bffd5a5e09bd5baa2dd5902d8#diff-236af404cd9308bec00c074ce8b289151f87376a938e17c321603e50ce6aecd7)
   - [添加了全局前置环境配置](https://github.com/255doesnotexist/lintestor/commit/6531a6b8855ce6b6a0f3b263b32f55d75defe8e7)，可预先配置测试所需环境变量和安装包
   - 改进了测试结果报告：
     - [修改 report.json 格式，包含测试脚本输出结果](https://github.com/255doesnotexist/lintestor/commit/b333650929085144d1bec4ef889cd7479a48b7c6)
     - [支持单软件包多个测试脚本](https://github.com/255doesnotexist/lintestor/commit/5ed367e2267ff31b2001653406cae925e72f9bbd)
     - [添加 TestScriptManager 管理不同发行版不同包的测试脚本列表](https://github.com/255doesnotexist/lintestor/commit/1abb22247542dc6dbde9350d2a2cdfc03c9d4fb4)
   - 优化了测试环境管理：
     - [修复 TestEnvManager 可能无视本地测试参数的问题](https://github.com/255doesnotexist/lintestor/commit/25cb8a80fed9685d85e7c828cfeadc603b0972be)
   - 改进了测试配置：
     - [弃用 `--locally` 选项](https://github.com/255doesnotexist/lintestor/commit/ba42ba99a9cb243c402cee01553268d7bce190e5)
     - [新增发行版测试配置类型: 'locally'、'remote'、'qemu-based-remote'](https://github.com/255doesnotexist/lintestor/commit/bb284190794def8fc6879a61a485ab2c449e7da6)
   - [合并了第一位贡献者 aisuneko 的 Pull Request](https://github.com/255doesnotexist/lintestor/commit/1fac3229bc61e28a3bf05840e8e51bb44b1920e2)
   - [实现了 RemoteTestRunner 的 verbose 功能](https://github.com/255doesnotexist/lintestor/commit/903574609d3c8672dfe76827ca6232d624dbca1f)
   [lintestor 项目](https://github.com/255doesnotexist/lintestor/)

2. Debian 软件包测试扩展
   - 为 Debian 新增了多个软件包测试，包括：
     [ZooKeeper](https://github.com/255doesnotexist/lintestor/commit/44e2d6bf3f010ec9f9adca9e89c4b93531a008cd), [Varnish](https://github.com/255doesnotexist/lintestor/commit/415fceaf5bd9217ec6df66d716cf1026b9c513dc), [Squid](https://github.com/255doesnotexist/lintestor/commit/eab4663044402aa14660526d7ac421779ea737bf), [SQLite](https://github.com/255doesnotexist/lintestor/commit/3d0d643584a645d23b7ce26e89b38b41fddc947f), [SciPy](https://github.com/255doesnotexist/lintestor/commit/0d9512b05c50dc593314859ec2a006e293e28ea6), [Rust](https://github.com/255doesnotexist/lintestor/commit/a5b05075387de94534d09170ea162e33c77c511b), [runc](https://github.com/255doesnotexist/lintestor/commit/42c8014b4cd50ad3007c7f15936df96d80db2d09), [Ruby](https://github.com/255doesnotexist/lintestor/commit/ffd1c207ba5db641768768664835697b14c805fb), [Redis](https://github.com/255doesnotexist/lintestor/commit/f0fb47429a78129fb10580e6f70f65fe818184a9), [Python](https://github.com/255doesnotexist/lintestor/commit/539d4ee134d35faf07325a3f6f699d83b9121015), [PostgreSQL](https://github.com/255doesnotexist/lintestor/commit/5b74a052c4adfe622fd981bebef2208af9166473), [Perl](https://github.com/255doesnotexist/lintestor/commit/0d6490896b9708967b2c0528cf1e2370051711d4), [OpenSSL](https://github.com/255doesnotexist/lintestor/commit/9194be9b582f2de2f13d75c6b279f05706a73c3d), [OpenJDK](https://github.com/255doesnotexist/lintestor/commit/ccf9369fa41964efb9c518e4a46e91f7bcda45ef) 等
   - [修复了 numpy 包测试前不检查自身是否已安装的问题](https://github.com/255doesnotexist/lintestor/commit/1326c5b7d1e8f751ae1929f2285575a66be3aa68)
   - [针对 OpenJDK 高版本不支持 sv48 以上的 paging modes 的问题，在 cmdline 加入 no4lvl 并降级 OpenJDK 版本至 11](https://github.com/255doesnotexist/lintestor/commit/177a8f25797bc59cf332c99bd045bd43c4b37fec)
   - [为 Debian 的全局依赖脚本中加入 Rust 等包的测试安装所依赖的 sudo、curl 等包](https://github.com/255doesnotexist/lintestor/commit/d190d48a51b7c9c4ba59013904861a7d3b6775f7)

3. CI/CD 改进
   - [使用自托管在 Infra 上的 Action runner 进行定期测试](https://github.com/255doesnotexist/lintestor/commit/2c9084d6c1f47fe9201146b46af19c6e8b8faf63)
   - 尝试在 BPI-F3 (Bianbu Linux) 上部署 Action Runner（遇到[一些问题](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month1/week2/week2.md#%E5%85%B6%E4%BB%96)，待解决）

## 文档内容

1. [PLCT 开放日 Marp 幻灯片](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month1/week1/marp.pdf)

## 其他内容

1. 尝试在 BPI-F3 (Bianbu Linux) 上部署 Action Runner，遇到了一些问题，疑似需要重新编译 dotnet 或使用其他部署方法
2. [准备使用 Bianbu on BPI-F3 的打洞连接地址直接运行 Bianbu 的测试](https://github.com/255doesnotexist/lintestor/commit/ff2c7f686cd17a3624105fd0fb24dc883a1ba40c)

## 未来计划

1. 在 BPI-F3 上部署 RISC-V GitHub runner（也许直接打洞然后配置成 remote 测试）[进行中]
2. 支持 Bianbu 的自动化测试 [进行中]
3. 探索支持 VNC 或 KVM 的图形化测试 [搁置中]
4. 考虑 GitHub Actions 测试完成后自动提交 PR
5. 扩展测试范围
6. 实现 metadata 机制支持 [还没写，但现在的包信息管理太脏了]
7. 为现有包的测试编写 metadata.sh
8. 制定 lintestor 项目的 roadmap，方便协作 [感觉可能还是一人项目的概率大些]
9. 文档文档文档写一写