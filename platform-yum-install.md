&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD

# 在线安装

# 脚本下载地址： [http:\/\/mirror.51ovm.com\/install\/ovm-platform-install.sh](http://mirror.51ovm.com/install/ovm-platform-install.sh)

使用官方发行版的CentOS 7 RHEL7 MINI 安装。

如果用户使用CentOS官方ISO安装了相应的 Centos7.2操作系统，并需使用外部的Yum源来安装相应的软件包，则需在线安装。

在线安装步骤如下：

1. 下在安装好系统复制安装脚本到任意目录（假如安装包名称为ovm-platform-install.sh）。

2. 在此目录下执行“.\/ovm-platform-install.sh”（如果不能执行请附加相应的执行权限）进行安装OVM管理平台。（在安装过程中，安装程序会从yum源安装系统依赖库。）

  \[root@localhost ~\]\# ls

  anaconda-ks.cfg ovm-platform-install.sh

  \[root@localhost ~\]\# chmod 100 ovm-platform-install.sh

  \[root@localhost ~\]\# .\/ovm-platform-install.sh

  Checking distribution... CentOS Linux release 7.2.1511 \(Core\)

  Installing OVM Platform, continue \(y\/n\)? y

  Installing ovm release... 4

  Done.

  Installing OVM Platform Packages...

3. 安装结束后会弹出自动初始化的窗口

4. 初始化完成后需要重启服务器以使用


> > > > > > > 58c308dd0265062eec8f3612d82212650b96b88c

