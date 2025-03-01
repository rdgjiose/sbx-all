# **更新内容**
- **V 1.2**
- **客户端配置文件添加Clash API支持。**
- **其它优化与修复。**

<details>
   <summary><b>历史更新内容</b></summary>

- **V 1.1**
- **修改客户端配置文件DNS配置部分。**

<br>

- **V 1.1-beta.3**
- **添加 HTTPUpgrade 传输层。**

<br>

- **V 1.1-beta.2**
- **修复自动更新证书问题。**
- **修复Cron检测规则。**

<br>

- **V 1.1-beta.1** 
- **添加 Multiplex (多路复用)、TCP Brutal (拥塞控制算法)、ECH (TLS 扩展)配置；若要启用 Multiplex、TCP Brutal，请使用1.7.0以上的 sing-box 内核，请在服务端自行安装 TCP Brutal。**
- **添加对 Juicity 节点链接生成的支持。**
- **添加对 HTTP 协议的支持。**
- **其它优化与修复。**

<br>

- **V 1.0** 
- **添加 WireGuard 解锁 YouTube 选项。**
- **添加节点管理选项，支持删除任意节点的配置，包括服务端与客户端配置文件。**
- **删除节点配置仅支持Version：1.0及之后的版本。**
- **其它优化与修复。**  
</details>

# **说明**
- **脚本使用sing-box、Juicity内核。**
- **脚本支持 CentOS 8+、Debian 10+、Ubuntu 20+ 操作系统。**
- **脚本所有协议均支持自签证书（NaiveProxy除外）。**
- **脚本支持多用户。**
- **脚本支持所有协议共存。**
- **脚本支持自签100年证书。**
- **脚本支持自动续签证书。**
- **脚本支持HTTP、WebSocket、gRPC、HTTPUpgrade传输协议。**
- **脚本支持 Multiplex、TCP Brutal、ECH 配置；若要启用 Multiplex、TCP Brutal，sing-box 内核需 ≥1.7.0，请在服务端自行安装 TCP Brutal。**
- **由于 Clash 不支持 TCP Brutal、ECH 配置，如果启用这些配置将不会自动生成 Clash 配置文件。**

# **安装**
- **Debian&&Ubuntu使用以下命令安装依赖**
```
apt update && apt -y install curl wget tar socat jq git openssl uuid-runtime build-essential zlib1g-dev libssl-dev libevent-dev dnsutils cron
```
- **CentOS使用以下命令安装依赖**
```
yum update && yum -y install curl wget tar socat jq git openssl util-linux gcc-c++ zlib-devel openssl-devel libevent-devel bind-utils cronie
```
- **使用以下命令运行脚本**
```
wget -N -O /root/singbox.sh https://raw.githubusercontent.com/rdgjiose/sbx-all/main/Install.sh && chmod +x /root/singbox.sh && ln -sf /root/singbox.sh /usr/local/bin/singbox && bash /root/singbox.sh
```

# **使用方法**
- **Clash客户端配置文件位于/usr/local/etc/sing-box/clash.yaml，下载后加载到 Clash 客户端即可使用，需要配合 Meta 内核。**
- **sing-box电脑端配置文件位于/usr/local/etc/sing-box/win_client.json，下载后加载到 V2rayN、SFM 客户端即可使用。**
- **sing-box手机端配置文件位于/usr/local/etc/sing-box/phone_client.json，下载后加载到 SFA、SFI 客户端即可使用。**

# **脚本支持的节点类型**
- **SOCKS**
- **HTTP**
- **TUIC V5**
- **Juicity**
- **WireGuard--解锁 ChatGPT、Netflix、Disney+**
- **Hysteria2**
- **VLESS+TCP**
- **VLESS+WebSocket**
- **VLESS+gRPC**
- **VLESS+HTTPUpgrade**
- **VLESS+Vision+REALITY**
- **VLESS+H2C+REALITY**
- **VLESS+gRPC+REALITY**
- **Direct--sing-box版任意门**
- **Trojan+TCP**
- **Trojan+WebSocket**
- **Trojan+gRPC**
- **Trojan+HTTPUpgrade**
- **Trojan+TCP+TLS**
- **Trojan+H2C+TLS**
- **Trojan+gRPC+TLS**
- **Trojan+WebSocket+TLS**
- **Trojan+HTTPUpgrade+TLS**
- **Hysteria**
- **ShadowTLS V3**
- **NaiveProxy**
- **Shadowsocks**
- **VMess+TCP**
- **VMess+WebSocket**
- **VMess+gRPC**
- **VMess+HTTPUpgrade**   
- **VMess+TCP+TLS**
- **VMess+WebSocket+TLS** 
- **VMess+H2C+TLS**
- **VMess+gRPC+TLS** 
- **VMess+HTTPUpgrade+TLS** 

##########################################端口跳跃方法###########################################################
# Debian&&Ubuntu

## 安装iptables-persistent
```
apt install iptables-persistent
```
## 清空默认规则
```
iptables -F
```
## 清空自定义规则
```
iptables -X
```
## 允许本地访问
iptables -A INPUT -i lo -j ACCEPT

## 开放SSH端口（假设SSH端口为22）
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

## 开放HTTP端口
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

## 开放UDP端口（10010替换为节点的监听端口）
iptables -A INPUT -p udp --dport 10010 -j ACCEPT

## 开放UDP端口范围（假设UDP端口范围为20000-40000）
iptables -A INPUT -p udp --dport 20000:40000 -j ACCEPT

## 允许接受本机请求之后的返回数据
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

## 其他入站一律禁止
iptables -P INPUT DROP

## 允许所有出站
iptables -P OUTPUT ACCEPT

## 查看开放的端口
iptables -L

## 添加NAT规则，20000:40000替换为你设置端口跳跃的范围，10010替换为你节点的监听端口
iptables -t nat -A PREROUTING -p udp --dport 20000:40000 -j DNAT --to-destination :10010

## 查看NAT规则
iptables -t nat -nL --line

## 保存iptables规则
netfilter-persistent save
