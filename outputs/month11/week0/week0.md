# week 0 (20250530 - 20250606)

- [[v0.2.0] templated test execution, enhanced report generator, and "variable" system for template](https://github.com/255doesnotexist/lintestor/pull/96) 为 Review 准备好
  - 清理旧代码、简化逻辑，executor options 之前留的 TODO 做完了
  - 修了下 Clippy workflow
  - 新增 `--keep-template-directory-structure (-k)` 选项，使报告目录默认保留模板目录结构
  - 移除分支中非代码的脏文件