
## [vultr](https://www.vultr.com/?ref=7236384) VPS的购买及搭建ss介绍，支持锐速加速优化


### 1 [购买vultr主机](https://www.vultr.com/?ref=7236384)

#### 1.1 Vultr简介

Vultr虽然成立时间不久，但是其背景实力还是比较雄厚的，基于全球最大的游戏服务器提供商之一的基础，所以才有实力开设这么多的数据中心。有速度较好的日本东京、洛杉矶等机房，也有我们很多人需要的欧洲机房等15个数据中心。Vultr采用小时计费，可以任意的删除和开通机器

![Vultr](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103181821831-235661580.png)

#### 1.2 注册

新用户注册 [vultr官网](https://www.vultr.com/?ref=7236384)，跳转到下图位置

![注册](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182220503-1647212316.png)

填写邮件地址、需要设置的密码（包括大写、小写字母和数字），点击Create即可

#### 1.3 新用户验证

注册后我们会收到一封vultr验证的邮件，我们点击相应的链接验证下即可。这一步一定要做，不然后面会出现问题

#### 1.4 新用户激活

验证并登陆后我们会跳转到充值界面，按照下图指示进行即可

![激活](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182244706-925891540.png)

#### 1.5 新机器创建

激活之后我们点界面右上角的那个圆形的蓝色加号。
1、首先是选择机器的位置，这里大家就按照自己的需要进行选择了，推荐的是东京（联通）、阿姆斯特丹（电信）、新加坡（移动）。但是也不能说绝对是这样，大家还是逐个位置进行测试，选择一个最好的。看不懂的地名就百度一下就好了

![创建机器](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182308237-568652507.png)

2、然后是系统类型，这里我们需要用到Debian里边的7 x64，所以选择这个就对了
![系统类型](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182325909-374897141.png)

3、接着是每个月的花费，我们选最低的那个$5/mo就好了，有2.5的就选2.5
![花费](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182346128-615390028.png)

4、其他的不需要更改，点击右下角的那个蓝色按钮就可以啦

![部署](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182358378-1112887794.png)

接着上面第4步，等待大概5分钟，然后进入机器详情页，一些信息我都给大家在下图中表示出来了

![机器详情](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103182421299-1951797957.png)


### 2 搭建ss

vps主机购买好之后，就可以搭建shadowsocks

#### 2.1 终端连接vps主机

ssh 连接vultr主机：

```
ssh root@108.61.142.103
```
输入主机密码，回车连接成功

![连接vps](https://images2018.cnblogs.com/blog/1044995/201806/1044995-20180626114646324-1418172715.png)





#### 2.2获取一键安装脚本

```
wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/shadowsocks-libev.sh && bash shadowsocks-libev.sh

```
![脚本](https://images2018.cnblogs.com/blog/1044995/201806/1044995-20180626104654121-812242597.png)


回车后系统会自行下载脚本文件并运行 按照下图输入ss的密码，端口，加密方式，最后回车继续

![配置](https://images2018.cnblogs.com/blog/1044995/201806/1044995-20180626104829134-662917483.png)

安装完成后会出现下图所示界面。根据图中指示，我们将红框圈中的信息保存到记事本内

![信息](https://images2018.cnblogs.com/blog/1044995/201806/1044995-20180626104850862-1308489913.png)

现在打开ss客户端，输入上面的服务器IP，端口，密码，加密方式就可以科学上网了

### 3安装TCP加速软件

前面虽然已经搭建好了 SS，但是因为服务器位于国外，连接速度会较慢，所以我们非常必要在服务器上安装 TCP 加速软件来提速。一般大家常用的 TCP 加速软件有锐速和 Google BBR 拥塞控制算法。

PS：两者不能同时安装，大家根据自己的喜好选择其中一个安装即可！

1、安装锐速请使用[《Vultr 专用破解版锐速一键安装脚本》](https://www.vultrcn.com/7.html)进行。（推荐这个）

2、安装 BBR 请按照[《一键安装原版 & 魔改版 Google BBR 拥塞控制算法教程》](https://www.vultrcn.com/5.html)进行


### 4获取一键安装脚本
Windows 客户端：[点击下载](https://www.vultrcn.com/goto/?url=aHR0cHM6Ly9jdXJscy5mdW4vU2hhZG93c29ja3MvU2hhZG93c29ja3MtV2luZG93cy00LjAuOS56aXA=)；Macbook 客户端：[点击下载](https://www.vultrcn.com/goto/?url=aHR0cHM6Ly9jdXJscy5mdW4vU2hhZG93c29ja3MvU2hhZG93c29ja3MtTWFjT1MtMi42LjMuemlw)；Android 客户端：[点击下载](https://www.vultrcn.com/goto/?url=aHR0cHM6Ly9jdXJscy5mdW4vU2hhZG93c29ja3MvU2hhZG93c29ja3MtQW5kcm9pZC00LjUuMS5hcGs=)；

iPhone/iPad 客户端：请通过 PP 助手安装 Shadowrocket，商店内同名应用为盗版。

Windows 客户端若无法运行则请先安装 NET4.6.2 软件：[点击下载](https://www.vultrcn.com/goto/?url=aHR0cHM6Ly9jdXJscy5mdW4vU2hhZG93c29ja3MvTmV0LVdpbmRvd3MtNC42LjIuemlw)

### 5修改Shadowsocks连接信息
有时我们搭建完成后想要修改 ShadowsocksR 的连接信息，比如密码、端口等。我们可以使用下面的命令直接修改 ShadowsocksR 的连接信息而无需耗费时间重新搭建。
```
wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/shadowsocks-libev.sh && bash shadowsocks-libev.sh modify
```
运行命令后重新输入 Shadowsocks 的各项连接信息，然后使用新的连接信息进行连接即可


