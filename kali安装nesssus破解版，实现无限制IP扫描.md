1.[Nessus](https://zhida.zhihu.com/search?content_id=199285682&content_type=Article&match_order=1&q=Nessus&zhida_source=entity)官网下载kali对应的Nessus版本

![](https://picx.zhimg.com/v2-bb497a786cea94ad47148561d8c1e74f_1440w.jpg)

下载适合自己系统的nessus版本

2.放在kali中的某一个文件夹下，我这里是放在了documents下

![](https://pic3.zhimg.com/v2-bef394a4e6574d8d2e1d243de314eaa0_1440w.jpg)

3.进入该文件夹documents打开终端执行如下命令

sudo dpkg -i Nessus-10.1.2-debian6\_amd64.deb

![](https://pica.zhimg.com/v2-a72096d84a34ff394cc209e4d4b75ec8_1440w.jpg)

图中显示安装成功

4.开启服务：执行如下命令

sodo systemctl start nessusd.service

4.1然后进入地址[https://kali:8834/#/](https://link.zhihu.com/?target=https%3A//kali%3A8834/%23/)

![](https://picx.zhimg.com/v2-c932289db22a0a36bcb3549f51392f1b_1440w.jpg)

4.2选择Managed Scanner，点击Continue

4.3选择[Tenable.sc](https://zhida.zhihu.com/search?content_id=199285682&content_type=Article&match_order=1&q=Tenable.sc&zhida_source=entity)，点击Continue

![](https://pica.zhimg.com/v2-e07bb68b17ebd4b9eaf114f184793d42_1440w.jpg)

4.4设置用户名和密码，并submit

![](https://pic2.zhimg.com/v2-28ed291f8d7f93590333cebab0ccfcd9_1440w.jpg)

4.5进入nessus设置页，这时的Nessus是没有扫描功能的

![](https://pica.zhimg.com/v2-aa18bd1cdb4e9cc6f7ee9fd994f92b66_1440w.jpg)

5.更新插件（注意：插件包名称要和自己的插件包名称一致，插件包可以Nessus官网获取，也可以直接在网上找资源下载）

sudo /opt/nessus/sbin/[nessuscli](https://zhida.zhihu.com/search?content_id=199285682&content_type=Article&match_order=1&q=nessuscli&zhida_source=entity) update **all-2.0-update.tar.gz**

![](https://picx.zhimg.com/v2-602ad863f8de19535c32ded80c2bf09f_1440w.jpg)

如图所示则更新成功

5.关闭服务

sudo systemctl stop nessusd.service

6.重启服务

sudo systemctl start nessusd.service

7.继续终端输入如下命令，进入文件plugin\_feed\_info.inc中

sudo vi /opt/nessus/var/nessus/plugin\_feed\_info.inc

8.粘贴如下内容

PLUGIN\_SET = "202204151200”;

PLUGIN\_FEED = "ProfessionalFeed (Direct)";

PLUGIN\_FEED\_TRANSPORT = "[Tenable Network Security Lightning](https://zhida.zhihu.com/search?content_id=199285682&content_type=Article&match_order=1&q=Tenable+Network+Security+Lightning&zhida_source=entity)";

9.创建文件

sudo mkdir /opt/nessus/var/nessus/plugins/

10.复制8内容到新文件plugins中

sudo cp /opt/nessus/var/nessus/plugin\_feed\_info.inc /opt/nessus/var/nessus/plugins/

11.关闭服务

sudo systemctl stop nessusd.service

12.重启服务

sudo systemctl start nessusd.service

13.再次更新插件

sudo /opt/nessus/sbin/nessuscli update **all-2.0-update.tar.gz**

![](https://pic2.zhimg.com/v2-313cac388026b18e4553f42ba7b5a061_1440w.jpg)

如图所示更新成功

14.以上步骤完成后，再次进入地址[https://kali:8834/#/](https://link.zhihu.com/?target=https%3A//kali%3A8834/%23/)，等待插件加载完成后登录即可，登录进入后就可以看到是破解过后的无限制IP扫描的版本了。

![](https://picx.zhimg.com/v2-93d32915480fb58d2b4c08c016f4ac51_1440w.jpg)

本文转自 <https://zhuanlan.zhihu.com/p/500193204>，如有侵权，请联系删除。