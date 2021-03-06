# 管理虚拟机

### 部署虚拟机

首先需要有上传的可用模板

进入项目中点击vapp，在虚拟机的列表处。点击“+”添加虚拟机。在弹出的创建虚拟机对话框中输入虚拟的名称，选择模板，直接点击确定或者点击下一页设置cpu内存磁盘大小等点击确定

![](/assets/火狐截图_2016-09-26T06-32-14.294Z.png)

此时的虚拟还处于未部署状态，点击虚拟机的功能按钮，选择部署

![](/assets/火狐截图_2016-09-26T06-55-22.329Z.png)

![](/assets/火狐截图_2016-09-26T06-56-59.273Z.png)

处于部署状态的虚拟机

![](/assets/火狐截图_2016-09-26T06-58-03.217Z.png)

等待部署完成，部署完成后会自动开机

![](/assets/火狐截图_2016-09-26T07-00-59.393Z.png)

### 编辑虚拟机

编辑处于关机状态的虚拟。

![](/assets/火狐截图_2016-09-26T08-37-39.848Z.png)

点击处于关机状态虚拟机的功能按钮选择编辑虚拟机，在基本信息处可以编辑虚拟机的名称，cpu，内存，网络带宽，和vnc的端口

![](/assets/火狐截图_2016-09-26T08-41-08.888Z.png)

在网络处可以编辑虚拟机网络设置，如添加网卡删除网卡，编辑已有网卡的ip等信息

![](/assets/火狐截图_2016-09-26T08-49-57.108Z.png)

在存储处可以修改磁盘大小，添加磁盘和删除磁盘。需要注意的是先选中磁盘功能按钮出现编辑点击后，在上面可以编辑磁盘的大小，先点击磁盘的保存然后点击整个编辑的页面的保存

![](/assets/火狐截图_2016-09-26T09-31-39.855Z.png)

### 删除虚拟机

点击虚拟的功能按钮，然后点击删除等待一会虚拟机就已经删除了。

### 彻底删除虚拟机

进入项目中在回收站中彻底删除虚拟机

### 远程访问

点击虚拟机功能按钮，选择更多选项，进入虚拟机的详细页面，点击远程访问，在弹出的窗口中就可以看到虚拟机的显示器。

![](/assets/火狐截图_2016-09-26T07-02-37.629Z.png)

### 加载虚拟光驱

点击虚拟机功能按钮，选择更多选项，进入虚拟机的详细页面，点击加载虚拟光驱，在弹出的加载虚拟光驱的对话框中选择要加载的光驱镜像，然后点击链接。

![](/assets/火狐截图_2016-09-26T08-41-08.999Z.png)

### 加载USB设置

点击虚拟机功能按钮，选择更多选项，进入虚拟机的详细页面，点击加载USB。在弹出的对话框中选择要加载的USB设置，点击链接。

![](/assets/火狐截图_2016-09-26T08-13-12.570Z.png)

### 设置第一启动项

点击虚拟机功能按钮，选择更多选项，进入虚拟机的详细页面，点击设置启动类型。选择第一启动项，点击确定

### 查看虚拟机所在的宿主机

在开机状态虚拟机，点击虚拟机的功能按钮，点击编辑在弹出的虚拟机基本信息中看到端口上边的ip，这个ip就是虚拟机所在的宿主机。

====》

