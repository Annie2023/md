Centos

第一步换源换源！！！！！

yum遇到错误

[CentOS 7 yum无法使用解决方法Could not retrieve mirrorlist http://mirrorlist.centos.org/?release=7&arch= - 愚生浅末 - 博客园 (cnblogs.com)](https://www.cnblogs.com/kohler21/p/18331060)

换源后进行配置

# dns配置：

```
yum install bind
rpm -q bind  #检查
```

打开named.conf文件（直接搜不到，隐藏掉了）

可以知道是在etc下的文件

```
将listen-on和allow-query设置成any

复制两个出来改成（配置正向和反向区域）

zone "study.com" IN {
        type master;
        file "study.com.zone";
};

zone "44.168.192.in-addr.arpa" IN {
        type master;
        file "study.com.ptr";
};

在主文件夹找到 /var/named/
复制两次named.localhost文件
分别修改为之前取的名字study.com.zone和study.com.ptr
```

修改配置文件：

正向：

```
$TTL 1D
@	IN SOA	dns.study.com. rname.invalid. (
					0	; serial
					1D	; refresh
					1H	; retry
					1W	; expire
					3H )	; minimum
@	IN 	NS	dns.study.com.
dns	IN 	A 	192.168.44.2
www	IN 	A 	192.168.44.10
mail	IN 	A 	192.168.44.11
ftp	IN 	A 	192.168.44.12
library	IN 	A 	192.168.44.13
pcl	IN 	CNAME ftp
```

反向：

```
$TTL 1D
@	IN SOA	dns.study.com. rname.invalid. (
					0	; serial
					1D	; refresh
					1H	; retry
					1W	; expire
					3H )	; minimum
@	IN	NS	dns.study.com.
2	IN	PTR	dns.study.com.
10	IN	PTR	www.study.com.
11	IN	PTR	mail.study.com.
12	IN	PTR	ftp.study.com.
13	IN	PTR	library.study.com.
```

检查：

named-checkconf -z /etc/named.conf

设置静态ip地址192.168.44.2

子网掩码255.255.255.0

dns192.168.44.2

重启服务器

```
systemctl restart named
nslookup开始解析
```

解析不成功：

[Linux下DNS正、反向解析报错:** server can‘t find ???: NXDOMAIN_server cant find nxdomain-CSDN博客](https://blog.csdn.net/qq_45675449/article/details/107060332#:~:text=问题可能就是区域配置库文件 (也就是正、反向解析文件)的属主和属组的问题，我们进入DNS的目录来看一下。 我们可以看到，我们自己定义的正向解析文件和反向解析文件的属组为 root 而DNS原配置文件的属组为 named,所以我们就要修改 正向、反向解析文件的属组，执行命令： chgrp named 配置文件名 1 修改完成后，重启DNS服务。)

需要修改属组具体命令

```
cd /var/named
ll
修改我们自己的正反向配置文件
chgrp named 配置文件名
```

再nslookup发现解析成功

# apache配置

注意一开始安装连接外网

安装apache

```
yum -y install httpd 
```

检查是否安装

```
rpm -q httpd
```

启动服务,会默认开一个127.0.0.1

```
systemctl start httpd.service
systemctl stop httpd.service
```

火狐成功访问127.0.0.1

关闭防火墙（临时关闭重启又开）

```
setenforce 0
```

## 任务一

设置三个静态ip

```
ifconfig
ifconfig ens33:1 192.168.06.4
ifconfig ens33:2 192.168.06.6
ifconfig ens33:3 192.168.06.8
```

配置apache的主目录http.conf

```
vim /etc/httpd/conf/httpd.conf
增加监听
Listen 192.168.06.4:81
```

修改根目录

```html
#Document "/var/www/html"
Document "/var/www/myweb"
<Directory "/var/www/myweb">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

在ifmoudle中增加访问页面
index.jsp index.php index. htm

配置字符编码改为GB2312
AddDefaultcharset GB2312

配置虚拟目录
Alias /OA/ "/var/www/OA/"
配置虚拟目录的权限
<Directory "/var/www/OA/">
    AllowOverride AuthConfig
    Options Indexes FollowSymLinks
    Allow from all
    Require all granted
</Directory>

:wq!退出

vim /etc/httpd/conf.d/a.conf
<VirtualHost 190.168.06.6:80>
DocumentRoot "/var/www/html"
ServerName 190.168.06.6
<Directory>
Order allow.deny
Allow from 190.168.06.0/24
</Directory>
DirectoryIndex index.html
Erroring "/var/www/www1/web1-access_log"
Customlog "/var/www/www1/web1-access_log" common
    
</VirtualHost>
```

