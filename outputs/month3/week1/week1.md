## week 1 (1008 - 1014)
### lintestor 主仓库部分：

1. **CI/CD 改进**:  主要集中在发布流程的自动化和修复交叉编译问题。
    - [d9ced98](https://github.com/255doesnotexist/lintestor/commit/d9ced98e10eb823cd6a8f18d4d375b748a9829c3)  `ci(publish): add auto-publish` -  实现自动发布：版本变更时触发自动发布流程。
    - [35dfba4](https://github.com/255doesnotexist/lintestor/commit/35dfba48988693b49bd58c3152e3bbe0b7b96da9) `ci(release): fix action Cross Compilation error no 29` - 修复交叉编译错误：移除 `powerpc64` 架构。
    - [36aaf0a](https://github.com/255doesnotexist/lintestor/commit/36aaf0a7b1c1239444c9424dbab311ebab66f390) `ci(release): fix release workflow #28 & pull only` -  修复 release workflow，移除 docker 构建过程，更新 action。
    - [820c5c7](https://github.com/255doesnotexist/lintestor/commit/820c5c797300289c9b13843d7e82c4f0c50ec20d) `ci(fix): try to fix cross compilation workflow` - 尝试修复交叉编译 workflow，使用自定义 Dockerfile。
    - [8c43420](https://github.com/255doesnotexist/lintestor/commit/8c4342095fb4a67ba509ddbd30b599b73a5db52d) `ci(release): give each architecture binaries different names` -  为不同架构的二进制文件赋予不同的名称。
    - [50bd2f9](https://github.com/255doesnotexist/lintestor/commit/50bd2f921254369e3a9a0efd6524f5eabcc3d797) `ci(all): move to self-hosted runners` - 将 CI 流程迁移到自托管的 runner 上。
    - [ea48aca](https://github.com/255doesnotexist/lintestor/commit/ea48acafe69b5b77f9d78fd7488799f41ce047e2) `ci(release): make it nightly` - 实现 nightly build，并添加日期到二进制文件名中。
    - 相关 issue：[CI 中尝试添加 nightly 交叉编译 riscv64gc 架构时提示 OpenSSL 某个汇编文件编译不过 #22](https://github.com/255doesnotexist/lintestor/issues/22)
    - 然后把所有 workflow 都转移到了 self-hosted runner 上跑。避免超时问题。

2. **元数据更新**: 添加了许可证、描述和仓库信息。
    - [add1881](https://github.com/255doesnotexist/lintestor/commit/add18814b3f4fe5611748ea8477b5f2b62b89887) `metadata: add lincense, description, repository` - 添加 LICENSE 文件，项目描述和仓库信息。
    - crates.io publish 前置条件。

3. **文档改进**:  添加了更多注释。
    - [53c93e7](https://github.com/255doesnotexist/lintestor/commit/53c93e71f2e539b42477ab73a991184e62126e0c) [4f18892](https://github.com/255doesnotexist/lintestor/commit/4f18892c95ad6ac275f0b03194ab41d3d636fc03) - 都是添加更多注释。

4. **代码风格**: 应用了自动格式化。
    - [19b3045](https://github.com/255doesnotexist/lintestor/commit/19b3045a4497997d3203be5171a4991b24e302f7) `style: apply automatic formatting` - 应用自动格式化。

5. **可能可复用的 Rust for rv64gc(etc.) 交叉编译用 Docker 镜像**
   - [docker hub](https://hub.docker.com/r/255doesnotexist/lintestor-cross-compile)
   - [docker file](https://github.com/255doesnotexist/lintestor/blob/main/Dockerfile)
   - 主要解决的是 cross-rs 内建的 gcc 工具链版本实在太老无法编译 openssl 的问题。