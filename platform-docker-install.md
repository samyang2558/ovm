# Docker方式部署

<<<<<<< HEAD
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
=======
<<<<<<< HEAD
>>>>>>> b14068226dd6224c884ee435feb99bd8875c31a3
使用ovm发行版的docker版iso 使用DVD安装

OVM虚拟化的docker发行版采用一键式安装中途需要设置root密码

安装好之后使用admin账户admin密码登录进入Console UI设置ip

![](/assets/Console UI1.png)

设置好ip后就可以使用Bui进行Docker的管理

# 手动桥接br0地址

### 备份eth0 网卡并生成br0网卡

\[root@localhost ~\]\# cd \/etc\/sysconfig\/network-scripts\/

\[root@localhost network-scripts\]\# cp ifcfg-eth0 ifcfg-br0

ifcfg-eth0 改为以下内容

\[root@localhost network-scripts\]\# vim ifcfg-eth0

TYPE="Ethernet"

.DEVICE="eth0"

ONBOOT="yes"

BRIDGE=br0

### Ifcfg-br0 配置

\(Static静态IP指定模式\)

\[root@localhost network-scripts\]\# vim ifcfg-br0

TYPE="Bridge"

DEVICE="br0"

ONBOOT="yes"

BOOTPROTO=static

IPADDR="192.168.8.143"

NETMASK="255.255.255.0"

GATEWAY="192.168.8.2"

\(DHCP动态IP获取模式\)

TYPE=Bridge

DEVICE=br0

ONBOOT=yes

BOOTPROTO=dhcp

### 2、重启网络服务

\[root@localhost network-scripts\]\# service network restart

Restarting network \(via systemctl\): \[ 确定 \]

# 下面简单介绍Bui的功能

1）物理机信息

![](/assets/火狐截图_2016-09-21T03-01-25.093Z.png)

2）容器列表

“+”：添加容器

停止容器\/启动容器

删除容器：容器停止状态下

![](/assets/火狐截图_2016-09-21T03-11-46.763Z.png)

3）镜像列表使用

![](/assets/火狐截图_2016-09-21T03-12-56.233Z.png)

4）点击“+”搜索镜像

![](/assets/Bui04.png)

5）选择镜像下载

![](/assets/Bui05.png)

实现docker的管理

# docker版平台的使用

登陆后台把ovm-platform.tar镜像上传服务器的任意目录

使用ssh登陆服务器

\[root@localhost src\]\# ls

debug kernels ovm-platform.tar

\[root@localhost src\]\# docker load &lt; ovm-platform.tar

等待一会

使用docker images查看平台太是否上传成功

![](/assets/Bui06.png)

Bui 上通过管理端镜像创建管理端容器

![](/assets/火狐截图_2016-09-21T03-16-03.457Z.png)

点击刷新，便会看到创建的容器

![](/assets/Bui08.png)

浏览器输入管理端容器ip，访问管理平台

![](/assets/Bui09.png)

=======

> > > > > > > 58c308dd0265062eec8f3612d82212650b96b88c

<<<<<<< HEAD
=======








=======
>>>>>>> 58c308dd0265062eec8f3612d82212650b96b88c
>>>>>>> b14068226dd6224c884ee435feb99bd8875c31a3
