 

网上找了一堆离线安装的教程，都跟屎一样，明明说了离线安装，还跳转这个网页，或者这个授权文件，没办法，自己总结一下内网离线安装的教程。

下载
--

链接：https://pan.baidu.com/s/1M7xG6ckzqDMX92pybpokGg   
提取码：076x

![](https://i-blog.csdnimg.cn/blog_migrate/9c415f343a285e6e9e22dc4541684bf0.png) 

安装
--

1、下载后解压

![](https://i-blog.csdnimg.cn/blog_migrate/ace417445c479a736b25df841db0f59a.png)

 2、点击[Nessus](https://so.csdn.net/so/search?q=Nessus&spm=1001.2101.3001.7020).8.10.0-x64-msi  文件进行安装，一直点击下一步

![](https://i-blog.csdnimg.cn/blog_migrate/3b8ab62fd15a76180c4fb4d924153463.png) 

 ![](https://i-blog.csdnimg.cn/blog_migrate/9f3fe6dd2cc7d9d1b3acefc62fabeb84.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/ba6a8cc964b41955e08fe3c01b9bd020.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/83ebf1383f45f3fec2befd13f10b1fe7.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/21b83cf34d3579dbdf23b98701037660.png)

3、点击完成，自动跳转到浏览器 ：[https://localhost:8834/![icon-default.png?t=N3I4](https://i-blog.csdnimg.cn/blog_migrate/64d367beb016e45fdc8d8aaff940b313.png)https://localhost:8834/](https://localhost:8834/ "https://localhost:8834/")

 ![](https://i-blog.csdnimg.cn/blog_migrate/76129c2e57ab95dad5334d24984f2c5a.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/32500497021f5a41f756c11c0c52e008.png)

 3、点击Connect via SSL

![](https://i-blog.csdnimg.cn/blog_migrate/726c298a83cf18d9eb8572d139366df5.png) 

 4、点击第四个，continue

![](https://i-blog.csdnimg.cn/blog_migrate/daa175585244d702b2fac9147773e193.png)

 5、选择第二个，continue

![](https://i-blog.csdnimg.cn/blog_migrate/b9b36790a658b5e61aee60d57a4ca590.png)

 ![](https://i-blog.csdnimg.cn/blog_migrate/00e2f21f60200a27043605e485fbc589.png)

 6、输入用户名，密码,continue

![](https://i-blog.csdnimg.cn/blog_migrate/317dd8b50aab43fc66239bc429a08c3c.png)

 7、自动加载完成，进入Nessus，但是不能new scan

![](https://i-blog.csdnimg.cn/blog_migrate/9c4c1aeeb4a74e93741cc25060404038.png)

 8、[任务管理器](https://so.csdn.net/so/search?q=%E4%BB%BB%E5%8A%A1%E7%AE%A1%E7%90%86%E5%99%A8&spm=1001.2101.3001.7020)的服务中吧Nessus停止运行，进行激活

![](https://i-blog.csdnimg.cn/blog_migrate/eb17a5938a198ef86b4a1d636674f7fc.png)

 9、替换授权文件，授权文件如下，家庭版升级为专业版

![](https://i-blog.csdnimg.cn/blog_migrate/53f45cb5b8033ea949dd0b7ca9785f58.png)

![](https://i-blog.csdnimg.cn/blog_migrate/592c437946edc9d25ca917c2f68149eb.png)

 10、把all-2.0.tar.gz复制到安装目录下

![](https://i-blog.csdnimg.cn/blog_migrate/f26d6939d954bf0670fa6c4d6fc31c50.png)

 11、更新离线包，以管理元身份运行cmd,cd到Nessus目录下

![](https://i-blog.csdnimg.cn/blog_migrate/3db322cd41beb3ac3b89e81d8d9a17fe.png)

 12、更新插件包，输入nessuscli.exe update .\\all-2.0.tar.gz，更新大概需要几分钟，请耐心等待

![](https://i-blog.csdnimg.cn/blog_migrate/13d4e7fb99ca4342286f00677677b95a.png)

 13、显示更新成功

![](https://i-blog.csdnimg.cn/blog_migrate/eb314cbb6b96fca6d313bbd58cba1550.png)

 14、重新启动nessus服务

![](https://i-blog.csdnimg.cn/blog_migrate/928dd243afc6cf402b77c2604c37ed61.png)

 15、重新浏览器打开Nessus，自动更新插件，可能也需要几分钟，请耐心等待。

 ![](https://i-blog.csdnimg.cn/blog_migrate/833097da117934e769f88d3402b3d803.png)

 16、更新完成，跳转到登录界面，输入用户名和密码，进入Nessus即可使用

![](https://i-blog.csdnimg.cn/blog_migrate/8570b8bfd92802f6849a1a3493484d2f.png)

注意：如果启动不成功，查看plugin\_feed\_info.i[nc文件](https://so.csdn.net/so/search?q=nc%E6%96%87%E4%BB%B6&spm=1001.2101.3001.7020)是否被替换覆盖，如果没有内容，重新复制过来

![](https://i-blog.csdnimg.cn/blog_migrate/393b5fd93943617df5d75ecad2f99a78.png)

使用
--

本文转自 <https://blog.csdn.net/qq_37776764/article/details/130695457>，如有侵权，请联系删除。