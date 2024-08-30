## week 3 (0826 - 0901)

1. 因可能存在多发行版的测试，```--locally``` 选项与设计逻辑不合（假设测试机是 debian，locally 选项启用后会在 debian 上嗯跑所有发行版的测试脚本我不好说这是什么设计），因此[弃用](https://github.com/255doesnotexist/lintestor/commit/ba42ba99a9cb243c402cee01553268d7bce190e5)。
2. [发行版的测试配置现在可以配置成不同的类型](https://github.com/255doesnotexist/lintestor/commit/bb284190794def8fc6879a61a485ab2c449e7da6)，'locally'、'remote'、'qemu-based-remote' 分别对应该发行版可用本地测试主机环境执行、利用 SSH 远程执行、基于自动启停 QEMU 功能用 SSH 远程执行三种情况。这样上回的 QEMU 启动也不用单独加开关了。但是用字符串是不是不如用 enum 优雅嗯🤔。
3. 正准备用[神秘的 Bianbu on BPI-F3 的打洞连接地址](https://github.com/255doesnotexist/lintestor/commit/ff2c7f686cd17a3624105fd0fb24dc883a1ba40c)直接跑起 bianbu 的测试玩。（另，凭据直接暴露在 public repo 真的不会有安全问题吗😰）
4. 关于 bianbu，总感觉能复用 debian 的大部分测试脚本。（虽然都不很健壮 XD）