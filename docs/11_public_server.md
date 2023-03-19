# 开外网

## 1 基础篇
### 服务端
1. 修改 `conf/char_athena.conf` 文件里的 `char_ip` 为服务器的公网IP
2. 修改 `conf/map_athena.conf` 文件里的 `map_ip` 为服务器的公网IP

### 客户端
1. 修改 `data/clientinfo.xml` 里的 `address` 为服务器的公网IP

以下为可选步骤，用于修改客户端的显示名称和注册地址
1. 修改 `data/clientinfo.xml` 里的 `display` 为你想展示给玩家的服务器名字
2. 修改 `data/clientinfo.xml` 里的 `registrationweb` 为你的服务器的账号注册网站地址

## 2 安全篇
既然对外开服了，就不得不考虑安全性问题。为了防止被人恶意攻击，我们需要做一些改动。

### 2.1 修改服务端进程内部通讯的账号密码
默认使用的是 s1 和 p1，如果有人知道了我们服务器IP和端口，就可以通过默认密码和我们的服务器通讯，进而篡改我们服务器的数据。因此我们需要修改为自己的账号密码。

修改方法：
1. 修改 `conf/map_athena.conf` 里的 `userid` 和 `passwd` 为自己的账号密码。注意账号密码的强度要足够高。
2. 修改 MySQL 里 `login` 表里 `account_id` 为1的账号的 `userid` 和 `user_pass` 为自己的账号密码。

### 2.2 修改服务器端口
对外暴露的端口总共有3个，分别是 `login_port`、`char_port` 和 `map_port`。默认使用的是 6900、6121 和 5121，我们需要修改为自己的端口。
虽然通过抓包也能分析出服务器的端口，但这样能避免被端口扫描工具扫描到，毕竟互联网上那么多服务器，不是谁都能知道你在开服的，但如果使用默认端口，别人一下就能扫出来。

服务端修改：
1. 修改 `conf/login_athena.conf` 里的 `login_port` 为自己的端口
2. 修改 `conf/char_athena.conf` 里的 `char_port` 为自己的端口
3. 修改 `conf/map_athena.conf` 里的 `map_port` 为自己的端口

客户端修改：
1. 修改 `data/clientinfo.xml` 里的 `port` 为自己的端口

### 2.3 修改封包加密密钥
服务端修改：
1. 修改 `src/map/clif_obfuscation.hpp` 里对应版本的 `packet_keys`。

客户端修改：
1. 下载并安装 [Nemo](https://gitlab.com/4144/Nemo)。
2. 选择一个要修改的客户端版本，下载其主程序并使用Nemo加载。
3. 点击 `Enable packets id encryption`，在弹出的窗口中修改3个Key。
4. 确保 `Disable packets id encryption` 处于未选中状态。

### 2.4 客户端加壳
加壳工具有很多，大家可以自行选择。
推荐一个我使用过的觉得不错的加壳工具：[Themida](https://www.cheatengine.org/)。
