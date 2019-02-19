# 搬瓦工搭建SS教程

## 附言：[vultr搭建ss教程](https://github.com/wandou911/ss/blob/master/vultr_install_ss.md)

## 前言

作者写在前面的话：

应同学的要求在此分享搬瓦工搭建SS的教程，此教程只作为学习之用，因某些原因本教程不适合长期使用，在大家学习之后请删除所做的操作，谢谢。

ss免费账号分享：http://mnstar.me


关于[搬瓦工](https://bwh1.net/aff.php?aff=19935)（Bandwagonhost）

说起搬瓦工大家应该都不会陌生，搬瓦工是美国主机商IT7旗下的一个便宜VPS托管商，搬瓦工原名Bandwagonhost是国内网民对BandwagonHost的简称，BandwagonHost类似的译音有点像“搬瓦工”，所以国内网民简称“BandwagonHost”为“搬瓦工”。BandwagonHost成立于2004年，也算是一家老牌的主机商。

选择搬瓦工的理由：

1.性价比高（年付$19.99，等于每月只需$1.5就可以搭建自己的SS）

2.稳定性好（目前使用了近4年，从未宕机）

3.YouTube流畅观看（1080P、2K毫无压力，新出的洛杉矶CN2线路在速度方面更是提升了不少）

4.后台一键SS（即便是菜鸟，什么都不懂也能搭建SS，完全小白操作）

5.购买方便（支持：信用卡、paypal、支付宝付款）

搭建SS教程

## 一.购买搬瓦工VPS

首先我们打开：[搬瓦工官网](https://bwh1.net/aff.php?aff=19935)

先不要去注册账号，先选择一个适合自己的VPS，这样的原因是为了跳过注册时的谷歌验证码（因搬瓦工官网采用的是谷歌验证码，所以验证码在国内是不显示的）

 

 

在我们选择好适合自己的VPS后会看到以下界面：
![](http://upload-images.jianshu.io/upload_images/8088606-43e2708a2ea87014.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

选择好付费周期和数据中心后点击“Add to Cart”加入购物车。（注意：单机房方案没有数据中心可选择，只有一个默认的洛杉矶机房）

 ![](http://upload-images.jianshu.io/upload_images/8088606-8c4587452520d35f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


搬瓦工搭建SS教程

输入完搬瓦工VPS优惠码后我们点击“Validate Code”进入下图界面
![](http://upload-images.jianshu.io/upload_images/8088606-0d3a95e3cd154969.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

对于已有搬瓦工账号的网友会跳转至结账页面，对于新用户则会跳转至注册页面（这时注册已经跳过验证码）

需要注意：此时不能够挂代理注册，国家、地区、邮箱必须真实
![email](http://upload-images.jianshu.io/upload_images/8088606-a0ea7400464a804e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

在付款页面我们选择alipay也就是支付宝（也可以选择信用卡和paypal付款）
![pay](http://upload-images.jianshu.io/upload_images/8088606-aed60a2d0b17ce4d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

然后我们登录支付宝，就可以完成本次支付

首先我们要输入支付宝邮箱，然后点击下面的支付宝，系统自动会发送一个验证码到你绑定的手机上，随后输入支付宝所有人的身份证最后五位数字，在支付宝有充足余额下即可完成支付。
![alipay](http://upload-images.jianshu.io/upload_images/8088606-0421c122567d3128.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

下图已经付款成功
![paysuccess](http://upload-images.jianshu.io/upload_images/8088606-9db47bc7c13b78b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

购买成功后我们会收到搬瓦工官方发来的邮件通知，登录我们注册时填写的邮箱即可看到，里面包含了搬瓦工VPS的各项信息，包含密码和端口。在以后每重装一次系统都会给我们发送邮件，大家请注意查收。
## 二. 安装ss服务端
然后登录我们刚刚购买的搬瓦工VPS管理后台

点击：VPS Hosting 之后我们看到如下界面，我们在Services下拉菜单中点击My Services
![myservice](http://upload-images.jianshu.io/upload_images/8088606-2d3a112c1763b7c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



点击My Services之后就会出现我们购买的VPS列表，在VPS列表的后面我们点击KiwiVM Control Panel，如图

![control panel](http://upload-images.jianshu.io/upload_images/8088606-3f85958eecb63361.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
搬瓦工搭建SS教程

点击KiwiVM Control Panel之后我们就进入了搬瓦工的控制面板界面

搬瓦工控制面板左侧是搬瓦工的各项功能选项，控制面板右侧是对应的各项功能界面。

最关键的时刻到了：一键设置ss 如下图

点击控制面板左侧的“Shadowsocks Server”
![shadowsocks server](http://upload-images.jianshu.io/upload_images/8088606-907995a02da90d66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![complete](http://upload-images.jianshu.io/upload_images/8088606-462c661ba007f4eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


设置好以后请记住你的IP 跟协议类型 端口 密码（尽量不要给别人用....）

友情提示：服务端 443 端口已经被屏蔽，请更换为其他端口 445，446 随便选都可以，不然无法访问油管
![port](http://upload-images.jianshu.io/upload_images/8088606-f8a410bd90e9ede9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2019年 搬瓦工没有Shadowsocks Server这个选项了

### 解决方法1
若页面中没有Shadowsocks Server这一项，说明一键搭建SS功能被去掉了，这时候需要在当前浏览器的新标签中打开以下网址：
[https://kiwivm.64clouds.com/main-exec.php?mode=extras_shadowsocks](https://kiwivm.64clouds.com/main-exec.php?mode=extras_shadowsocks)，打开以后就是安装页面，点击页面中的Install Shadowsocks Server安装即可(安装前提是服务器已打开已运行)。

开始安装
![](https://ws3.sinaimg.cn/large/006tKfTcly1g0bql68nc9j30p00jj3zr.jpg)

成功安装后如下：
![](https://ws4.sinaimg.cn/large/006tKfTcly1g0bqmiwnapj30f30brdh9.jpg)

Go Back 后就能看到 shadowsocks 的连接信息了，如下图所示：

![](https://ws2.sinaimg.cn/large/006tKfTcly1g0bqm2m98gj30l008lgm3.jpg)

至此，ss服务器端就配置完成了！

### 解决方法2 命令行手动安装


#### 2.1 终端连接vps主机

ssh 连接vultr主机：

```
ssh root@108.61.142.103 -p 26185
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

备注：wget 时提示 -bash:wget command not found,很明显没有安装wget软件包，输入命令安装wget

```
yum -y install wget
```
wget安装成功后回到步骤2.2

电脑版SS软件下载

![software download](http://upload-images.jianshu.io/upload_images/8088606-52463b1956d35162.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


ss设置 设置好右下角有个小飞机的图标右键启用

PAC模式IP不变，全局代理ip会变成服务器IP

![setup](http://upload-images.jianshu.io/upload_images/8088606-b4a0d1eb9f288ddd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/8088606-0d7be29e3680fc4d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
搬瓦工搭建SS教程

手机版SS设置也是一样
![phone](http://upload-images.jianshu.io/upload_images/8088606-f65895ea7d42fa6c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

搬瓦工搭建SS教程

然后愉快的看油管去吧，1080P、2K测试毫无压力

![youtube](http://upload-images.jianshu.io/upload_images/8088606-e5cb62b4797b25c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
搬瓦工搭建SS教程

备注：如果配置成功不能访问油管，请修改ss的端口

本教程学习成功后请及时删除，本文原创文章如需转载请注明出处，谢谢！

### 相关链接：

1 [vultr ss搭建指南](http://www.cnblogs.com/mnstar/p/8142885.html)

2 [各版本shadowsocks客户端下载地址](https://www.flyzy2005.com/fan-qiang/shadowsocks/ss-clients-download/)

3 [搬瓦工一键搭建 ss 手把手教你搭建自己的 ss 翻墙服务器](https://www.diycode.cc/topics/1247)

4 [https://justmysocks.net/members/index.php](https://justmysocks.net/members/index.php)
