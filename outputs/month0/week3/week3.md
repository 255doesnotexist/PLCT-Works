## week 3

本周工作


1. 为 [lintestor](https://github.com/255doesnotexist/lintestor) 准备了[技术分享报告](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month0/week3/RuyiSDK%20%E6%94%AF%E6%8C%81%E7%9F%A9%E9%98%B5%20RISC-V%20%E8%BD%AF%E4%BB%B6%E5%8C%85%E6%94%AF%E6%8C%81%E6%83%85%E5%86%B5%E7%9F%A9%E9%98%B5%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7%E6%80%BB%E7%BB%93.pptx)。

lintestor 主仓库代码部分：

1. 添加了配置功能，在根目录下有一个 [config.toml](https://github.com/255doesnotexist/lintestor/blob/5f3d7acd01558315490e142195f2bf058a914b18/config.toml) 作为 base_config。同时，不同发行版有不同的配置文件，位于 [\<distro\>/config.toml](https://github.com/255doesnotexist/lintestor/blob/5f3d7acd01558315490e142195f2bf058a914b18/debian/config.toml) 下，便于灵活管理启停测试环境、连接测试环境的各类参数。
2. 新增了[允许跳过特定包的功能](https://github.com/255doesnotexist/lintestor/commit/164452869fdd696511ecc2ee5df6a41493db0405)。此时应用上次（或手写的 report.json）。可以用于手动指定某发行版的特定包的测试结果。
3. 添加了 Clap 依赖并提供了更有趣些的[命令行交互逻辑](https://github.com/255doesnotexist/lintestor/commit/1c0e7309998be77cc19e1a7c1e1d0e49fb117c68#diff-42cb6807ad74b3e201c5a7ca98b911c5fa08380e942be6e4ac5807f8377f87fc)。
4. （上一条的意思是可选用哪个基本配置文件启动测试、仅执行测试或仅执行生成表格等不同模块。见 [README.md](https://github.com/255doesnotexist/lintestor/commit/1c0e7309998be77cc19e1a7c1e1d0e49fb117c68#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5)）
5. 增加了 [Debian](https://github.com/255doesnotexist/lintestor/commit/a0f63eec825db4adbb0c5d42c3cf582b55799676) [QEMU 虚拟机的自动启动/停止](https://github.com/255doesnotexist/lintestor/commit/e8d1c419e39cfa3b15acffb08e0e3253710434c2)。现在lintestor 能自动管理测试环境的启停了。
6. 删除[一些未使用的导入](https://github.com/255doesnotexist/lintestor/commit/7bae275969d7321d06fe6307613398dc453f1be8)、简单拆分了 [main.rs](https://github.com/255doesnotexist/lintestor/commit/1c0e7309998be77cc19e1a7c1e1d0e49fb117c68#diff-42cb6807ad74b3e201c5a7ca98b911c5fa08380e942be6e4ac5807f8377f87fc)。

Debian 测试脚本部分：

1. 修复了 [Apache](https://github.com/255doesnotexist/lintestor/commit/64110c85b2a07d5f81feb1684f6e1497c3a83465) 和 [HAProxy](https://github.com/255doesnotexist/lintestor/commit/c443263d8c2c60c7804eafe3dddb43e0652ecacf) 的测试逻辑
2. 移除、跳过了 [Docker](https://github.com/255doesnotexist/lintestor/commit/15699609255f8f33ef7695821eb1dfd4fed62f29) 自动化测试（可能意义不大，建议基于实机反馈修改 report.json）
