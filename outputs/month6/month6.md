# month 6 (2025 - 01) 

1. RT-Thread 测试：  
   - 基于 QEMU 验证了 RT-Thread Standard 与 Smart 版本（含用户应用根文件系统）的启动、Shell 交互及 `poweroff` 关机功能（基于 [测试文档](https://github.com/plctlab/plct-rt-thread/blob/notes/0.notes/20241223-rtt-test-guide.md) 要求的 case 5/6）。编译生成 `rtthread.bin` 后，标准版和 Smart 版均正常进入 `msh`/`ash`，关机流程完整。任务后续取消因此无公开报告。  
 

2. 操作系统比较测试报告：  
   - **openEuler 24.03 SP1**：适配 QEMU 固件后成功启动，验证桌面基础功能（[报告](https://github.com/QA-Team-lo/oscompare/blob/main/openEuler/QEMU/README.md)）。  
   - **deepin 23 Beige preview**：基于 oe 启动脚本重写修改后启动 LiveCD，但全盘安装存在分区计算错误（-29XMiB），需手动补全 EFI 文件；登录后 QEMU 假死暂未解决（[报告](https://github.com/QA-Team-lo/oscompare/blob/main/Deepin/QEMU/README.md)）。  

3. CI 小改，没调完：  
   - 重构 Lintestor 的多发行版测试工作流（[分拆 commit](https://github.com/255doesnotexist/lintestor/commit/d2a61d56bad636e4572b41392b5cd0d0fc298494)），支持按发行版独立运行测试；合并代码清理 PR [#64](https://github.com/255doesnotexist/lintestor/pull/64)，减少冗余字符串分配。 
