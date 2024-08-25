## week 2 (0819 - 0825)

### lintestor 主仓库代码部分：

1. 合并了第一位贡献者 [aisuneko](https://github.com/aisuneko) 的 [Pull Request](https://github.com/255doesnotexist/lintestor/commit/1fac3229bc61e28a3bf05840e8e51bb44b1920e2)。
2. 为 [RemoteTestRunner 部分实现了 verbose](https://github.com/255doesnotexist/lintestor/commit/903574609d3c8672dfe76827ca6232d624dbca1f)，并调整了 verbose flag 初始化的位置（在创建 TestRunner 实例时）。当 verbose 启用时，将会在标准输出打印测试脚本的运行输出等。
3. 修复了 [TestEnvManager](https://github.com/255doesnotexist/lintestor/commit/25cb8a80fed9685d85e7c828cfeadc603b0972be) 可能无视本地测试 ```--locally``` 参数状态，依旧启动 QEMU 的问题。后续可能将“是否使用虚拟环境管理器”也独立为配置文件开关。这样，关闭 QEMU 启动后，复用原有代码即可实现利用 SSH 在远程测试机上执行测试的功能。
4. 修改了 report.json 的格式，使其能够承载测试脚本的输出结果。
   - 在 [本地和远程 TestRunner](https://github.com/255doesnotexist/lintestor/commit/b333650929085144d1bec4ef889cd7479a48b7c6) 中修改生成 report.json 的实现，输出测试脚本运行时向标准输出和标准错误写入的内容。
   - 在 [TestResult 结构体](https://github.com/255doesnotexist/lintestor/commit/d3c4246f46ebc8441237f44e5caa371633db91eb) 中加入 output 字段。
5. 支持了单软件包的多个测试脚本。不同脚本的测试结果将写入 report.json 中 test_results 列表的不同位置。其中 test_name 指向脚本文件名。
   - 加入 [TestScriptManager](https://github.com/255doesnotexist/lintestor/commit/1abb22247542dc6dbde9350d2a2cdfc03c9d4fb4) 用于获取不同发行版不同包的测试脚本列表。
   - 修改 [TestRunner](https://github.com/255doesnotexist/lintestor/commit/5ed367e2267ff31b2001653406cae925e72f9bbd)，应用多脚本测试的逻辑。由于原本的包版本获取逻辑依赖单测试脚本的假设，暂时移除包版本信息。
   - 带回包版本信息，通过在 [TestRunner](https://github.com/255doesnotexist/lintestor/commit/cafe3788d85a0f9c280da3fd394fd3927a4e24d7) 中以兼容旧脚本的方式获取包版本。
   - 未来需要加入 metadata.sh，用于获取测试时的各项元信息，希望与原本的测试逻辑解耦。

### 测试脚本部分：

1. 为 Debian 的[全局依赖脚本](https://github.com/255doesnotexist/lintestor/commit/c8c150cd83d05ff1748c2f6bf92da523f7c2f30f)中加入 Rust 等包的测试安装所依赖的 [sudo](https://github.com/255doesnotexist/lintestor/commit/d190d48a51b7c9c4ba59013904861a7d3b6775f7)、curl 等包。
2. OpenJDK 高版本不支持 sv48 以上的 paging modes，为测试通过，需要[在 cmdline 加入 no4lvl 关闭 4 级以上的分页模式并降级 OpenJDK 版本至 11](https://github.com/255doesnotexist/lintestor/commit/177a8f25797bc59cf332c99bd045bd43c4b37fec)。
3. 修复 numpy 包在[测试前不检查自身是否已安装](https://github.com/255doesnotexist/lintestor/commit/1326c5b7d1e8f751ae1929f2285575a66be3aa68)的问题。
4. 由于 report.json 格式变更，[重新冻结 docker 的测试结果](https://github.com/255doesnotexist/lintestor/commit/180c8436b076b5528259c7419b5d6c544dd44fd3)。
5. 基于合并 PR 后的代码和变更后的代码重跑了测试和矩阵（[#1](https://github.com/255doesnotexist/lintestor/commit/5d6d16a47f19f49dacf374329061185a9657607d), [#2](https://github.com/255doesnotexist/lintestor/commit/a75c82b47f7a97ad80287258abf01b526ad03f7c)）

### 其他：
试着在 BPI-F3 (Bianbu Linux) 上部署 Action Runner，遇到类似于下文的错误。

```
root@k1:/usr/share/dotnet# ./config.sh 
Must not run with sudo
ldd: ./bin/libcoreclr.so: 没有那个文件或目录
ldd: ./bin/System.Security.Cryptography.Native.OpenSsl.so: 没有那个文件或目录
ldd: ./bin/System.IO.Compression.Native.so: 没有那个文件或目录

--------------------------------------------------------------------------------
|        ____ _ _   _   _       _          _        _   _                      |
|       / ___(_) |_| | | |_   _| |__      / \   ___| |_(_) ___  _ __  ___      |
|      | |  _| | __| |_| | | | | '_ \    / _ \ / __| __| |/ _ \| '_ \/ __|     |
|      | |_| | | |_|  _  | |_| | |_) |  / ___ \ (__| |_| | (_) | | | \__ \     |
|       \____|_|\__|_| |_|\__,_|_.__/  /_/   \_\___|\__|_|\___/|_| |_|___/     |
|                                                                              |
|                       Self-hosted runner registration                        |
|                                                                              |
--------------------------------------------------------------------------------

# Authentication

What is the URL of your repository? 
<...省略>
Core dumped
```

猜测可能需要重新编译 dotnet，或换用其他手段部署。

### 未来计划：

1. 主代码中加入对 metadata 机制的支持。
2. 为目前已有的每个包的测试写 metadata.sh。
3. 给是否自动启动 QEMU 在每个发行版的配置里加一个开关。
4. 可能是时候给 lintestor 弄一个 roadmap，方便协作？（虽然不知道还会不会有 contributor 来了，（笑））
5. BPI-F3 那个 Action Runner 要是跑通了就能多测一维 Bianbu Linux 的结果了，可惜了。
6. 测试脚本还有俩疑似有点问题需要改改。