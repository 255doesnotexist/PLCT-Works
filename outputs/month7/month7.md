# month 7 (20250213 - 20250303)

## week 1 (20250213 - 20250216)

0214 返校后即周会，无产出。

## week 2 (20250217 - 20250223)

1. 在 Lintestor Weekly Debian CI Test 中试验性为测试用系统镜像启用缓存 ([1](https://github.com/255doesnotexist/lintestor/commit/cab3f39d4b9dc3fae9cd978b40744a6b75520d4e), [2](https://github.com/255doesnotexist/lintestor/commit/d0df47a8cc1f03ba4a749741162e08a1a5d54ccb))，避免每次从远端拉取系统磁盘镜像。后续如未发现明显问题也将应用到其他 qemu 类 ci 测试中。

    ![alt text](image.png)

2. 为 openjdk 测试[关闭 sv57](https://github.com/255doesnotexist/lintestor/commit/b1963886258af58e2a1093ba3a98bfd9a4cd712f)。因为“only satp modes up to sv48 are supported for openjdk now”。

3. 现在最终生成的 Markdown 报告产物会附带详细的测试名和测试输出（如果该组测试中的某一项测试未通过）。([3](https://github.com/255doesnotexist/lintestor/commit/9d57b4bd45a266e1948752dd5c38046c245ac5d8))

    ![alt text](image-1.png)

4. [弃用 actions/artifacts@v3 转向 actions/artifacts@v4](https://github.com/255doesnotexist/lintestor/commit/673096c32b176780a0abe5c241910c8c825254cb)。因 v3 版本 action 已在本月月初被 GitHub 弃用。

## week 3 (20250224 - 20250303)

1. 支持矩阵 [BPI-F3 Bianbu v2.1](https://github.com/ruyisdk/support-matrix/pull/179) 测试报告更新。将 sys_ver 更改为了 symver 格式，所以不需要再在 CI 插件中特殊处理此项，将 CI 插件一并修改。

2. lintestor 0.1.6

    - 现在会在测试前清理远端已存在的 report.json 避免潜在的测试报告可能未被新结果复写的问题。[1](https://github.com/255doesnotexist/lintestor/commit/11d05d039335d9b7766903a4ec5b188826819c34)
    - issue #78 修复了 summary.md 中潜在的失败测试日志与包位置错位不匹配的问题。[2](https://github.com/255doesnotexist/lintestor/commit/ced8255df894be34b745d47e593bc483d2fdb66a), [对应 issue](https://github.com/255doesnotexist/lintestor/issues/78)
    - 现在可以直接点击 summary.md 中的包链接跳转到具体的测试环境细节，如测试失败可见输出日志。[3](https://github.com/255doesnotexist/lintestor/commit/e1ad7e18c4c58a45d52def16bf69ad9a4af145e9)

3. Lintestor CI Fedora Test 部分重写，实现了在线构建安装 QEMU 9.2.2 以提供测试所需新版 QEMU 的方法。[4](https://github.com/255doesnotexist/lintestor/commit/88fa09528fc41ee11881f2440611cc01310e7105)

4. 另外还将 Fedora RISC-V Test 的测试用系统镜像换新到了 Fedora 41 20250224 版本。并弃用 expect 方式初始化镜像，改用 cloud-init 方式。[5](https://github.com/255doesnotexist/lintestor/commit/d4fb8ae3c331f826cb2d6957ff648216f1166f24), [6](https://github.com/255doesnotexist/lintestor/commit/a708cb04dfe8323b887f7044e759b57be8e85e96)

5. 一些 Lintestor CI 测试脚本的更正与适配工作：

    - 使得 fedora 测试脚本不必需求 root 账户， sudoers 即可。[7](https://github.com/255doesnotexist/lintestor/commit/56e8900e8683114a5c33ab69c9b2a2310fb705a1)
    - Fedora Test: 一些更正 mariadb, nginx, nodejs, numpy, openjdk, lighttpd, nginx, postgresql, redis, runc, rust, vanish, zookeeper [8](https://github.com/255doesnotexist/lintestor/commit/17012aa9b68b280c306b2594ef6f0d3b59a782cb), [9](https://github.com/255doesnotexist/lintestor/commit/010c7585d55f3d42320540d91debe867e4862b38)
    - Debian Test: rust (select default rust toolchain before testing) [10](https://github.com/255doesnotexist/lintestor/commit/cf76b0a7d5a4cacf01cbad47fb52c3c82679c9f1)
    - ~~Fedora CI: 移除 pflash, acpi=off 等旧版 QEMU 不兼容的参数。~~ CI 中已更新新版 QEMU 因此本变更作用可有可无。[11](https://github.com/255doesnotexist/lintestor/commit/27bed0c10e666f71f3ee5f0a22009e98d076593d), [12](https://github.com/255doesnotexist/lintestor/commit/b916e066d226cd6a5c7c41b26fe649875df625f9)
    - 自动的三个发行版 Debian (on qemu-system-riscv64), Bianbu (BPI-F3), Fedora (on qemu-system-riscv64) 包测试结果更新。[13](https://github.com/255doesnotexist/lintestor/commit/8bab5fb254dd6d3e763d200e844e889aaad850b1), [14](https://github.com/255doesnotexist/lintestor/commit/88bc80473d2f10e016ef9d6156e52bdb4dd7b859), [15](https://github.com/255doesnotexist/lintestor/commit/b644a6a9b4c3dbb63843cf141a0e3244f47e6dd0)
    - Fedora Test: 同样启用了上周类同 Debian 的 image cache。[16](https://github.com/255doesnotexist/lintestor/commit/aba98a21f9f063dba6256b62fa33dec107fc29de)

6. Bump depended crates:

    - [chore(deps): bump clap from 4.5.26 to 4.5.30](https://github.com/255doesnotexist/lintestor/commit/b7bc172163ab5ccf3338e9f9d0a0b88edd778285)
    - [chore(deps): bump serde_json from 1.0.137 to 1.0.139](https://github.com/255doesnotexist/lintestor/commit/54c0d1d28976f9eca064e2c7471e76efca0c3009)

7. 最新的 [summary.md](https://github.com/255doesnotexist/lintestor/blob/464c8dd2a8d6d26f7170478dcfd4146965c084ee/summary.md) 包测试结果矩阵。
