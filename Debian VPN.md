#### Debian 系统下搭建 VPN 服务 和 Ubuntu 下应用
---
时间： 2016年01月17日

说明： 转载 [Debian 操作系统架设 VPN 服务器图文教程](http://www.tofree.net/posts/237.html)

1 安装 pptpd 服务
```
  sudo apt-get install pptpd
```
2 配置 pptpd
```
  编辑 /etc/pptpd.conf 文件
    sudo vi /etc/pptpd.conf 将下面命令前 # 去掉
    #localip 192.168.0.1 
    #remoteip 192.168.0.234-238,192.168.10.245
```
3 配置 DNS
```
  编辑 /etc/ppp/options 文件
    sudo vi /etc/ppp/options 加入下面 2 行命令
    ms-dns 8.8.8.8 
    ms-dns 8.8.4.4
    注： 该 dns 为 google 提供的 dns 地址，因此 vpn 连接时会通过 google 去访问相关页面。
```
4 开启IP转发
```
  编辑 /etc/sysctl.conf 文件
    sudo /etc/sysctl.conf  去掉下面代码前的 #
    net.ipv4.ip_forward=1
```
5 添加VPN用户名密码
```
  编辑 /etc/ppp/chap-secrets 文件
    sudo /etc/ppp/chap-secrets 输入符合下面格式的 vpn 账号和密码
    用户名 pptpd 密码 *
    例如： xingliu pptpd 12345678 *
```
6 制作转发脚本
```
  把转发规则写成文件，执行命令：vi /etc/pptpdfirewall.sh 然后内容输入：
  sudo /sbin/iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -j SNAT --to-source 你的VPS公网IP 
  sudo /sbin/iptables -A FORWARD -s 192.168.0.0/24 -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j TCPMSS --set-mss 1356
```
7 设置文件权限
```
  chmod 755 /etc/pptpdfirewall.sh
```
8 设置开机自启动
```
  编辑 /etc/init.d/rc.local ，在最后一行加入下面代码：
  sh /etc/pptpdfirewall.sh
  注： pptpdfirewall.sh 文件路径和 rc.local 文件中执行的路径保持一致。
```
9 重启 VPS
```
  sudo reboot
```
10 应用
```
  因为 ubuntu 系统提供 vpn 连接服务，所以配置 vpn 账号就可以使用。
  10.1 步骤
    打开 System Setting --> NetWork 点击左下角 + 选择 VPN --> create --> pptp --> create
  10.2 配置
    Gateway  vps 公网 ip
    optional （在 vps 中填入的 vpn 用户和密码）
      username xingliu
      password 12345678
    点击 save 在右上角 网络 图标出点击选择 vpn
  10.3 调整
    在 10.2 步中，最后提示 vpn 连接失败，所以需要修改 vpn 配置，打开 vpn 配置窗口选择 Advanced 取消勾选 PAP CHAP EAP 选中
    Use Point-to-Point encryption(MPPE) 点击 OK --> Save 重新连接 vpn，此时会提示 vpn 登陆成功,然后在终端中可以尝试 
    ping google.com 会发现有数据响应。
```