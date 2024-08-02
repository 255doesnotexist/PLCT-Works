# 在 Debian 12 x86_64 上部署一个 RISC-V QEMU Debian Sid

宿主机：Debian 6.1.94-1 (2024-06-21) x86_64 GNU/Linux

因为是跨架构模拟，需要参照 [Debian Wiki](https://wiki.debian.org/QEMU) 安装 qemu system 本体（GUI 包可忽略）。

```sh
sudo apt install qemu-utils qemu-system-x86 qemu-system-gui qemu-system-misc
```

然后前往 [Debian Quick Image Baker pre-baked images](https://people.debian.org/~gio/dqib/) 可领取预烘焙好的 rv64 Debian Sid 一枚。（自己有空闲也可以从头开始编译XD）

你可以这样下载并解压镜像。

```sh
wget -O rv64deb.zip "https://gitlab.com/api/v4/projects/giomasce%2Fdqib/jobs/artifacts/master/download?job=convert_riscv64-virt"
unzip rv64deb.zip
```

解压完成后，执行 ```ls -l```，你应该看到一个名为 ```dqib_riscv64-virt``` 的目录。

执行以下命令，你将进入这个目录，并生成一个启动脚本。

```sh
cd dqib_riscv64-virt
echo 'qemu-system-riscv64 -machine virt -m 1G -smp 8 -cpu rv64 \' > boot.sh
echo '-device virtio-blk-device,drive=hd \' >> boot.sh
echo '-drive file=image.qcow2,if=none,id=hd \' >> boot.sh
echo '-device virtio-net-device,netdev=net \' >> boot.sh
echo '-netdev user,id=net,hostfwd=tcp::2222-:22 \' >> boot.sh
echo '-bios /usr/lib/riscv64-linux-gnu/opensbi/generic/fw_jump.elf \' >> boot.sh
echo '-kernel /usr/lib/u-boot/qemu-riscv64_smode/uboot.elf \' >> boot.sh
echo '-object rng-random,filename=/dev/urandom,id=rng \' >> boot.sh
echo '-device virtio-rng-device,rng=rng \' >> boot.sh
echo '-nographic -append "root=LABEL=rootfs console=ttyS0"' >> boot.sh
chmod +x boot.sh
```

最后，执行 ```./boot.sh``` 即可启动新鲜出炉的 RISC-V 架构 Debian。这同时还会映射 2222 端口到本机，通过 SSH 等方式进行访问也很方便。

而后，可以通过克隆测试包存储库、执行测试脚本的方式，在 QEMU 中仿真测试各类 RISC-V Debian 软件包的情况。

如执行 boot.sh 时提示找不到 RISC-V BIOS：
（此问题在 Ubuntu 24.04 LTS WSL 上出现。已解决。）

```sh
qemu-system-riscv64: Unable to find the RISC-V BIOS "/usr/lib/riscv64-linux-gnu/opensbi/generic/fw_jump.elf"
```

请尝试安装 opensbi 和 u-boot-qemu 包：

```sh
sudo apt-get install opensbi u-boot-qemu
```

