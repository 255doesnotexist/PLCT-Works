## week 2 (0916 - 0922)

### lintestor 主仓库部分:

1. 重构测试运行器，优化元数据提取:
   - [使用模式匹配重构本地和远程测试运行器中的元数据提取](https://github.com/255doesnotexist/lintestor/commit/d9115d7)

2. 改进测试脚本管理:
   - [为 TestScriptManager 添加 get_metadata_script_names 功能](https://github.com/255doesnotexist/lintestor/commit/cd29cd4)
   - [更新 TestScriptManager 文档](https://github.com/255doesnotexist/lintestor/commit/56d1626)

3. 修复远程测试相关问题:
   - [修复远程元数据脚本路径错误 (issue #17)](https://github.com/255doesnotexist/lintestor/commit/451e0a7)
   - [修复远程测试目标上的路径问题](https://github.com/255doesnotexist/lintestor/commit/c1ff887)
   - [修复远程测试中 tar 路径变更问题](https://github.com/255doesnotexist/lintestor/commit/e3d386e)
   - [在远程测试结果判断中使用 exit_status](https://github.com/255doesnotexist/lintestor/commit/c1ff887)

4. 改进报告生成:
   - [修订 Markdown 报告格式](https://github.com/255doesnotexist/lintestor/commit/2e78791)
   - [在 Markdown 报告中添加更多环境信息列 (fix #18)](https://github.com/255doesnotexist/lintestor/commit/ec861ca)

5. 新功能开发:
   - [实现独立的包元数据功能](https://github.com/255doesnotexist/lintestor/commit/5c7189e)

### 测试脚本部分:

1. 添加元数据脚本:
   - [为 Bianbu 添加所有元数据脚本](https://github.com/255doesnotexist/lintestor/commit/dba8329)
   - [为 Debian 添加所有元数据脚本](https://github.com/255doesnotexist/lintestor/commit/7952d24)

2. 更新测试结果:
   - [重新测试并同步所有报告](https://github.com/255doesnotexist/lintestor/commit/01c30db)

### Issue 修复:

1. 解决 Issue: [remote模式下无法正确获得测试脚本返回值 #16](https://github.com/255doesnotexist/lintestor/issues/16)
   - 修复了远程测试中获取测试脚本返回值的问题
   - 相关提交: [b4d9884](https://github.com/255doesnotexist/lintestor/commit/b4d9884), [c1ff887](https://github.com/255doesnotexist/lintestor/commit/c1ff887), [e3d386e](https://github.com/255doesnotexist/lintestor/commit/e3d386e)

2. 解决 Issue: [在 remote 类型测试中获取包元信息的方式存在问题 #17](https://github.com/255doesnotexist/lintestor/issues/17)
   - 修复了远程测试中获取包元信息的路径问题
   - 相关提交: [cd29cd4](https://github.com/255doesnotexist/lintestor/commit/cd29cd4), [451e0a7](https://github.com/255doesnotexist/lintestor/commit/451e0a7)

3. 解决 Issue: [Markdown report 在添加测试环境列后在多发行版测试时工作不正常 #18](https://github.com/255doesnotexist/lintestor/issues/18)
   - 修复了 Markdown 报告在多发行版测试时的列宽问题
   - 相关提交: [ec861ca](https://github.com/255doesnotexist/lintestor/commit/ec861ca84f2c4f92646b376c87d721651507f9a4)

### 未来计划：

1. 试着把 [CI 自动发版 (nightly?) #14](https://github.com/255doesnotexist/lintestor/issues/14) 做出来。
2. 按剩下的 roadmap 来。