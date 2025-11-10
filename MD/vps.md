# 新机到手

## Hysteria2搭建

1. 系统组件升级至最新：

​	`apt update -y && apt install -y curl && apt install -y socat`

2. Hysteria 2 一键安装脚本

​	`wget -N --no-check-certificate https://raw.githubusercontent.com/flame1ce/hysteria2-install/main/hysteria2-install-main/hy2/hysteria.sh && bash hysteria.sh`

3. 查看 hysteria 服务 状态

​	`systemctl status hysteria-server.service`

4. 启动 hysteria 服务

`	systemctl start hysteria-server.service`

5. 设置 hysteria 服务 开机自启

​	`systemctl enable hysteria-server.service`

6. 停止 hysteria 服务

​	`systemctl stop hysteria-server.service`

7. 重启 hysteria 服务

​	`systemctl restart hysteria-server.service`
三、开放端口

节点如果不能正常使用，请先放行端口，
将下面的命令复制, 粘贴后敲回车.
注意: 80和443一定要开放, 另外, 再将 xxx 改为你自己的hysterial监听端口。

`iptables -I INPUT -p tcp --dport 80 -j ACCEPT`
`iptables -I INPUT -p tcp --dport 443 -j ACCEPT`
`iptables -I INPUT -p tcp --dport xxx -j ACCEPT`



开放所有端口

`ufw disable`

# 一键脚本

```bash
一、安装基础组件
# Debian/Ubuntu
apt update -y  && apt install -y curl

# CentOS/RedHat/Fedora/AlmaLinux/Rocky Linux
yum update && yum install -y curl

# CentOS/RedHat/Fedora/AlmaLinux/Rocky Linux
apk update && apk add curl

二、运行脚本
bash <(curl -sL kejilion.sh)
```

**其他脚本**

```bash
# 三网回程路由检测脚本
curl https://raw.githubusercontent.com/zhanghanyun/backtrace/main/install.sh -sSf | sh

# 解锁流媒体测试脚本
sudo apt install curl openssl ca-certificates -yq #安装依赖
bash  <( curl -L -s check.unlock.media)

# 下面4条命令任何一个都可以测试VPS的性能
# Github 开源地址：https://github.com/Aniverse/A
bash <(wget -qO- git.io/ceshi)
bash <(curl -Ls git.io/ceshi)
bash -c "$(wget -qO- https://github.com/Aniverse/A/raw/i/a)"
wget -q https://github.com/Aniverse/A/raw/i/a && bash a

# bench.sh：一键 VPS 性能测试脚本（下行网络 & 磁盘 IO）
# bench.sh 是秋水逸冰（teddysun）编写的 VPS 测试脚本，适用于几乎所有主流Linux 发行版。脚本集成了系统信息、全球多点下行测速、IPv6 支持，以及三轮磁盘 IO 测试并取均值。
wget -qO- bench.sh | bash

# 开启BBR加速
bash <(curl -Lso- https://github.com/teddysun/across/raw/master/bbr.sh)

# IP质量检测
bash <(curl -Ls IP.Check.Place)
```



## 安装wordpress

```bash
# 关闭防火墙/设置防火墙规则
ufw disable

# 更新系统
apt update -y  && apt upgrade -y

# 1Panel一键安装脚本
curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh

安装应用：OpenResty、MySQL、Redis、PHP8
# 安装主题显示要ftp，在wp-config中加入下列代码
define("FS_METHOD", "direct");
define("FS_CHMOD_DIR", 0777);
define("FS_CHMOD_FILE", 0777);
```

