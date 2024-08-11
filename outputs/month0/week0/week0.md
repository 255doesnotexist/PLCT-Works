## week 0 (0710 - 0714)

本周工作

1. 周一晚入组，大约在周二左右完成全部群组权限、PVE 设施权限接收。
2. 熟悉了 SpacemiT X60 AI 相关的文档，计划在 BPI-F3 上跑起几个 demo。
3. 利用 spacemit-ai-sdk 结合 qemu 仿真部署测试了图像分类、目标检测模型。产出文档：
- [spacemit-ai-sdk 相关文档产出](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/spacemit_sdk.md)
4. 在 x86_64 主机上编译通过了 SpacemiT 官方提供的，图像分类、目标检测 demo。
5. 在 BananaPI BPI-F1 (SpacemiT K1) 板子上正常执行了图像分类、目标检测的 demo。产出文档：
- [BananaPI BPI-F3 运行官方示例图像分类、目标检测 DEMO
](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/spacemit_demo.md)
6. 观察到有人曾在 16GB 版本 BPI-F3 上跑通 ChatGLM2-6B Q4 量化版 ONNX 模型。写了简单展望，但因硬件限制（测试板仅有 4GB RAM）原因暂时搁置。
- [【WIP】BananaPI BPI-F3 运行 ChatGLM2 Q4 量化版
](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/chatglm2.md)