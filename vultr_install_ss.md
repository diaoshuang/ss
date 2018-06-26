
##vultr VPS的购买及搭建ss介绍，支持锐速加速优化


### 1 购买vultr主机

#### 1.1 Vultr简介

Vultr虽然成立时间不久，但是其背景实力还是比较雄厚的，基于全球最大的游戏服务器提供商之一的基础，所以才有实力开设这么多的数据中心。有速度较好的日本东京、洛杉矶等机房，也有我们很多人需要的欧洲机房等15个数据中心。Vultr采用小时计费，可以任意的删除和开通机器

![Vultr](https://images2017.cnblogs.com/blog/1044995/201801/1044995-20180103181821831-235661580.png)
ssh 连接vultr主机：

```
ssh root@108.61.142.103
```

输入主机密码

获取一键安装脚本

```

wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/shadowsocks-libev.sh && bash shadowsocks-libev.sh

```

按照下图输入ss的密码，端口，加密方式，最后回车进入安装


#==========================================================#
# One Click Install Shadowsocks Server for CentOS & Debian #
# Github: https://github.com/uxh/shadowsocks_bash          #
# Thanks: https://github.com/teddysun/shadowsocks_install  #
#==========================================================#
Please Enter Shadowsocks's Password
(Default: Number123890):
 
安装成功：

Congratulations, Shadowsocks-libev server install completed!
------------------------------------------------------------
Your Server IP        :  108.61.142.103 
Your Server Port      :  5832 
Your Password         :  Camelot!
Your Encryption Method:  aes-256-cfb 
------------------------------------------------------------
ss://YWVzLTI1Ni1jZmI6Q2FtZWxvdCExMjNAMTA4LjYxLjE0Mi4xMDM6NTgzMg==

[root@vultr ~]#
