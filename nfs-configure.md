# NFS服务器配置

&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
NFS服务器的配置

**在OVM NFS服务器的角色**

OVM 需要一个NFS资源库来存储 **虚拟机模板（为用户部署提供自助服务）。**因此数据中心必须要有一个NFS服务器导出一个共享目录\(NFS资源库\),即我们的**应用程序库**。

使用NFS资源库:

* 数据中心组件
* 应用管理
* V2V转换
* Hypervisors

它用于存储和共享:

* 虚拟机模板
* 虚拟磁盘快照 \(实例\)
* 虚拟机模板转换

在OVM使用NFS资源库：
使用NFS资源库的步骤:
  •应用管理从远程应用库下载虚拟映像模板到NFS资源库
  •V2V转换虚拟镜像模板为不同的磁盘格式,并将其存储在NFS资源库
  •Hypervisors为部署从NFS资源库复制虚拟镜像模板

**NFS安装和设置类型**

默认情况下, ovm 通过挂载它在 \/opt\/templatelibrary来使用NFS资源库**。**NFS资源库的配置是在eSage Remote Servers上的 .esage\_ecos  文件中和资源库可以有任何的文件和路径名。

你可以从几个不同 NFS 安装和\/或安装类型选择。选择并设置这些选项,将在以下各节中说明:

* 专用存储服务器\(例如NetApp、EMC\)
* 软件NFS服务器
* CentOS   Ubuntu  ISO
* 操作系统上的NFS软件包

**专用存储服务器配置**

创建一个卷,并将它使用NFS导出。

NFS共享目录必须有一个空的文件名称叫 .esage\_ecos \(文件前面的点是必需的\)。

如果需要创建此文件,请使用以下命令。

```
touch /<path-to-shared-dir>/.esage_ecos
```

例如:

```
touch /opt/templatelibrary/.esage_ecos
```

**CentOS7.2 ISO**

NFS资源库可以从CentOS7.2 ISO选择来创建一个独立的NFS服务器。创建一个本地NFS服务器。

**安装**

NFS安装的基本命令如下所示。

在CentOS-RHEL上:

```
[root@localhost  ~] yum -y install nfs-utils rpcbind
```

在Ubuntu上:

```
[root@localhost  ~]sudo apt-get install nfs-kernel-server
```

**配置**

编辑\/etc\/exports文件并添加以下行:

```
[root@localhost  ~]# cat /etc/exports
/vmimage *(rw,no_root_squash,subtree_check,insecure)
#/home *(rw,no_root_squash,subtree_check,insecure)

[root@localhost  ~]# 
```

NFS共享目录必须有一个空的文件名称叫 **.**esage\_ecos \(文件前面的点是必需的\)。

创建此文件,请使用以下命令。

```
touch /<path-to-shared-dir>/.esage_ecos
```

安装成功后也应在\/etc\/fstab中自动配置了您输入的NFS资源库的信息。您可以使用以下命令来检查配置,请执行以下操作:

```
[root@localhost ~]# cat /etc/fstab 

#
# /etc/fstab
# Created by anaconda on Thu Aug 11 01:51:42 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/ovm-root    /                       xfs     defaults        1 1
UUID=81b18c68-fac7-4ad6-be11-789f7b35fbe7 /boot                   ext4    defaults        1 2
/dev/mapper/ovm-home    /home                   xfs     defaults        1 2
/dev/mapper/ovm-vmimage /vmimage                xfs     defaults        1 2
/dev/mapper/ovm-swap    swap                    swap    defaults        0 0
192.168.0.59:/vmimage  /opt/templatelibrary nfs    defaults        0 0
[root@localhost ~]# 

```

=======

