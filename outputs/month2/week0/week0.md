## week 0 (0902 - 0908)

### lintestor 主仓库部分：

1. 代码重构：拆分了一些太长不适合写在一个文件里的代码。
    - [split test_runner module into local and remote components](https://github.com/255doesnotexist/lintestor/commit/49728f4d24fb16f72f2f1bea81c39d616cdd7c7a)
    - [split config.rs into multiple modules](https://github.com/255doesnotexist/lintestor/commit/33859c2c903471a0a2c1568601b436c44538e0b4)
2. 一些洁癖清理：移除没用到的代码、让 clippy 开心、格式化。
   - [chore: remove unused imports](https://github.com/255doesnotexist/lintestor/commit/964fcae5dfee03f59f052e3c7e0bd1d47d320b8f)
   - [style: address Clippy lints](https://github.com/255doesnotexist/lintestor/commit/fb1fc74c70fe40a57ecaefb8fcc0ac8ed40de90b)
   - [style: formatting](https://github.com/255doesnotexist/lintestor/commit/e7a20c63fb75843603f3a5e51c56847444c2405e)
3. 文档：为代码写了初步的文档。
   - [docs: add comprehensive documentation to core modules](https://github.com/255doesnotexist/lintestor/commit/159227d3ba59df87abb5311b50475a39e12f3617)
4. CI：现在有了自动文档部署、Linting & Formatting、Dependabot
   - [ci: deploy Rust documentation to GitHub Pages](https://github.com/255doesnotexist/lintestor/commit/4709b77c573f2233afd3e2494c91654d502677bd)
   - [ci: automatic formatting](https://github.com/255doesnotexist/lintestor/commit/a0197abbc55bdfcf0668e800dfc2ed98d2a80ac2)
   - [ci: dependabot](https://github.com/255doesnotexist/lintestor/commit/b290260b79817c118cbfa7ffec66239c09761da2)
   - 以及从 dependabot 处合并数个 pull requests。此略。
   - [cargo doc 部署至 GitHub Pages](https://255doesnotexist.github.io/lintestor/)

5. Roadmap：整理未来开发计划至 issues，方便协作。
   - [#6](https://github.com/255doesnotexist/lintestor/issues/6)
   - [#7](https://github.com/255doesnotexist/lintestor/issus/7)
   - [#8](https://github.com/255doesnotexist/lintestor/issues/8)
   - [#9](https://github.com/255doesnotexist/lintestor/issues/9)
   - [#10](https://github.com/255doesnotexist/lintestor/issues/10)
   - ...
   - [#15](https://github.com/255doesnotexist/lintestor/issues/15)

6. README：
   - 贴上了 [Docs 和 Summary](https://github.com/255doesnotexist/lintestor/commit/8fbbb9a1ffab026508fdecdb5f95192fd97bda4d) 的链接

### 测试脚本部分：

本周无改动。

### DEMO 部分

- 在 BPI-F3（4G RAM 版本） 上用 llama.cpp 跑通了 Qwen2-0.5B (Q5_K_M 量化) 的模型。
  - 背景：在 [llama.cpp issue #165](https://github.com/ggerganov/llama.cpp/issues/165) 观测到该软件包早已支持 rv64 但当时苦于没有支持 rvv 1.0 的板子无法投入实际应用。
  - 测试结果：在随机的小对话中，BPI-F3 能以 2~3 tokens/s 的速度给出回答。[作为对比，VisionFive2 的推理速度约为 17 s/token。](https://github.com/ggerganov/llama.cpp/issues/165#issuecomment-1470499272)、
  - 看起来有利用到 rvv 1.0 的能力，加速很明显。
  - 关于此 DEMO 的详细文档[见此](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/qwen2.md)。

### 未来计划：

见 Roadmap。