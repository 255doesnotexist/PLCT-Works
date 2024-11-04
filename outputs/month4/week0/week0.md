## week 0 (1028 - 1103)

### 1. 为 lintestor 加入了 fedora 系的测试脚本。
    - [fedora 测试脚本初始提交](https://github.com/255doesnotexist/lintestor/commit/0977b319bf0b2bd6c1ed192ec6c4ac42baea7a4b)
    - 通过对 debian 的脚本稍加修改适配的方式创建。
    - 包的 metadata 元数据脚本也已经迁移。
    - 包含以下软件包的测试：
        - apache
        - example（示例也迁移了）
        - libmemcached
        - nodejs
        - perl
        - runc
        - varnish
        - clang
        - gcc
        - lighttpd
        - numpy
        - postgresql
        - rust
        - zookeeper
        - cmake
        - gdb
        - llvm
        - ocaml
        - python
        - scipy
        - docker
        - golang
        - mariadb
        - openjdk
        - redis
        - sqlite
        - erlang
        - haproxy
        - nginx
        - openssl
        - ruby
        - squid

### 2. 修缮了 boardtest server 原本不够完善的几个接口。

boardtest server 之前的接口设计：

仅有一个 ```POST /start_test```，靠 ws socket 实时回传 log。

[修缮后的接口设计](https://github.com/255doesnotexist/boardtest/commit/c5a823d4c7ce2cb4881ded1c5b5a63f00981933b)，可以控制的参数更多些，也不用一直维持 ws socket 长连接了：

1. 创建测试: `POST /create_test` 
    - 创建新的测试实例，需提供认证令牌和测试命令行参数。
2. 启动测试: `POST /start_test/{test_id}` 
    - 启动指定ID的测试，需提供认证令牌。
3. 获取测试状态: `GET /test_status/{test_id}` 
    - 查询指定测试的当前状态。
4. 获取测试的差分输出: `GET /test_output/{test_id}` 
    - 获取测试的输出内容，需提供已获取的输出长度。
5. 停止测试: `POST /stop_test/{test_id}` 
    - 停止正在运行的测试，需提供认证令牌。

所有需要认证的端点都使用 secret.token 文件中的令牌进行验证。

### 3. 米家 SDK 控制设备上下电的调研：

1. **必须先获取小米token和设备IP**：首先要获取小米账号的token以及智能插座的IP地址和token。用Xiaomi-cloud-tokens-extractor工具就可以，具体步骤如下：
   - 安装必要的库：`pip3 install pycryptodome pybase64 requests`
   - 克隆Xiaomi-cloud-tokens-extractor项目：`git clone https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor`
   - 进入项目目录：`cd Xiaomi-cloud-tokens-extractor`
   - 运行token提取脚本：`python3 token_extractor.py`

2. **控制插座**：确保插座和控制设备在同一个局域网内（heartland 确实是在一起），使用`python-miio`库来控制插座。首先安装`python-miio`库：
   - `pip3 install python-miio`
   - `apt-get install libffi-dev libssl-dev`

3. **获取设备信息**：使用`miiocli`工具获取设备信息。
   - `miiocli device --ip IP --token TOKEN info`

4. **获取插座状态**：通过以下命令获取插座的当前状态。
   - `miiocli -d device --ip YOUR_DEVICE_IP --token YOUR_DEVICE_TOKEN raw_command get_properties "[{'did': 'MYDID', 'siid': 2, 'piid': 1 }]"`

5. **开启插座**：使用以下命令开启插座。
   - `miiocli -d device --ip YOUR_DEVICE_IP --token YOUR_DEVICE_TOKEN raw_command set_properties "[{'did': 'MYDID', 'siid': 2, 'piid': 1, 'value':True}]"`

6. **关闭插座**：使用以下命令关闭插座。
   - `miiocli -d device --ip YOUR_DEVICE_IP --token YOUR_DEVICE_TOKEN raw_command set_properties "[{'did': 'MYDID', 'siid': 2, 'piid': 1, 'value':False}]"`

boardtest 正好是个 python 项目，可以试试刷写、测试前后加上自动上下电功能。

问题：token 会不会经常过期。。目前没试过还不知道