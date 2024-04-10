# DNS、DDNS 相关

# 常用 DNS

Cloudflare DNS 1.1.1.1 自推出以来一直是全球最快的公共 DNS 之一，根据 DNSPerf 的数据，1.1.1.1 在 2020 年 3 月测得的全球平均响应表现排名第一。

# 设置 DNS

LINUX DNS 解析的 3 种修改方法

## 1.HOST 本地 DNS 解析

`/etc/hosts` 是一个本地计算机用于存储主机名与 IP 地址映射的文件，系统在解析域名时会首先查询这个文件。

- 打开 `/etc/hosts` 文件，在文件中添加或修改条目，格式如下：

```bash
127.0.0.1     localhost 
192.168.1.10  example.local
```

- 每行的第一部分是 IP 地址，第二部分是对应的主机名。你可以添加任何需要直接解析到特定 IP 的主机名。

## 2.网卡配置文件 DNS 服务地址

vi /etc/sysconfig/network-scripts/ifcfg-eth0

添加规则 例如:

DSN1=’114.114.114.114’

## 3.修改 `/etc/resolv.conf` 文件

传统的方法是直接编辑 `/etc/resolv.conf` 文件，手动添加 DNS 服务器的地址。例如，要使用 Google 的 DNS，可以添加如下行：

```bash
nameserver 8.8.8.8 
nameserver 8.8.4.4
```

#### 注意点：

- 临时性：在很多现代的 Linux 发行版中，`/etc/resolv.conf` 可能会被网络管理服务（如 `NetworkManager` 或 `systemd-resolved`）自动管理和覆盖，所以对它的直接修改可能会在重启网络服务或系统后失效。
- 安全性：确保 DNS 服务器来源可靠，避免 DNS 污染或重定向攻击。
