## week 3 (1021 - 1027)

1. 为 boardtest 编写了一个 server 并添加了 /start_test 接口，允许传入 token 和参数，远程调用全功能的 boardtest 并异步实时拿到测试结果。([20c71a0](https://github.com/255doesnotexist/boardtest/commit/20c71a0))
   - (预备为 lintestor 加入调用 boardtest 为目标开发板刷写对应 OS 后重新上电连接，便于测试目标操作系统包可用性的功能)([458058b](https://github.com/255doesnotexist/boardtest/commit/458058b))
   - 实现了基于 token 的身份验证机制，确保远程调用的安全性([2f6c9eb](https://github.com/255doesnotexist/boardtest/commit/2f6c9eb))
   - 优化了数据传输方式，逐字符推送避免卡在某一行不动([7017363](https://github.com/255doesnotexist/boardtest/commit/7017363))
   - 新增了测试模式下的 prompt always yes 参数支持，防止自动化测试时询问用户然后卡住([50a3d85](https://github.com/255doesnotexist/boardtest/commit/50a3d85))
   - 完善了服务端日志记录，便于问题追踪和调试([7017363](https://github.com/255doesnotexist/boardtest/commit/7017363))

2. 完成了 Bianbu v2.0 在 BPI-F3 开发板上的系统测试([bb17fe4](https://github.com/255doesnotexist/boardtest/commit/bb17fe4))
   - 替换了新版本的系统链接和下载地址
   - 验证了系统启动流程和串口登录功能
   - 收集并更新了完整的启动日志和系统信息
   - 测试报告已合并入主分支([3630bd6](https://github.com/ruyisdk/support-matrix/commit/3630bd6))

## 下周可能计划

1. 看看米家 SDK 如何控制自动上电下电
2. lintestor 适配接入 boardtest，需要思考怎么做
3. 把之前没跑完的 fedora riscv on qemu 配出来也作为一个测试环境
4. dirty 分支中加入 fedora 测试脚本
