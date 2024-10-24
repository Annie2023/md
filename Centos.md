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

关闭防火墙
systemctl stop firewalld
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
#DocumentRoot "/var/www/html"
DocumentRoot "/var/www/myweb"
<Directory "/var/www/myweb">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

在ifmoudle中增加访问页面
index.jsp index.php index.htm

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
编辑内容如下：
<VirtualHost 192.168.06.6:80>
DocumentRoot "/var/www/www1"
ServerName 192.168.06.6
<Directory "/var/www/www1">
Order allow,deny
Allow from 192.168.06.0/24
</Directory>
DirectoryIndex index.html
Errorlog "/var/www/www1/web1-access_log"
Customlog "/var/www/www1/web1-access_log" common   
</VirtualHost>

<VirtualHost 192.168.06.8:80>
DocumentRoot "/var/www/www2"
ServerName 192.168.06.8
<Directory "/var/www/www2">
Order allow,deny
Allow from 192.168.06.0/24
</Directory>
DirectoryIndex index.html
Errorlog "/var/www/www2/web2-access_log"
Customlog "/var/www/www2/web2-access_log" common   
</VirtualHost>


:wq

创建目录：
mkdir /var/www/OA
mkdir /var/www/www1
mkdir /var/www/www2
mkdir /var/www/myweb

编辑一下内容：
vim /var/www/OA/index.html
vim /var/www/www1/index.html
vim /var/www/www2/index.html
vim /var/www/myweb/index.html

OA权限：
配置名称：
vim /var/www/OA/.htaccess
AuthName "Test"
AuthType Basic
AuthuserFile "conf/OAuser"
Require user admin

配置验证密码：
htpasswd -c /etc/httpd/conf/OAuser admin
admin

systemctl start httpd.service

(如果打不开http服务)httpd -t

配置完每次重启

systemctl restart httpd.service
```

![image-20241022172826374](C:\Users\Annie\AppData\Roaming\Typora\typora-user-images\image-20241022172826374.png)

![image-20241022172751553](C:\Users\Annie\AppData\Roaming\Typora\typora-user-images\image-20241022172751553.png)



注意：重启机子后需要重新配置ifconfig！！！！（ifconfig清空了）

配置完之后访问192.168.6.4:81/OA 报Internal error

修改方法：在计算机里面搜索error_log查看错误日志

![image-20241022210313005](C:\Users\Annie\AppData\Roaming\Typora\typora-user-images\image-20241022210313005.png)

发现配置重复了

修改.htaccess文件中：为AuthuserFile "conf/OAuser"

## 任务二

```
xrandr
xrandr -s 1152X864
yum -y install httpd(已经装了)
systemctl restart httpd
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

### 不同IP

```html
vim /etc/sysconfig/network-scripts/ifcfg-ens33

写入
IFADDR1=192.168.xxxx 245.147

systemctl restart network
ifconfig
ping -c 4 192.168.245.147
ping -c 4 192.168.245.146

vim /etc/httpd/conf/httpd.conf

写入

<VirtualHost 192.168.245.146:80>
    DocumentRoot  /var/www/web1
    ServerName 192.168.245.146 
</VirtualHost>
<VirtualHost 192.168.245.147:80>
    DocumentRoot  /var/www/web2
    ServerName 192.168.245.147 
</VirtualHost>

:wq

mkdir /var/www/web1
mkdir /var/www/web2
vim /var/www/web1/index.html
vim /var/www/web2/index.html

systemctl restart httpd

分别访问192.168.245.146:80
192.168.245.147:80
```

### 不同主机

```html
vim /etc/sysconfig/network.scripts/ifcfg-ens33
DNS1=192.168.245.146
DOMAIN=stu.com

yum -y install bind(装了)
rpm -q bind

这里修改ifcfg文件之后可能会安装不成功（改成联网状态或者按照一下修改ifcfg文件）
注释掉
#IPADDR
#NETMASK
#GATEWAY
#DNS1
#DOMAIN
修改
BOOTPROTO=dhcp
保存

systemctl restart network
systemctl start named

vim /etc/named.conf
listen on port 改为192.168.245.146
allow-deny改为any

vim /etc/named.rfc1912.zones
修改
zone "localhost.localdomain" IN{
xxx
}
为
zone "stu.com" IN{
    xxxx（不变）
    file "stu.com.zone"
    xxxx（不变）
}
zone "245.168.192.in-addr.arpa" IN{
    xxxx（不变）
    file "stu.com.zero"
    xxxx（不变）
}

cd /var/named
ll
cp -p /var/named/named.localhost /var/named/stu.com.zone
cp -p /var/named/named.loopback /var/named/stu.com.zero
vim /var/named/stu.com.zone
修改
$TTL 1D
@	IN SOA	dns.stu.com. (
					0	; serial
					1D	; refresh
					1H	; retry
					1W	; expire
					3H )	; minimum
@	IN 	NS	dns.stu.com.
dns 	IN 	A 	192.168.245.146
www1	IN 	A 	192.168.245.146
www2	IN 	A 	192.168.245.147

vim /var/named/stu.com.zero

$TTL 1D
@	IN SOA	dns.stu.com. (
					0	; serial
					1D	; refresh
					1H	; retry
					1W	; expire
					3H )	; minimum
@	IN 	NS	dns.stu.com.
146  IN 	PTR     www1.stu.com.
147  IN 	PTR 	www2.stu.com.

systemctl restart named
systemctl restart httpd
```





# ftp配置

下载vsftp包

rpm -q vsftpd

yum -y install vsftpd 

启动服务

systemctl start vsftpd

设置静态ip：192.168.6.16  子网掩码：255.255.255.0

本机可以ping成功

```
vim /etc/vsftpd/vsftpd.conf

修改
anon_upload_enable=NO   #禁止匿名用户上传
userlist_enable=NO #白名单关掉

写入
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
anon_root=/var/ftp/doc
anon_world_readable_only=YES
启用服务器参数：
max_clients=100
max_per_ip=2
pasv_enable=YES  //被动模式开启
pasv_min_port=45000
pasv_max_port=49000

创建匿名用户文件夹
mkdir /var/ftp/doc
vim /var/ftp/doc/1.txt
1234564564684

重启服务 
systemctl restart vsftpd
systemctl status vsftpd

测试：
（1）可以控制台ftp命令
需要安装
yum install -y ftp
(2)文件资源管理
其他位置->连接到服务器->ftp://192.168.6.16
验证
匿名可下载不可上传
```

```
实现本地用户要求：约束本地用户在自己test目录下（就是其他用户不限制，只有test限制）
创建本地用户
useradd -d /home/test -m test
passwd test
123
123
vim /etc/vsftpd/vsftpd.conf
chroot
修改
chroot_local_user=NO #限制
chroot_list_enable=YES  #开白名单
chroot_list_file ....#开黑名单

写入
allow_writeable_chroot=YES

编辑黑名单用户
vim /etc/vsftpd/chroot_list
test

systemctl restart vsftpd

注：要一直忘记密码，取消登录状态

```

