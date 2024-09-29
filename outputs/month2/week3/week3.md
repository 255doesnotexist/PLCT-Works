## week 3 (0923 - 0929)

### lintestor 主仓库部分:

1. CI 和发布改进:
    - 做了自动发版。但现在只能 amd64 用。
      - 并没有成功支持 ~~[ci(release): support multi archs](https://github.com/255doesnotexist/lintestor/commit/4fe3062)~~
      - [ci(release): removed cross-rs unsupported archs](https://github.com/255doesnotexist/lintestor/commit/d926bb1)
      - [ci(release): nightly release](https://github.com/255doesnotexist/lintestor/commit/47ddaf1)
    - 更新一些用法：
      - [ci(release): update download-artifact v4](https://github.com/255doesnotexist/lintestor/commit/6e3ca51)

2. 报告生成优化:
   - 独立测试环境部分到下方了。
     - [feat(maarkdown_report): optimized summary matrix (just give it a try)](https://github.com/255doesnotexist/lintestor/commit/6ffb21e)
     - [fix(markdown_report): ok it seems we need more newlines^^](https://github.com/255doesnotexist/lintestor/commit/69d921d)

3. 代码质量改进:
   - [linting: make clippy happy](https://github.com/255doesnotexist/lintestor/commit/573aee8)
   - [style: apply automatic formatting](https://github.com/255doesnotexist/lintestor/commit/5aeec47)

4. 合并了 panglars 的 pull request：
    - [Add openkylin test script and interrupted more metadata echo error](https://github.com/255doesnotexist/lintestor/pull/23)

### Issue 修复:

1. 解决 Issue: [测试环境信息独立到表格下方 #21](https://github.com/255doesnotexist/lintestor/issues/21)
   - 实现了将测试环境信息独立到表格下方的功能
   - 相关提交: [6ffb21e](https://github.com/255doesnotexist/lintestor/commit/6ffb21e), [69d921d](https://github.com/255doesnotexist/lintestor/commit/69d921d), [8093284](https://github.com/255doesnotexist/lintestor/commit/8093284)

2. 解决 Issue: [Lintestor 在 CI 上因 Metadata 机制执行失败 #20](https://github.com/255doesnotexist/lintestor/issues/20)
   - 修复了 CI 上因 Metadata 机制执行失败的问题
   - 相关提交: [7020cd5](https://github.com/255doesnotexist/lintestor/commit/7020cd5)

3. 部分解决 Issue: [CI 自动发版 (nightly?) #14](https://github.com/255doesnotexist/lintestor/issues/14) 
4. 提了 Issue：[CI 中尝试添加 nightly 交叉编译 riscv64gc 架构时提示 OpenSSL 某个汇编文件编译不过 #22
](https://github.com/255doesnotexist/lintestor/issues/22)
    - 在调试发版问题时发现一个交叉编译问题

### 未来计划：

1. 尝试做一个满足编译条件的 docker 镜像（或其他方式）用来给 rv64 发版。
2. 想想办法改善代码质量。
3. 有点想加一个模式支持调用 autotester 或其他方式给板子上环境测试。