# week 0 (20241202 - 20241208)

## 1. 持续集成与测试环境
- [344c5ea](https://github.com/255doesnotexist/lintestor/commit/344c5ea) 修了 Fedora VM 测试环境现在可用了
- [c3bef23](https://github.com/255doesnotexist/lintestor/commit/c3bef23) CI(Debian): 修复类似riscv-software-src/opensbi/issues/372 相关问题
  - 使用 `fw_jump.bin` 替代 `.elf`，避免 ROM 区域重叠问题
- [52266c0](https://github.com/255doesnotexist/lintestor/commit/) 修复 QEMU 脚本中意外的文件/目录不存在问题
  - 在脚本路径前追加变量工作目录

## 2. 测试环境脚本
- [753d424](https://github.com/255doesnotexist/lintestor/commit/753d424) Fedora 环境： `boot` 和 `init` 简单分离了一下功能
  - `boot.sh` 仅负责启动虚拟机
  - 初始化操作（下载、解压镜像、安装依赖、配置 SSH）移至 `init.sh`
- [2dc459e](https://github.com/255doesnotexist/lintestor/commit/2dc459e) 调整 Fedora SSH 服务端口
  - 更改端口为 2223，避免与其他虚拟机可能的端口冲突

## 3. 测试报告
- [1a72034](https://github.com/255doesnotexist/lintestor/commit/1a72034) Debian: 在 `prerequisite.sh` 中添加 `apt update` 避免软件源过旧测试时无法安装包问题
- [b8190a2](https://github.com/255doesnotexist/lintestor/commit/b8190a2) 更新测试总结（把 Fedora 的测试结果合进去了）
  - 包含 Debian、Bianbu 和 Fedora 的测试信息
- [4605156](https://github.com/255doesnotexist/lintestor/commit/4605156) 手动更新 Debian 测试结果 json
- [2f8786d](https://github.com/255doesnotexist/lintestor/commit/2f8786d) 手动更新 Fedora 的测试结果 json

## 4. 别的零散的
- [src/testenv_manager.rs](https://github.com/255doesnotexist/lintestor/commit/8e08f13) 测试环境管理器改进
  - 添加日志记录功能，支持调试信息输出
  - 小改优化 `run_script` 里几行实现
  - 增加日志记录：关于当前工作目录路径
