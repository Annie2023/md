 

    Cobalt Strike是一款基于java的渗透测试神器，常被业界人称为CS神器。自3.0以后已经不在使用[Metasploit框架](https://so.csdn.net/so/search?q=Metasploit%E6%A1%86%E6%9E%B6&spm=1001.2101.3001.7020)而作为一个独立的平台使用，分为客户端与服务端，服务端是一个，客户端可以有多个，非常适合团队协同作战，多个攻击者可以同时连接到一个团队服务器上，共享攻击资源与目标信息和sessions，可模拟APT做模拟对抗，进行内网渗透。  
    Cobalt Strike集成了端口转发、服务扫描，[自动化](https://ml-summit.org/cloud-member?uid=c1041&spm=1001.2101.3001.7020)溢出，多模式端口监听，win exe木马生成，win dll木马生成，java木马生成，office宏病毒生成，木马捆绑；钓鱼攻击包括：站点克隆，目标信息获取，java执行，浏览器自动攻击等等

环境搭建
----

> 百度网盘
> 
> 链接：https://pan.baidu.com/s/1QvKzXASZI9Mvjb0-zCDmEg   
> 提取码：Gas1

### 步骤一：准备工作

在开始安装之前，请确保您已经完成以下准备工作：

1.  一台Windows操作系统（推荐Windows 10或更高版本）
2.  Java Runtime Environment (JRE) 8或更高版本
3.  CobaltStrike 4.8安装文件（可以从官方网站或授权渠道获取）

### 步骤二：安装Java环境

        检测是否有jdk环境

> apt search java | grep jdk

         使用这个命令安装jdk

> apt install openjdk\-11-jdk

![](https://i-blog.csdnimg.cn/blog_migrate/ce98416d57de0edd0e2f4a05ca2287ea.png)

### 步骤三：安装CobaltStrike 4.8

#### 服务端安装

![](https://i-blog.csdnimg.cn/blog_migrate/a309907636698a01adf2ebd2a1b34365.png)

        1.解压缩CobaltStrike 4.8安装文件到您选择的目录,也可以直接复制到桌面

![](https://i-blog.csdnimg.cn/blog_migrate/866897c8019f045994ff978541726634.png)

        2.进入该目录，找到并运行“teamserver.bat”文件。 

![](https://i-blog.csdnimg.cn/blog_migrate/e709d8679866d79befbc82441ff794fa.jpeg)

        3. 您将会看到CobaltStrike控制台启动，并显示一个许可证请求。

![](https://i-blog.csdnimg.cn/blog_migrate/299689aef5d2bb2be73a886457c5ab88.png)

#### [客户端](https://so.csdn.net/so/search?q=%E5%AE%A2%E6%88%B7%E7%AB%AF&spm=1001.2101.3001.7020)安装

1.  客户端也需要jdk环境，我用的是jdk-8u381-windows-x64版本，其他版本建议自己尝试。

![](https://i-blog.csdnimg.cn/blog_migrate/67e34ab9fc9a3e083c645350581793ba.png)

        2.进行必要的配置和设置，包括监听器、目标主机等。

![](https://i-blog.csdnimg.cn/blog_migrate/f689a5d2181d85b27de1a7632d937f09.png)

         3.识别证书是否一致

![](https://i-blog.csdnimg.cn/blog_migrate/d5aaec827db9b0c76b2e4ff3e35750d9.png)

        4.完成设置后，您将看到CobaltStrike控制台命令行界面。

![](https://i-blog.csdnimg.cn/blog_migrate/badc5b2d30c4e02adfaaae7e0e447a45.png)

### 常见问题解决方法：

1.  如果在Java环境变量配置过程中出现问题，请确保输入的路径是正确的，并重新启动您的计算机。
2.  如果CobaltStrike控制台无法启动，请检查是否安装了正确版本的Java，并尝试重新安装。
3.  如果许可证文件无法识别或引发错误，请确保您获得了有效的许可证文件。

请关注微信公众号![](https://i-blog.csdnimg.cn/blog_migrate/ecf3f033c296f7a0f216f2d056098c0f.jpeg)获取最新内容。

本文转自 <https://blog.csdn.net/Sgirll/article/details/131865632>，如有侵权，请联系删除。