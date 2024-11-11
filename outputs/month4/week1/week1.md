## week1 (20241104 - 20241110)

### 1. 在 Boardtest 中集成米家 SDK 实现自动化电源控制
- [0ca8add](https://github.com/255doesnotexist/boardtest/commit/0ca8add)
- 使用 miio 实现基础的米家 SDK 功能

- [f1eca6c](https://github.com/255doesnotexist/boardtest/commit/f1eca6c)
- 在开发板配置中添加可选的米家 SDK 配置

- [31e07c1](https://github.com/255doesnotexist/boardtest/commit/31e07c1)
- 实现使用米家 SDK 自动控制开发板上下电（待进一步测试）

- [f1f936b](https://github.com/255doesnotexist/boardtest/commit/f1f936b)
- 添加命令行选项以开启/关闭米家 SDK 功能

### 2. boardtest server API 文档和加了点功能
- [7fde519](https://github.com/255doesnotexist/boardtest/commit/7fde519)
- 实现远程测试和开发板配置写入功能（需要 token）

- [7c83231](https://github.com/255doesnotexist/boardtest/commit/7c83231)
- 添加测试和开发板配置覆盖标志

- [ed063cb](https://github.com/255doesnotexist/boardtest/commit/ed063cb)
- 补充 API 文档

### 3. 文档
- [aa0ccd5](https://github.com/255doesnotexist/boardtest/commit/aa0ccd5)
- 在 README 中添加 python-miio 依赖说明

试着做了开发板自动上下电的框架代码。

另外可以远程写入测试和板子的配置了。

写了一点 API 文档，接入 lintestor 的时候顺手一点。

米家的东西还得再改改测试。