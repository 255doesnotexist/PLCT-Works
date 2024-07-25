## week 1

本周工作


1. 为 [lintestor](https://github.com/255doesnotexist/lintestor) 添加了以下测试脚本：
   - cmake
   - docker
   - erlang
   - golang
   - haproxy
   - libmemcached
   - lighttpd
   - llvm
   - mariadb
   - nginx
   - nodejs
   - numpy
   - ocaml
   - apache
   - clang
   - gcc
   - gdb

2. 扩展了 [lintestor](https://github.com/255doesnotexist/lintestor) 的 `markdown_report` 生成函数，确保生成的报告能够展示所有的测试结果，并更加健壮。

3. 修改了 `aggregator` 的逻辑，使其携带更多包相关的信息。 
   
4. 以下包的测试脚本依赖环境较复杂，仍需调试。
   - apache
   - docker
   - golang
   - libmemcached
   - llvm
   - mariadb
  
5. 正尝试进行 GitHub Actions 部署。

未来计划

1. 继续编写并添加 debian 软件包测试脚本。实际成熟时合入支持矩阵。
2. 对依赖部署复杂的软件包构造更稳健的脚本。
3. 重构 boardtest。