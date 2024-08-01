# month 0

记录本月产出。

## 测试用例 / testcases

1. Boardtest项目
   - 完成了基本的USB SD Mux支持功能的开发
   - 编写并通过了SD-Mux基础控制器类的功能
   - 增加了重定向类使切换sd-mux-ctrl或sd-mux包作为SDWireC驱动成为可能
   - 增加了丰富的CLI界面和报告接口,添加了人类友好的提示信息
   - 完成了闪存和测试开关功能的初步验证
   - 增加了`dd`进度参数
   - 使板子和测试的配置更加灵活,完成了基本框架的开发
   - 修复了多个问题,包括CLI小问题、`eject`命令误用、驱动配置格式错误等
   - 在Bianbu系统上进行了测试
   [Boardtest项目](https://github.com/255doesnotexist/boardtest/)

2. SpacemiT X60 AI相关
   - 利用spacemit-ai-sdk结合qemu仿真部署测试了图像分类、目标检测模型
   - 在x86_64主机上编译通过了SpacemiT官方提供的图像分类、目标检测demo
   - 在BananaPI BPI-F1 (SpacemiT K1)板子上正常执行了图像分类、目标检测的demo
   [BananaPI BPI-F3运行官方示例图像分类、目标检测DEMO](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/spacemit_demo.md)

3. RISC-V Debian包可用性测试工具lintestor
   - 开发了基于SSH的远程测试功能
   - 添加了多个软件包的测试脚本,包括cmake、docker、erlang、golang、haproxy、libmemcached、lighttpd、llvm、mariadb、nginx、nodejs、numpy、ocaml、apache、clang、gcc、gdb等
   - 扩展了markdown_report生成函数,确保生成的报告能够展示所有的测试结果,并更加健壮
   - 修改了`aggregator`的逻辑,使其携带更多包相关的信息
   - 将硬编码的连接信息并入config.toml配置文件中
   - 尝试进行GitHub Actions部署
   [lintestor项目](https://github.com/255doesnotexist/lintestor)

## 文档内容

1. [Boardtest项目README文档](https://github.com/255doesnotexist/boardtest/blob/main/README.md)
2. [spacemit-ai-sdk相关文档](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/spacemit_sdk.md)
3. [QEMU Debian RISC-V64部署开发环境镜像文档](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month0/week1/qemu_debian_riscv64.md)
4. lintestor生成的[可用性矩阵](https://github.com/255doesnotexist/lintestor/blob/main/summary.md)
5. [【WIP】BananaPI BPI-F3运行ChatGLM2 Q4量化版](https://github.com/255doesnotexist/bpi-f3_demos/blob/main/chatglm2.md)

## 其他内容

1. [为lintestor准备了技术分享报告](https://github.com/255doesnotexist/PLCT-Works/blob/main/outputs/month0/week3/RuyiSDK%20%E6%94%AF%E6%8C%81%E7%9F%A9%E9%98%B5%20RISC-V%20%E8%BD%AF%E4%BB%B6%E5%8C%85%E6%94%AF%E6%8C%81%E6%83%85%E5%86%B5%E7%9F%A9%E9%98%B5%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95%E5%B7%A5%E5%85%B7%E6%80%BB%E7%BB%93.pptx)
2. 在Infra提供的设施上拉取部署了RISC-V Debian Sid镜像并展开开发工作

```bash
ezra@debian:~/dqib_riscv64-virt$ ls
boot.sh      nano-7.2                          nano_7.2.orig.tar.xz.asc  ssh_user_rsa_key
image.qcow2  nano_7.2-1+deb12u1.debian.tar.xz  readme.txt
initrd       nano_7.2-1+deb12u1.dsc            ssh_user_ecdsa_key
kernel       nano_7.2.orig.tar.xz              ssh_user_ed25519_key
ezra@debian:~/dqib_riscv64-virt$ cat boot.sh 
qemu-system-riscv64 -machine virt -m 1G -smp 8 -cpu rv64 \
-device virtio-blk-device,drive=hd \
-drive file=image.qcow2,if=none,id=hd \
-device virtio-net-device,netdev=net \
-netdev user,id=net,hostfwd=tcp::2222-:22 \
-bios /usr/lib/riscv64-linux-gnu/opensbi/generic/fw_jump.elf \
-kernel /usr/lib/u-boot/qemu-riscv64_smode/uboot.elf \
-object rng-random,filename=/dev/urandom,id=rng \
-device virtio-rng-device,rng=rng \
-nographic -append "root=LABEL=rootfs console=ttyS0"
```

3. 观察到有人曾在16GB版本BPI-F3上跑通ChatGLM2-6B Q4量化版ONNX模型,写了简单展望

## 未来计划

1. 继续编写并添加debian riscv64的软件包测试脚本,成熟时合入支持矩阵
2. 针对不同发行版的差异,提供例外配置文件及描述
3. 对依赖部署复杂的软件包构造更稳健的脚本
4. 重构boardtest项目
5. 完善lintestor的GitHub Actions部署
6. 维护重构boardtest的代码
7. 为lintestor填充各类包软件测试用例