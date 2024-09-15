## week 1 (0909 - 0915)

这周有跑在实机 BPI-F3 上的 bianbu 的测试结果了，可喜可贺^^

### lintestor 主仓库部分：

1. 解决 Issue: [如果将 remote 类型的测试也置于仓库中，会造成连接验证信息泄露 #12](https://github.com/255doesnotexist/lintestor/issues/12)
   - [在 CI 中添加从 SECRETS 读取 credentials 并在运行时替换原有配置的代码](https://github.com/255doesnotexist/lintestor/commit/4953cd295d2b36e371c3e36c4391032522018e37) 
   - [在配置文件中留下 placeholder](https://github.com/255doesnotexist/lintestor/commit/a6fbd4fde3e633f4c777ab765b842691d826bab3)
  
2. 解决 Issue: [补全 Bianbu Linux 的测试脚本 #11](https://github.com/255doesnotexist/lintestor/issues/11)
   - [改变配置启用 bianbu 测试，此时 clang 通过](https://github.com/255doesnotexist/lintestor/commit/832cfde23359d25b9a31265196861d503cb3335a)
   - [尝试全面复用 debian 相关测试](https://github.com/255doesnotexist/lintestor/commit/111ba26cc02a12ea37230ea4cf4a7004fb0c8291)
   - [测试结果初次同步](https://github.com/255doesnotexist/lintestor/commit/f2216930205e1de2bf9055fd922ad9f06f277137)

3. 其他对代码的小改动：
   - 现在会 [自动跳过不存在的包测试目录](https://github.com/255doesnotexist/lintestor/commit/ce7a36e5fdc03bf1ca24208ac4a0ba4560ba265f)。
   - 现在会 [将 remote 的标准输出返回记录到日志中](https://github.com/255doesnotexist/lintestor/commit/57f13bdfb4257f465dc0616e151b46db42270633)。
   - ~~好多次 make clippy happy (雾)。[#1](https://github.com/255doesnotexist/lintestor/commit/fff380356ed1444f3f492959502a74027fcb14e9) [#2](https://github.com/255doesnotexist/lintestor/commit/57aabdcd1af80536b8a3ab898351543784d78165)~~

4. CI 修复与改动：
   - 修好了 [原本自动格式化代码的 CI 无权限提交](https://github.com/255doesnotexist/lintestor/actions/runs/10873213811/job/30169081507) 的问题：
     - [ci(format): give the writting content permission to ci
](https://github.com/255doesnotexist/lintestor/commit/bd54836fa67fc3f0c0e5de24e03974c6e5e4ca4f)
     - 哎呀终于成功执行了：[style: apply automatic formatting
](https://github.com/255doesnotexist/lintestor/commit/b07d54e6d1236ee8702299e2d7f90fca494beb4d)
   - 修好了 [原本上传 artifacts 的 CI 已经过时的问题](https://github.com/255doesnotexist/lintestor/actions/runs/10873213811/job/30169081507) 的问题：
     - [ci(lintestor): update upload-artifacts v4
](https://github.com/255doesnotexist/lintestor/commit/d8e24536b187c6b736df5481d2f8c1fcff73a968)

### 测试脚本部分：

1. 重新执行了全部测试（debian reports 格式有小变更）：
   - [更新含 bianbu 的测试结果和矩阵](https://github.com/255doesnotexist/lintestor/commit/f2216930205e1de2bf9055fd922ad9f06f277137)
   - [更新全部的测试结果和矩阵（debian reports 需要 output 字段）](https://github.com/255doesnotexist/lintestor/commit/dddd421206a30336dd4b53717fbfe90469df8e0e)
  
2. 配置文件小修：
   - [bianbu/config.toml](https://github.com/255doesnotexist/lintestor/commit/2dc55c5888144fee5ed35ab49b30ac214e8dbfbc) 中的端口模板不应用双引号包裹因其定义为 u16 整型。

### 未来计划：

1. 构思尝试解决 [测试时动态获取包相关元数据的机制 #6](https://github.com/255doesnotexist/lintestor/issues/6)。
2. 与上一条一起讨论 [为不同包的元数据提供灵活的配置文件 #8](https://github.com/255doesnotexist/lintestor/issues/8)。
3. 试着把 [CI 自动发版 (nightly?) #14](https://github.com/255doesnotexist/lintestor/issues/14) 做出来。
4. [summary.md](https://github.com/255doesnotexist/lintestor/blob/dddd421206a30336dd4b53717fbfe90469df8e0e/summary.md) 里的版本号等信息似乎又丢失了。之前的临时 patch 似乎失效。和 1、2 一起解决。届时会提一个 issue。