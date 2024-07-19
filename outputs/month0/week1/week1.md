## week 1

本周工作

1. 周一接下在 Debian Sid 系统上接续 [isrc-cas/tarsier-meta](https://github.com/isrc-cas/tarsier-meta/blob/main/report/info.md) 开发自动测试软件包工具的任务。
2. 在 Infra 提供的设施上拉取部署了 RISC-V Debian Sid 镜像并展开开发工作。(另附[部署开发环境镜像文档](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month0/week1/qemu_debian_riscv64.md)一份)
3. 着手开发自动化 Debian 软件包测试工具。（或调研已经可用的自动化测试工具。）
4. 发现可用的自动化包测试工具 autopkgtest。在本机启用 source 源后即可通过 ```apt source nano``` 下载包对应的源码和测试描述文件。启动 QEMU 虚拟机后使用 ```autopkgtest nano_7.2-1+deb12u1.dsc -- ssh -H root@localhost -p 2222 -- ``` 即可执行该包对应的自动化测试。
5. 在 QEMU RISC-V Debian Sid 环境下手动测试了 nano_7.2-1+deb12u1 软件包。通过。自动化测试工具开发中。
6. 开发了 RISC-V Debian 包可用性测试工具 [lintestor](https://github.com/255doesnotexist/lintestor)

    基于 git commit log 的总结：
   - 添加了在提取文件之前清理远程目录的功能。
   - 修正了 Markdown 表格格式的问题。
   - 移除了 TOML 报告格式，改为使用 JSON 格式。
   - 添加了 CMake 相关测试。
   - 在测试后添加了清理临时文件的功能。
   - 完成了基于 SSH 的远程测试功能，并添加了相关依赖 ssh2。
   - 初步添加了通过 SSH 进行测试的功能。
   - 添加了 Debian GCC 的简单测试。
   - 添加了 PRINT_SSH_MSG 以启用 SSH 在标准输出的打印（供调试）。
   - 修正了 serde 派生序列化的误用问题。
   
1. lintestor 基本具备在 QEMU 执行包测试、生成[可用性矩阵](https://github.com/255doesnotexist/lintestor/blob/main/summary.md)的能力。

未来工作

1. 维护重构 boardtest 的代码。
2. 为 lintestor 填充各类包软件测试用例。
3. lintestor 测试结果成熟时并入支持矩阵 QEMU 相关目录下。
4. 接新的任务。