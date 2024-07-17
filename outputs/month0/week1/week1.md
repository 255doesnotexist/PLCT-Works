## week 0

本周工作

1. 周一接下在 Debian Sid 系统上接续 [isrc-cas/tarsier-meta](https://github.com/isrc-cas/tarsier-meta/blob/main/report/info.md) 开发自动测试软件包工具的任务。
2. 在 Infra 提供的设施上拉取部署了 RISC-V Debian Sid 镜像并展开开发工作。(另附[部署开发环境镜像文档](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month0/week1/qemu_debian_riscv64.md)一份)
3. 着手开发自动化 Debian 软件包测试工具。（或调研已经可用的自动化测试工具。）
4. 发现可用的自动化包测试工具 autopkgtest。在本机启用 source 源后即可通过 ```apt source nano``` 下载包对应的源码和测试描述文件。启动 QEMU 虚拟机后使用 ```autopkgtest nano_7.2-1+deb12u1.dsc -- ssh -H root@localhost -p 2222 -- ``` 即可执行该包对应的自动化测试。
5. 在 QEMU RISC-V Debian Sid 环境下手动测试了 nano_7.2-1+deb12u1 软件包。通过，测试报告待写。自动化测试工具开发中。