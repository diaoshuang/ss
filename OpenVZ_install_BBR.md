
### 搬瓦工OpenVZ 平台 Google BBR 一键安装脚本

最近很多朋友在找搬瓦工OpenVZ 平台安装谷歌BBR的使用方法，经过多个脚本的比较测试，选择了这个一键脚本来安装谷歌BBR。经多位网友测试网络速度有大幅度的提升。Google BBR是谷歌公司提出的一个开源TCP拥塞控制的算法。在最新的linux 4.9及以上的内核版本中已被采用。目前不建议购买OpenVZ操作系统的VPS,KVM架构更适合国内用户使用。购买参考：搬瓦工VPS19.99刀KVM不定期上货

使用方法

已测试通过的系统： Ubuntu 14.04 x64、Ubuntu 16.04 x64、CentOS 6 x64、CentOS 7 x64、 debian-8.0-x86_64只支持 64 位系统，要求 glibc 版本 2.14 以上。 建议选择debian-8.0-x86_64
```
wget https://raw.githubusercontent.com/kuoruan/shell-scripts/master/ovz-bbr/ovz-bbr-installer.sh
chmod +x ovz-bbr-installer.sh
./ovz-bbr-installer.sh
```
需要配置的有如下几个选项：

1.需要加速的端口，即 SS 端口。加速开启之后，流量会先经过 BBR 处理，之后再发送给后端的 SS。

2.可能需要配置 “公网接口名称”，即你服务器上具有公网 IP 的接口名称。搬瓦工 OpenVZ 上默认都是 venet0，但是有朋友可能需要安装在其他服务器上，所以我加入了此选项。

需要注意的是，在有 firewalld 的服务器上安装的时候，firewalld 会干扰 iptables 的规则，造成网络不通（现在具体原因未知，谁有解决方案可以提示一下）。所以在装有 firewalld 的服务器上需要先退出 firewalld：

这个步骤搬瓦工不需要配置
```
systemctl stop firewalld
```
如需卸载，请使用：
```
./ovz-bbr-installer.sh uninstall
```
 

多端口加速

安装的时候只配置了一个加速端口，但是你可以配置多端口加速，配置方法非常简单。 修改文件
```
vi /usr/local/haproxy-lkl/etc/port-rules
```
在文件里添加需要加速的端口，每行一条，可以配置单个端口或者端口范围，以 # 开头的行将被忽略。 例如：8800 或者 8800-8810 配置完成之后，只需要重启 haproxy-lkl 即可。

注： 最初版本的实现是需要再开一个新端口，后来经人提醒，我又看了一下 HAproxy 的配置说明，可以直接代理后端端口，不必再开新端口。请注意，使用该方法后，如果 HAproxy 进程异常退出，会造成无法连接原有端口。所以，请确保在退出 HAproxy 时是通过命令正常退出的，在退出时会自动清理原有的防火墙规则。

使用 systemctl 或者 service 命令来启动、停止和重启 HAporxy-lkl：
```
systemctl {start|stop|restart} haproxy-lkl
service haproxy-lkl {start|stop|restart}
```
/usr/local/haproxy-lkl/etc/haproxy.cfg 这个文件是通过 port-rules 自动生成的，每次启动都会重新生成，所以直接修改它的配置没用。 如果想要自定义配置，请修改启动文件：

/usr/local/haproxy-lkl/sbin/haproxy-lkl

更新 glibc

CentOS 6 更新 glibc，首先下载如下几个文件：
```
wget http://ftp.redsleeve.org/pub/steam/glibc-2.15-60.el6.x86_64.rpm \
http://ftp.redsleeve.org/pub/steam/glibc-common-2.15-60.el6.x86_64.rpm \
http://ftp.redsleeve.org/pub/steam/glibc-devel-2.15-60.el6.x86_64.rpm \
http://ftp.redsleeve.org/pub/steam/glibc-headers-2.15-60.el6.x86_64.rpm \
http://ftp.redsleeve.org/pub/steam/nscd-2.15-60.el6.x86_64.rpm
```
然后安装：
```
# rpm -Uvh glibc-2.15-60.el6.x86_64.rpm \
glibc-common-2.15-60.el6.x86_64.rpm \
glibc-devel-2.15-60.el6.x86_64.rpm \
glibc-headers-2.15-60.el6.x86_64.rpm \
nscd-2.15-60.el6.x86_64.rpm
```
如果以上步骤无法更新，可以手动编译更新（来自网友的方法）

先安装gcc
```
yum install -y gcc-c++
```

下载编译安装
```
wget http://ftp.gnu.org/gnu/glibc/glibc-2.15.tar.gz
wget http://ftp.gnu.org/gnu/glibc/glibc-ports-2.15.tar.gz
tar -zxf glibc-2.15.tar.gz
tar -zxf glibc-ports-2.15.tar.gz
mv glibc-ports-2.15 glibc-2.15/ports
mkdir glibc-build-2.15
cd glibc-build-2.15
../glibc-2.15/configure --prefix=/usr --disable-profile --enable-add-ons --with-headers=/usr/include --with-binutils=/usr/bin
make all && make install
```

检查一下：
```
# ldd --version
ldd (GNU libc) 2.15
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.??There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
```
已经升级到 glibc 2.15 了。

判断 BBR 已正常工作

判断 bbr 是否正常启动可以尝试 ping 10.0.0.2，如果能通，说明 bbr 已经启动。

然后检查 iptables 规则
```
iptables -t nat -nL
Chain PREROUTING (policy ACCEPT)
target prot opt source  destination
LKL_IN  all -- 0.0.0.0/0 0.0.0.0/0
Chain POSTROUTING (policy ACCEPT)
target  prot opt source  destination
Chain OUTPUT (policy ACCEPT)
target  prot opt source  destination
Chain LKL_IN (1 references)
target  prot opt source  destination
DNAT  tcp -- 0.0.0.0/0 0.0.0.0/0 tcp dpt:8989 to:10.0.0.2
```
里边会看到多了一张链表 LKL_IN，里边有相应的端口规则。

另外建议添加定时重启，测试打开视频网页如遇到速度慢，直接刷新或者下一视频即可

参考链接:[搬瓦工OpenVZ 平台 Google BBR 一键安装脚本](https://www.bawagon.com/openvz-google-bbr/)
