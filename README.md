# OCI

## 适用于 Ubuntu 20.04

Oracle Cloud 控制面板开放端口
ROOT操作

sudo su

处理预设规则，全部端口开放

iptables -D INPUT -j REJECT --reject-with icmp-host-prohibited

iptables -D FORWARD -j REJECT --reject-with icmp-host-prohibited

/etc/init.d/netfilter-persistent save

/etc/init.d/netfilter-persistent reload

开启 BBR 加速并优化 VPS 设置

wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"
chmod +x tcp.sh
./tcp.sh

申请 SSL 证书，更换邮件及解析域名

apt update -y

apt install -y curl

apt install -y socat

curl https://get.acme.sh | sh

~/.acme.sh/acme.sh --register-account -m xxxx@xxxx.xx

~/.acme.sh/acme.sh --issue -d xx.xxxx.xx --standalone

~/.acme.sh/acme.sh --installcert -d xx.xxxx.xx --key-file /root/private.key --fullchain-file /root/cert.crt

安装 x-ui

bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)

填写相应证书

公钥路径：/root/cert.crt

私钥路径：/root/private.key

设置入站列表即可

## 适用于 Oracle Linux 7.9

ROOT操作

sudo su

停止 firewall

systemctl stop firewalld.service
禁止 firewall 开机启动

systemctl disable firewalld.service
更新并安装支持

yum update -y

yum install -y curl

yum install -y socat

申请 SSL 证书，更换邮件及解析域名

curl https://get.acme.sh | sh

~/.acme.sh/acme.sh --register-account -m xxxx@xxxx.xx

~/.acme.sh/acme.sh --issue -d xx.xxxx.xx --standalone

~/.acme.sh/acme.sh --installcert -d xx.xxxx.xx --key-file /root/private.key --fullchain-file /root/cert.crt

安装 x-ui

bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)

填写相应证书

公钥路径：/root/cert.crt

私钥路径：/root/private.key

设置入站列表即可
