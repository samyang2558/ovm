# 安装部署后配置

KVM计算节点安装完毕后使用admin\/admin设置模板库地址

检查模板库是否挂载

```
[root@localhost ~]# cat /etc/fstab 

#
# /etc/fstab
# Created by anaconda on Mon Sep  5 17:22:29 2016
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/centos-root /                       xfs     defaults        0 0
UUID=321b1cea-d662-4652-9cef-47419180dc2c /boot                   xfs     defaults        0 0
/dev/mapper/centos-swap swap                    swap    defaults        0 0
192.168.0.125:/vmimage  /opt/templatelibrary nfs    defaults        0 0
[root@localhost ~]# df -h
文件系统                 容量  已用  可用 已用% 挂载点
/dev/mapper/centos-root   36G  2.1G   34G    6% /
devtmpfs                 1.9G     0  1.9G    0% /dev
tmpfs                    1.9G     0  1.9G    0% /dev/shm
tmpfs                    1.9G  8.9M  1.9G    1% /run
tmpfs                    1.9G     0  1.9G    0% /sys/fs/cgroup
/dev/sda1                497M  125M  373M   25% /boot
192.168.0.125:/vmimage    36G  2.1G   34G    6% /opt/templatelibrary
tmpfs                    378M     0  378M    0% /run/user/992
tmpfs                    378M     0  378M    0% /run/user/0
[root@localhost ~]# 
```

Docker计算节点安装完毕后

系统默认使用的docker.com官方的docker仓库，我们的ovm计算节点的ConsoleUI 中Set Repertory选项中可以设置私有仓库的地址

![](/assets/Docker_Repertory.png)



