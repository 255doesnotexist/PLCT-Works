# month 2

记录本月产出。

## 测试用例 / testcases

1. lintestor 项目
   - CI 和发布改进:
     - [实现了nightly自动发版功能,但目前仅支持amd64作为宿主](https://github.com/255doesnotexist/lintestor/commit/47ddaf1)
     - [更新了CI中的artifact下载方式至v4](https://github.com/255doesnotexist/lintestor/commit/6e3ca51)
     - 尝试支持多架构编译，但未成功：[移除了cross-rs不支持的架构](https://github.com/255doesnotexist/lintestor/commit/d926bb1)
   - 重构和优化:
     - [使用模式匹配重构了本地和远程测试运行器中的元数据提取](https://github.com/255doesnotexist/lintestor/commit/d9115d7)
     - [为TestScriptManager添加了get_metadata_script_names功能](https://github.com/255doesnotexist/lintestor/commit/cd29cd4)
     - [更新了TestScriptManager文档](https://github.com/255doesnotexist/lintestor/commit/56d1626)
   - 报告生成改进:
     - [优化了Markdown报告格式,将测试环境信息独立到表格下方](https://github.com/255doesnotexist/lintestor/commit/6ffb21e)
     - [在Markdown报告中添加了更多环境信息列](https://github.com/255doesnotexist/lintestor/commit/ec861ca)
     - [修订了Markdown报告格式](https://github.com/255doesnotexist/lintestor/commit/2e78791)
   - 修复问题:
     - [修复了远程测试中获取测试脚本返回值的问题](https://github.com/255doesnotexist/lintestor/commit/b4d9884)
     - [修复了远程测试中获取包元信息的路径问题](https://github.com/255doesnotexist/lintestor/commit/451e0a7)
     - [修复了远程测试目标上的路径问题](https://github.com/255doesnotexist/lintestor/commit/c1ff887)
     - [修复了远程测试中tar路径变更问题](https://github.com/255doesnotexist/lintestor/commit/e3d386e)
     - [在远程测试结果判断中使用exit_status](https://github.com/255doesnotexist/lintestor/commit/c1ff887)
   - 新功能:
     - [实现了独立的包元数据功能](https://github.com/255doesnotexist/lintestor/commit/5c7189e)
   - 代码质量改进:
     - [各种 linting 优化](https://github.com/255doesnotexist/lintestor/commit/573aee8)
     - [自动应用代码格式化](https://github.com/255doesnotexist/lintestor/commit/5aeec47)

2. 测试脚本扩展
   - 支持了 Bianbu 的测试。通过 remote 方式。
   - [为Bianbu添加了所有元数据脚本](https://github.com/255doesnotexist/lintestor/commit/dba8329)
   - [为Debian添加了所有元数据脚本](https://github.com/255doesnotexist/lintestor/commit/7952d24)
   - [合并了panglars的PR,添加了openkylin测试脚本并改进了元数据echo错误的解释](https://github.com/255doesnotexist/lintestor/pull/23)

3. 测试结果更新
   - [重新执行并同步了所有测试报告](https://github.com/255doesnotexist/lintestor/commit/01c30db)

## 问题修复

1. [修复了remote模式下无法正确获得测试脚本返回值的问题 (#16)](https://github.com/255doesnotexist/lintestor/issues/16)
2. [解决了在remote类型测试中获取包元信息的方式存在问题 (#17)](https://github.com/255doesnotexist/lintestor/issues/17)
3. [修复了Markdown report在添加测试环境列后在多发行版测试时工作不正常的问题 (#18)](https://github.com/255doesnotexist/lintestor/issues/18)
4. [实现了将测试环境信息独立到表格下方的功能 (#21)](https://github.com/255doesnotexist/lintestor/issues/21)
5. [修复了CI上因Metadata机制执行失败的问题 (#20)](https://github.com/255doesnotexist/lintestor/issues/20)
6. 部分解决了 [CI 自动发版 (nightly?) (#14)](https://github.com/255doesnotexist/lintestor/issues/14)
7. [解决了如果将remote类型的测试也置于仓库中，会造成连接验证信息泄露的问题 (#12)](https://github.com/255doesnotexist/lintestor/issues/12)
8. [完成了补全Bianbu Linux的测试脚本 (#11)](https://github.com/255doesnotexist/lintestor/issues/11)
9. [实现了为不同包的元数据提供灵活的配置文件 (#8)](https://github.com/255doesnotexist/lintestor/issues/8)
10. [完成了测试时动态获取包相关元数据的机制 (#6)](https://github.com/255doesnotexist/lintestor/issues/6)

## 其他内容

1. 发现并提出了新的问题: [CI中尝试添加nightly交叉编译riscv64gc架构时提示OpenSSL某个汇编文件编译不过 (#22)](https://github.com/255doesnotexist/lintestor/issues/22)
2. ~~尝试了在BPI-F3上部署GitHub runner，但遇到了一些问题，可能需要重新编译dotnet或使用其他部署方法。~~ 现通过 remote 方式直接进行测试。
3. 在 BPI-F3（4G RAM 版本） 上用 llama.cpp 跑通了 Qwen2-0.5B (Q5_K_M 量化) 的模型。
     - 背景：在 [llama.cpp issue #165](https://github.com/ggerganov/llama.cpp/issues/165) 观测到该软件包早已支持 rv64 但当时苦于没有支持 rvv 1.0 的板子无法投入实际应用。
     - 测试结果：在随机的小对话中，BPI-F3 能以 2~3 tokens/s 的速度给出回答。[作为对比，VisionFive2 的推理速度约为 17 s/token。](https://github.com/ggerganov/llama.cpp/issues/165#issuecomment-1470499272)
     - 看起来有利用到 rvv 1.0 的能力，加速很明显。
     - 关于此 DEMO 的详细文档[见此](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/qwen2.md)。

## 未来计划

1. 尝试创建一个满足编译条件的docker镜像（或其他方式）用于rv64架构的发版。
2. 考虑添加一个模式支持调用autotester或其他方式为板子上环境进行测试。
3. nightly自动发版功能，尝试支持更多架构。
4. 扩大测试覆盖范围。
5. ~~减少 git push -f 次数。~~