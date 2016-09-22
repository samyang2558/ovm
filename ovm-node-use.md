# OVM-Node使用

&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD

## ConsoleUI设置

### 1、使用admin\/admin登陆进入Console UI，设置相关信息

![](/assets/image013.png)

首先一部分显示的系统名称，时间\(国际时间SCT\)主机名

第二部分显示主要的控制台界面

![](/assets/image015.png)

首先要输入root密码然后才能设置

### 2、Console UI各功能的说明（Enter：进入功能管理）

![](/assets/image017.png)

| Network and management interface | 网络和管理接口。 网络包括设置网络ip及dns，测试网络，设置ntp |
| --- | --- |
| Authentication | 认证，其中有登陆及注销 修改root密码 |
| Hardware and BIOS Information | 硬件和BIOS信息，查看系统硬件cpu，内存，存储控制器，BIOS信息 |
| Set Node Type | 设置节点类型，默认开启KVM，docker 计算节点，设置docker私有仓库，设置ntp服务 |
| Set Repertory | 设置KVM模板库的地址和docker私有仓库的地址 |
| Reboot or Shutdown | 重启或者关闭系统 |
| Quit | 退出 |

### 3、设置IP

选择“Network and Management Interface”，回车

![](/assets/image019.png)

选择要设置Ip的网卡（注意网络连接状态）

![](/assets/image023.png)

这里选择“Static”静态配置方式

![](/assets/image025.png)

### 4.设置Node Type为Docker Server

选择“Set Node Type”

![](/assets/image027.png)

选择“Enable\/disable Docker”，可见当前状态为“Disable”，回车设置为“Enable”状态

![](/assets/image029.png)

按“F8”键，确认

![](/assets/image031.png)

Docker Server”启动

注意：中文界面安装系统，不建议“su  -  admin”切换到admin用户下

# 5、访问webUI

1、访问地址：http:\ \ ip:8008

建议使用谷歌、火狐、IE浏览器访问

### 2、WebUI功能介绍

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

![](/assets/image043.png)

5）选择镜像下载

![](/assets/image045.png)

# 6、管理端导入使用

使用shh 上传或者使用U盘复制 ovm-platform.tar 管理平台的docker镜像

导入管理端 ovm-platform.tar 包到本机镜像列表

`[root@localhost src]# ls`

`debug kernels ovm-platform.tar`

`[root@localhost src]# docker load < ovm-platform.tar`

稍等一会儿

![](/assets/image049.png)

# 7.WebUI 上通过管理端镜像创建管理端容器

![](/assets/火狐截图_2016-09-21T03-16-03.457Z.png)

点击刷新，便会看到创建的容器

![](/assets/image053.png)

# 8.浏览器输入管理端容器ip，访问管理平台

用户名密码：admin\/admin

![](/assets/image055.png)

=======

> > > > > > > 58c308dd0265062eec8f3612d82212650b96b88c

