# week 1 (20250505 - 20250511)

- lintestor 重构、实现模板测试系统

(顺序：新 -> 旧)

- 支持基于模板直出报告和 summary.md 总结报告、有断言、变量、引用能力

  * [feat: Implement template reference system for test templates](https://github.com/255doesnotexist/lintestor/commit/79d9bb0)
  * [feat: enhance template parser to support multiple assertions and improve attribute extraction](https://github.com/255doesnotexist/lintestor/commit/5754828)

- lintstor 实现测试步骤断言能力

  * [feat: Enhance assertion types and parser functionality](https://github.com/255doesnotexist/lintestor/commit/9bc36d6)
  * [feat: enhance template parsing with detailed logging and error handling](https://github.com/255doesnotexist/lintestor/commit/47688b6)
  * [fix: update test reports with correct execution timestamps and enhance variable extraction patterns](https://github.com/255doesnotexist/lintestor/commit/01783c)

- lintestor 模板变量系统 PoC

  * [feat: update test reports with new execution timestamps and output formatting](https://github.com/255doesnotexist/lintestor/commit/2032daf)

- 测试用模板新增

  * [feat: add comprehensive test reports and enhance report aggregation logic](https://github.com/255doesnotexist/lintestor/commit/dd2e969)

- CLI 参数重构到 cli_args.rs 中

  * [feat(v0.2.0): Enhance CLI argument handling and add report aggregation features](https://github.com/255doesnotexist/lintestor/commit/7254553)

- 大量关于新模板机制的解析和适配代码

  * [refactor: bunch of new templates adapts](https://github.com/255doesnotexist/lintestor/commit/526d9fb)

- 重构测试脚本管理器，为管理测试模板准备

  * [Refactor test script management to use templates](https://github.com/255doesnotexist/lintestor/commit/e7fb624)

- 利用重写的 TestExecutor 封装统一了测试行为

  * [feat: Implement unified test execution logic with TestExecutor](https://github.com/255doesnotexist/lintestor/commit/551603c)

- 将 lintestor 原本的比较局限限定的 [发行版, 包] 对应测试概念改为 [测试目标, 测试单元] 概念，保持兼容性但应用范围更广

  * [refactor: distro -> target, package -> unit](https://github.com/255doesnotexist/lintestor/commit/9fe79d8)