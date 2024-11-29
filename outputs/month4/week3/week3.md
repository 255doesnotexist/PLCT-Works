## week 3 (20241118 - 20241124)

### 1. Boardtest 测试环境支持
- [0cef170](https://github.com/255doesnotexist/lintestor/commit/0cef170) feat(test_runner/boardtest): 基本实现 
  - 实现 BoardtestRunner 用于远程实机开发板测试环境
  - 实现完整的测试流程（连接 Boardtest Server）
    - 创建测试客户端
    - 压缩并 base64 编码测试目录
    - 利用 API 上传自定义测试命令配置
    - 启动测试，利用命令配置写入 base64 的数据到目标开发板
    - 然后在目标开发板上反 base64 解开恢复数据
    - 监控测试输出、并从返回码获取测试结果
  - 倒是可以自定义测试超时时间

- [a664d5a](https://github.com/255doesnotexist/lintestor/commit/a664d5a) feat(config/distro): 添加 Boardtest 配置选项
  - 在 `distro_config.rs` 中新增 Boardtest 配置支持
  - 扩展 `testing_type`，增加 "boardtest" 选项
  - 添加配置项：
    - token: Boardtest 服务器认证令牌
    - board_config: 板配置文件路径
    - serial: SD Mux 设备序列号
    - mi_sdk_enabled: 可选的 Mi SDK 控制器（用来自动上下电）
    - api_url: 测试服务器 API 地址
    - timeout_secs: 测试超时时间

- [be7cd40](https://github.com/255doesnotexist/lintestor/commit/be7cd40) fix(boardtest_config): 修复一些配置模块细节

### 2. 测试运行器管理重构
- [e833115](https://github.com/255doesnotexist/lintestor/commit/e833115) refactor(runner_manager): 测试运行器管理（WIP）
  - 新增 `RunnerContext` 结构体，整合多种测试运行环境的配置
  - 实现 `RunnerManager` 用于动态选择和创建合适的测试运行器
  - 支持本地、远程和 Boardtest 三种测试环境类型的切换
  - ~~为了洁癖试图解耦一点逻辑然而好像更乱了，而且还没写完~~

### 3. 测试框架配置更新
- 在 `USAGE.md` 更新配置示例
  - 详细说明 Boardtest 相关配置
  - 提供配置模板和必填/可选参数说明
- 修改 `main.rs` 支持 Boardtest 测试流程
  - 新增 `via_boardtest` 标志
  - 集成 BoardtestRunner 到测试流程

### 4. 两条玄铁视频评论

### 下周可能计划：
- （已接）Eulaceura 的 (Pioneer / Lichee4A) Chromium 测试报告
- （然而可用的 Lichee4A 正被更高优先级的数据库测试任务占着，Pioneer 再看看，Meles 倒是可用）
- `RunnerManager` 重构
- Boardtest 接口接是接上了总得保证有一次全跑通演示吧边跑边调
- 添加 Firefox 自动化测试
- 优化测试报告生成机制