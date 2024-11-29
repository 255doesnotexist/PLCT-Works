# month 4

记录本月产出。

## 测试用例 / Testcases

### lintestor

#### CI/CD 系统改进
- [Fedora 测试脚本 & CIFAR](https://github.com/255doesnotexist/lintestor/commit/0977b319bf0b2bd6c1ed192ec6c4ac42baea7a4b)
  - apache、nodejs、postgresql 等 30 余个软件包在 fedora 下的简单可用性测试脚本
  - 基于现有 Debian 测试脚本进行适配
  - 包括软件包元数据脚本迁移

- [SSH 远程连接模块重构](https://github.com/255doesnotexist/lintestor/commit/0052a55)
  - 新增公钥认证机制支持
  - 在 `connection_config` 结构中添加 `private_key_path` 配置
  - 实现密码认证失败后自动尝试公钥认证

- [Fedora QEMU 测试环境配置](https://github.com/255doesnotexist/lintestor/commit/4d488aa)
  - 完成虚拟机启动和停止脚本
  - 配置基于 SSH 的远程连接参数
  - 设置测试环境配置文件 `config.toml`

- [依赖包更新](https://github.com/255doesnotexist/lintestor/commit/d090e84)
  - 版本更新至 0.1.4
  - 自动更新核心依赖：
    - clap 升级到 4.5.21
    - serde_json 升级到 1.0.133
    - serde 升级到 1.0.215

#### 测试运行器管理
- [BoardtestRunner 实现](https://github.com/255doesnotexist/lintestor/commit/0cef170)
  - 开发远程实机开发板测试环境运行器
  - 实现完整测试流程：
    - 创建测试客户端
    - 压缩并 base64 编码测试目录
    - 利用 API 上传自定义测试配置
    - 监控测试输出和结果

- [测试运行器管理重构 (WIP)](https://github.com/255doesnotexist/lintestor/commit/e833115)
  - 新增 `RunnerContext` 结构体
  - 实现 `RunnerManager` 支持多种测试环境类型

### boardtest

#### 服务端功能实现
- [API 接口重新设计](https://github.com/255doesnotexist/boardtest/commit/c5a823d4c7ce2cb4881ded1c5b5a63f00981933b)
  - 新增 5 个 API 端点：
    1. `POST /create_test`：创建测试实例
    2. `POST /start_test/{test_id}`：启动测试
    3. `GET /test_status/{test_id}`：查询测试状态
    4. `GET /test_output/{test_id}`：获取测试输出
    5. `POST /stop_test/{test_id}`：停止测试
  - 基于 token 的安全认证机制

#### 米家 SDK 集成
- [智能插座设备控制](https://github.com/255doesnotexist/boardtest/commit/0ca8add)
  - 使用 `python-miio` 库实现设备控制
  - 支持开发板自动上下电功能
  - 添加可选的米家 SDK 配置

- [远程测试配置支持](https://github.com/255doesnotexist/boardtest/commit/7fde519)
  - 实现 `/write_test` 和 `/write_config` 接口
  - 支持远程写入测试和开发板配置
  - 添加配置覆盖标志

### 测试环境建设

#### 配置与集成
- [Boardtest 配置选项扩展](https://github.com/255doesnotexist/lintestor/commit/a664d5a)
  - 在 `distro_config.rs` 新增 Boardtest 配置支持
  - 增加 `testing_type` 的 "boardtest" 选项
  - 新增配置项：
    - token：服务器认证令牌
    - board_config：板配置文件路径
    - serial：SD Mux 设备序列号
    - mi_sdk_enabled：米家 SDK 控制器开关
    - api_url：测试服务器地址
    - timeout_secs：测试超时时间

## 未来计划

1. lintestor
   - 完善 Boardtest 接口测试流程
   - 添加 Firefox 自动化测试

2. boardtest
   - 米家 SDK 设备控制实际测试跑通
