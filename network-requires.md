# 网络要求

&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD

## 网络配置

### 三层交换机

三层配置成混搭模式

单网卡需要配置

双网卡可以设置Bond或者Team

来提高网络的通信能力

具体设置方法参考centos wiki中关于nmtui图形工具设置网络

```
[root@ovm-okatform ~]# nmtui
```

![](/assets/nmtui1.png)

### 无三层交换机

网桥设置

设置网桥的目的是为了方便没有三层交换机用户实现虚拟机与宿主机在同一网段并实现通信的要求

ovs-br

```
[root@localhost ~]# ovs-vsctl add-br br0
[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-br0 
DEVICE=br0ONBOOT=yes
DEVICETYPE=ovs
TYPE=OVSBridge
BOOTPROTO=static
HOTPLUG=no
IPADDR=192.168.0.125
NETMASK=255.255.255.0
GATEWAY=192.168.0.1
DNS1=192.168.0.1
[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0 
DEVICE=eth0
ONBOOT=yes
DEVICETYPE=ovsTYPE=OVSPort
OVS_BRIDGE=br0
BOOTPROTO=none
HOTPLUG=noUUID=66472372-34a1-4c4e-87e5-cbb586a5f6bf
HWADDR=00:25:B3:C9:FF:0A
[root@localhost ~]# 
```

ovs-bond

```
[root@localhost ~]# ovs-vsctl add-br br
[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-bond0
0DEVICE=bond0 
BOOTPROTO=none 
NM_CONTROLLED=no 
ONBOOT=yes
DEVICETYPE=ovs 
TYPE=OVSBond
OVS_BRIDGE=br0
BOND_IFACES="eth0 eth1"
OVS_OPTIONS="bond_mode=balance-tcp lacp=off" 
#OVS_OPTIONS="bond_mode=balance-slb lacp=off" 
#OVS_OPTIONS="bond_mode=active-backup lacp=off" 
[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-br0
DEVICE=br0
ONBOOT=yes
DEVICETYPE=ovs
TYPE=OVSBridge
BOOTPROTO=static
IPADDR=10.54.1.101
PREFIX=22
GATEWAY=10.54.0.1
HOTPLUG=no 
[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth0
DEVICE=eth0
BOOTPROTO=none
NM_CONTROLLED=no
ONBOOT=yes

[root@localhost ~]# cat /etc/sysconfig/network-scripts/ifcfg-eth1
DEVICE=eth1
BOOTPROTO=none
NM_CONTROLLED=no
ONBOOT=yes
```

三种模式可供选择

Active-backup
这种mode 的用途主要在于稳定，平常只会使用 bonding 中的其中一条link 进行传输，当link down时，会马上切换到其他 link 继续传输。本质上没有办法提升throughput。
Balance-slb
这种 mode 的 hash 方式是根据封包的 source MAC + vlan tag来处理。
Balance-tcp
这种mode 的 hash 是根据封包的 L2\/L3\/L4 header 来处理的，所以每条connection 可能会走不同的 link 出去，但是相同 connection 则会一直固定以避免发生 out of order 之类的事情。

=======

