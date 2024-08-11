## pre week (prior to 0709)

本周工作

1. **boardtest 项目基础框架开发及功能扩展**
   - 完成了基本的 USB SD Mux 支持功能的开发。
   - 编写并通过了 SD-Mux 基础控制器类的功能。（但 SD-Mux 包在测试机上不可用）
   - 增加了一个重定向类使切换 sd-mux-ctrl 或 sd-mux 包作为 SDWireC 驱动成为可能。
   - 增加了丰富的 CLI 界面和报告接口，添加了人类友好的提示信息。
   - 完成了闪存和测试开关功能的初步验证。
   - 增加了 `dd` 进度参数。
   - 使板子和测试的配置更加灵活，完成了基本框架的开发。

2. **文档和配置文件更新**
   - 增加了兼容设备列表。
   - 增加了 BananaPI BPI-F3 板子的配置文件。
   - 增加了一些文档并填充了配置文件，修正了 SD 检测部分，增加了更多输出。
   - 移除了配置文件中无用的设备参数。

3. **问题修复和测试**
   - 修复了一些 CLI 小问题。
   - 修复了 `eject` 命令的在代码中的误用。
   - 修复了驱动配置格式错误。
   - 修正了 `image_path` 未应用的问题。
   - 进行了初步的调试测试，并在 Bianbu 系统上进行了测试。
   - 修正了主要测试服务器的连接逻辑问题。
   - 原本在 StarFive VisionFive 1 上测试，但遇到 SDWireC 信号完整性问题该板子无法从 SDWireC 卡启动，更换设备后测试完成。

4. **依赖管理**
   - 完成了 `requirements.txt` 文件的添加。
   - 修改了 pyserial 相关的使用方法。

产出文档：
- [Boardtest 项目 README 文档](https://github.com/255doesnotexist/boardtest/blob/main/README.md)
- [Boardtest 项目本身](https://github.com/255doesnotexist/boardtest/)

预期工作：
1. 完成 USB SD Mux 软件包支持的开发。
2. 优化日志输出功能，减少不必要的 stdout 输出。
3. 完善和测试自动化测试框架。
4. 扩展兼容设备列表，增加更多板子的支持。

PS: 有一部分是 GPT 读取 commit log 生成的所以具体条目比较冗杂。