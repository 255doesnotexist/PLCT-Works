## week 2 (1014 - 1020)

### lintestor 主仓库部分：

1. 配置修复
   - [fix(configs and etc.): further fix for connection_config](https://github.com/255doesnotexist/lintestor/commit/61906c0)
     - 为 connection_config 添加了 Option<T> 包装，使其成为可选项
     - 调整了 main 和 testenv_manager 以匹配 Option<T> 的变更
     - 添加了 is_not_qemu_based_remote 和 is_not_remote，并修改了相关跳过逻辑
     - 在 distro 检测过程中增加了更多调试日志

2. 为单元测试添加 CI workflow
   - [ci(unit_test): get ready for further unit tests](https://github.com/255doesnotexist/lintestor/commit/b76c25c)
     - 为进一步的单元测试做准备

3. 修复 ConnectionConfig 在解析时非可选的问题，并由此解决自动发行版探测失效的问题。
   - [fix: connection config cannot be skipped (issue #34)](https://github.com/255doesnotexist/lintestor/commit/859ac02)
     - 修复了 connection_config 无法被跳过的问题（issue #34）
     - 保留了 is_not_qemu_based_remote，因为它不是死代码

4. 其他改进（10月15日）
   - [ci(test): fix commit_message TT](https://github.com/255doesnotexist/lintestor/commit/ae42535)
     - 修了不太对的 ci commit_messag
   - [ci(test): auto commit test reports](https://github.com/255doesnotexist/lintestor/commit/6df46d3)
     - 实现了测试报告的自动提交
     - 使用了 stefanzweifel/git-auto-commit-action@v5
     - 添加了内容写入权限
   - [ci(format): only on pushing](https://github.com/255doesnotexist/lintestor/commit/1b66532)
     - 仅在推送时执行格式化，避免在 pr 中执行


5. 代码样式和格式化
   - [style: apply automatic formatting](https://github.com/255doesnotexist/lintestor/commit/49a5cc0)
     - 应用了自动格式化
  
6. Merge 请求
   - [Merge pull request #30 from panglars/muilt-test](https://github.com/255doesnotexist/lintestor/commit/63188e9)
     - 合并了来自 panglars/muilt-test 的 pull request #30
     - 更新了 make 命令，使其只选择失败的测试脚本在包中运行

## 下周计划

1. dirty 分支中加入 fedora 测试脚本
2. 为 boardtest 写一个 web 接口用于远端切换开发板不同系统以便测试