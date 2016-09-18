# 安装后配置

&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
安装完毕后使用admin用户登录（admin\/admin）

初始化平台系统。

初始化后检查是否将配置文件写进平台系统检查平台系统配置

## 平台配置

\/opt\/esage\/config\/esage.properties

其中192.168.0.125的位置是需要修改的、

```
[root@localhost ~]# cat /opt/esage/config/esage.properties 
[datacenter]
esage.database.host = 127.0.0.1
esage.rabbitmq.username = guest
esage.rabbitmq.host = 127.0.0.1
esage.appstore.templateLocation = 192.168.0.125:/vmimage
esage.appstore.localtemplatePath = /opt/templatelibrary/
esage.rabbitmq.password = guest
esage.datacenter.id = Default
esage.rabbitmq.port = 5672
esage.redis.host = 127.0.0.1
esage.redis.port = 6379
esage.event.identity = m_user
esage.platform.api.location = http://192.168.0.125:8009/api
esage.event.credential = m_password

[platform]
esage.platform.sessionTimeout = 60
esage.database.user = esage
esage.database.password = esage_2020@
esage.database.host = 127.0.0.1
esage.platform.mail.server = 127.0.0.1
esage.platform.mail.user = ovm_sf@51ovm.com
esage.platform.mail.password = none
esage.auth.module = esage
esage.rabbitmq.username = guest
esage.rabbitmq.password = guest
esage.rabbitmq.port = 5672
esage.redis.host = 127.0.0.1
esage.redis.port = 6379
esage.platform.api.location = http://192.168.0.125:8009/api
esage.rabbitmq.host = 127.0.0.1

[root@localhost ~]# 
```

如果自动化配置没有生效，需要手工配置， ovm-UI配置文件的路径为：

\/var\/www\/html\/ui\/index.html

其中192.168.0.125的位置是需要修改的

```
[root@localhost ~]# cat /var/www/html/ui/index.html 
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <title></title>
  <meta name="description" content="">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <link rel="stylesheet" href="./styles/fonts.css"/>
  <!--<link rel="stylesheet" href="./styles/react-select.css"/>-->
</head>
<body>
<!--[if lt IE 8]>
<p class="browsehappy">You are using an <strong>outdated</strong> browser. Please <a href="http://browsehappy.com/">upgrade
  your browser</a> to improve your experience.</p>
<![endif]-->
<div id="content">
</div>
<script>
  __REACT_DEVTOOLS_GLOBAL_HOOK__ = parent.__REACT_DEVTOOLS_GLOBAL_HOOK__
</script>
<script>
  const global_uploadHost = 'http://192.168.0.125:8009';
  const global_host = 'http://192.168.0.125:8009/api';
</script>
<script type="text/javascript" src="assets/main.js"></script>
<!--<script type="text/javascript" src="utils/react-select.js"></script>-->
</body>
</html>
[root@localhost ~]# 
```

修改完配置文件后重启一下两个服务

```
[root@localhost ~]# systemctl restart esage-tomcat.service
[root@localhost ~]# systemctl restart httpd.service
```

=======

> > > > > > > 58c308dd0265062eec8f3612d82212650b96b88c

