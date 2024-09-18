## lintestor 包自动化测试工具

### 预期目标

复刻 https://github.com/isrc-cas/tarsier-meta/blob/main/report/info.md 中原软件包可用性矩阵结果。给出 RISC-V 不同发行版下不同包可用的结果。计划加入串口连接方式和 GUI 相关测试。

### 目前进度

测试结果矩阵：https://github.com/255doesnotexist/lintestor/blob/main/summary.md

基本完成 Debian、Bianbu 部分。包的元数据信息记录获取方式仍待拓展。

支持测试配置为本地测试、连接远端开发板测试、借由 QEMU 进行测试三种类型。

测试内容灵活，可以自由编写测试脚本实现，亦可附带其他配置和二进制数据。框架仅负责统计合并结果。

配置示例：

```toml
testing_type = "remote"
skip_packages = []

[connection]
method = "ssh"
ip = "{BIANBU_IP}"
port = {BIANBU_PORT}
username = "{BIANBU_USERNAME}"
password = "{BIANBU_PASSWORD}"
```

### 仓库地址

https://github.com/255doesnotexist/lintestor

## boardtest 单板电脑自动化测试工具

### 预期目标

通过 SDWireC + 串口连接方式自动为 SD 卡内灌入不同操作系统。借由串口执行不同配置好命令的测试，以各类方式（返回值、字符串包含、Special Judge 等）判定测试结果。

### 目前进度

以上功能全部实现。包含两部分配置。

开发板配置 (boards/banana_pi_f3_config.toml) 示例：

```toml
[test_framework]
log_dir = "./logs" # 日志路径

[board]
board_name = "banana_pi_f3" # 板名

[serial]
serial_file = "/dev/ttyUSB0" # 串口设备文件
bund_rate = 115200 # 波特率
serial_name = "sdwirec_alpha" # sdwirec 名
sd_mux_device = "/dev/sda" # sdwirec 对应的磁盘设备

[os_list]
[os_list.Bianbu]
url = "/home/xyz/bianbu-23.10-nas-k1-v1.0rc1-release-20240429192450.img" # 可以写镜像的在线 url 或本地路径、会自动拉取刷入
dd_params = ["bs=4M", "conv=fsync", "status=progress"] # 用 dd 向 sdwirec 卡中写数据的参数，可灵活定制
test_config = "./tests/bianbu_test.toml" # 指定该板该系统需执行的测试集路径
auto_login = true
username = "root"
password = "bianbu" # 登录凭据
login_prompts = ["login:", "用户名：", "Username:", "用户名:"] # 用于判定进入登录阶段的提示字符串
password_prompts = ["Password:", "密码：", "Secret:"]
shell_prompt = "root@k1:~#" # 用于判定可进入 shell 阶段的提示字符串
```

测试集配置 (tests/bianbu_test.toml) 示例：

```toml
tests = [
    {name = "uname_test", command = "uname -a", expected_output = "Linux", method = "contains", timeout = 10},
    {name = "os_release_test", command = "cat /etc/os-release", expected_output = "Bianbu", method = "contains", timeout = 10},
    {name = "cpu_info_test", command = "cat /proc/cpuinfo", expected_output = "processor", method = "contains", timeout = 10},
    {name = "memory_info_test", command = "cat /proc/meminfo", expected_output = "MemTotal", method = "contains", timeout = 10},
    {name = "disk_usage_test", command = "df -h", expected_output = "/dev", method = "contains", timeout = 10}
] # 执行命令并检查输出中是否包含预期的字符串。也可配置为判定返回值、Special Judge 方式。
```

### 仓库地址

https://github.com/255doesnotexist/boardtest

## Demo 调研

### 预计结果

寻找一些能利用到硬件特性的 Demo、一些有趣的 Demo，给出教学实操文档。

### 目前进度

BananaPi BPI-F3 上硬件 RVV 1.0 加速相关的 Demo 搜集了一些。

### 仓库地址

https://github.com/255doesnotexist/bpi-f3_demos