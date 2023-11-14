# **更新内容**
- **添加 Multiplex (多路复用)、TCP Brutal (拥塞控制算法)、ECH (TLS 扩展)配置；若要启用 Multiplex、TCP Brutal，请使用1.7.0以上的 sing-box 内核，请在服务端自行安装 TCP Brutal。**
- **添加对 Juicity 节点链接生成的支持。**
- **添加对 HTTP 协议的支持。**
- **其它优化与修复。**

<details>
 <summary><span style="font-size: 24px; font-weight: bold;">更新内容</span></summary>
  
- **添加 Multiplex (多路复用)、TCP Brutal (拥塞控制算法)、ECH (TLS 扩展)配置；若要启用 Multiplex、TCP Brutal，请使用1.7.0以上的 sing-box 内核，请在服务端自行安装 TCP Brutal。**
- **添加对 Juicity 节点链接生成的支持。**
- **添加对 HTTP 协议的支持。**
- **其它优化与修复。**

</details>



# **说明**
- **脚本使用sing-box、Juicity内核。**
- **脚本支持 CentOS 8+、Debian 10+、Ubuntu 20+ 操作系统。**
- **脚本所有协议均支持自签证书（NaiveProxy除外）。**
- **脚本支持多用户。**
- **脚本支持所有协议共存。**
- **脚本支持自动续签证书。**
- **脚本支持 Multiplex、TCP Brutal、ECH 配置。**

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
wget -N -O /root/singbox.sh https://raw.githubusercontent.com/TinrLin/sing-box/main/Install.sh && chmod +x /root/singbox.sh && ln -sf /root/singbox.sh /usr/local/bin/singbox && bash /root/singbox.sh
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
- **VLESS+Vision+REALITY**
- **VLESS+H2C+REALITY**
- **VLESS+gRPC+REALITY**
- **Direct--sing-box版任意门**
- **Trojan+TCP**
- **Trojan+WebSocket**
- **Trojan+gRPC**
- **Trojan+TCP+TLS**
- **Trojan+H2C+TLS**
- **Trojan+gRPC+TLS**
- **Trojan+WebSocket+TLS**
- **Hysteria**
- **ShadowTLS V3**
- **NaiveProxy**
- **Shadowsocks**
- **VMess+TCP**
- **VMess+WebSocket**
- **VMess+gRPC**   
- **VMess+TCP+TLS**
- **VMess+WebSocket+TLS** 
- **VMess+H2C+TLS**
- **VMess+gRPC+TLS** 
