# month 5 (2024 - 12)

本月产出不多。主要在月初完成了一些测试环境相关改进:

1. 修复了测试环境问题:
- [344c5ea](https://github.com/255doesnotexist/lintestor/commit/344c5ea) 修复 Fedora VM 测试环境
- [c3bef23](https://github.com/255doesnotexist/lintestor/commit/c3bef23) 修复 Debian CI 在某些版本的 QEMU 上启动时有 ROM 重叠问题，使用 `fw_jump.bin` 替代 `.elf`
- [52266c0](https://github.com/255doesnotexist/lintestor/commit/) 修复 QEMU 脚本路径问题

2. 重构测试脚本:
- [753d424](https://github.com/255doesnotexist/lintestor/commit/753d424) Fedora 环境中分离 boot 和 init 功能
- [2dc459e](https://github.com/255doesnotexist/lintestor/commit/2dc459e) 调整 Fedora SSH 端口至 2223

3. 测试报告更新:
- [1a72034](https://github.com/255doesnotexist/lintestor/commit/1a72034) 添加 `apt update` 修复依赖安装
- [b8190a2](https://github.com/255doesnotexist/lintestor/commit/b8190a2) 更新测试总结，合入 Fedora 结果
- [4605156](https://github.com/255doesnotexist/lintestor/commit/4605156) 更新 Debian 测试结果
- [2f8786d](https://github.com/255doesnotexist/lintestor/commit/2f8786d) 更新 Fedora 测试结果
- 都更新了一下因为 CI 最近出了点问题不手动更新就有点旧了

4. 其他改进:
- [8e08f13](https://github.com/255doesnotexist/lintestor/commit/8e08f13) 添加测试环境管理器的日志功能
- [e9c1b5e](https://github.com/255doesnotexist/lintestor/commit/e9c1b5e5a665838f4636967f6ad00293f42ac2ea) 添加测试失败时的交互式提示选项

月中旬和下旬因课程设计和期末考试，基本无产出。