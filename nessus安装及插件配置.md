 

#### 文章目录

*   [前言](#_1)
*   [一、安装nessus](#nessus_13)
*   *   [1.1 安装 nessus 程序](#11__nessus__15)
    *   [1.2 运行安装程序](#12__35)
    *   *   [1.2.1 路径选择](#121__39)
        *   [1.2.2 问题弹窗](#122__47)
*   [二、注册 nessus 用户](#_nessus__62)
*   *   [2.1 注册网站](#21__64)
    *   [2.2 注册](#22__77)
    *   [2.3 查收邮箱](#23__91)
*   [三、配置 nessus 网页](#_nessus__98)
*   *   [3.1 回到安装完 nessus 自动弹出的网页，](#31__nessus__100)
    *   [3.2选择 \`Managed Scanner\`,并点击\`continue\`](#32_Managed_Scannercontinue_107)
    *   [3.4 获取第一个值](#34__123)
    *   *   [3.4.1 进入 nessus 的安装路径下](#341__nessus__125)
        *   [3.4.2 打开管理员 的 cmd 窗口](#342___cmd__130)
    *   [3.5 输入激活码](#35__158)
    *   [3.6 下载插件](#36__174)
    *   [3.7 复制/下载 license](#37__license_184)
    *   [3.8 自定义账号密码](#38__204)
*   [四、配置 nessus 插件](#_nessus__213)
*   *   [4.1 停止nessus 的服务](#41_nessus__223)
    *   [4.2 将插件移动到 nessus 目录中](#42__nessus__234)
    *   [4.3 更新插件库](#43__243)
    *   [4.4 重新开启 nessus 服务](#44__nessus__263)
*   [五、检查插件](#_278)

前言
--

```markdown
   本篇讲解` windows` 系统下 `nessus 的安装及插件配置`

   nessus 是支持免费使用的，不过有一定限制，但还是比较划算的，我在本次使用该工具的过程中，发现很难找到一篇对安装和插件配置集合的文章，要么不是最新的，有些出处，要么会遇到一些问题，导致我解决这个问题的时候，找了很多资源
   
   因为我本机已安装，就用的虚拟机安装的，可能会存在样式排版不一致

   接下来开始 安装 `nessus`
```

一、安装[nessus](https://so.csdn.net/so/search?q=nessus&spm=1001.2101.3001.7020)
----------------------------------------------------------------------------

### 1.1 安装 nessus 程序

进入安装 nessus 的官网：[Download Tenable Nessus | Tenable®](https://www.tenable.com/downloads/nessus?loginAttempted=true)

![下载官网](https://i-blog.csdnimg.cn/blog_migrate/f261da8a56c4da133a891f1e3dc83071.png)

因为是外国的网站，可能会有访问问题，下面是网盘地址

链接：https://pan.baidu.com/s/1XxbfqCgVOYeYV4TF6bzTQw?pwd=unkm  
提取码：unkm

安装好后，在想要安装的位置建立[文件夹](https://so.csdn.net/so/search?q=%E6%96%87%E4%BB%B6%E5%A4%B9&spm=1001.2101.3001.7020)，文件名为 nessus ，如 `E/tools/nessus`

### 1.2 运行安装程序

> 在此只说需要注意的地方，其他直接点击下一步就行了

#### 1.2.1 路径选择

记住这个路径，或更改为新建的文件夹中，之后直接下一步，最后安装就行

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/19807dcbe703918f5c5c02e1bd53f15a.png)

#### 1.2.2 问题弹窗

意思是，是否清空这个选择的文件夹，如果需要保留此文件夹下的内容，点 否，不想保留就点 是 (我点的`是`）

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/3dee867103bd69fbbdec2869a6c617f3.png)

安装成功后(点击 finish 后)，会自动弹出 nessus 的网站，先不要管这个，重开一个web页，走第二步

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2b633145033995bfdd116f968a20bffa.png)

二、注册 nessus 用户
--------------

### 2.1 注册网站

注册网站：[https://www.tenable.com/products/nessus/activation-code](https://www.tenable.com/products/nessus/activation-code)

点击这个的 `Register Now`

其他都是试用，或收费

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c180e07275265500d4c2368bfa1e0889.png)

### 2.2 注册

> 邮箱一定要是有效的，是需要激活凭证码的，输入完毕后，点击 get started 就行

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d85fc3273767d6187268aa7beda3161a.png)

成功后的页面

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/c8c9a17443e9393e5f73af6136ab45c3.png)

### 2.3 查收邮箱

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/afc52e3c85e55ec4ee62739222887898.png)

三、配置 nessus 网页
--------------

### 3.1 回到安装完 nessus 自动弹出的网页，

> 点击后 再点击 点击 `continue`

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d510d30cbe5b2a421b45c41c3bdf86a9.png)

### 3.2选择 `Managed Scanner`,并点击`continue`

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/ce5f52a56524e23ed7811174a1f3a16a.png)

就默认第一个，但原本是有获取lincens 和 插件包的链接的，不过可能是因为我用的虚拟机的问题，  
导致样式没出来，如果你的也没有出来跳转链接，就访问这个地址：[https://plugins.nessus.org/v2/offline.php](https://plugins.nessus.org/v2/offline.php)

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/feb846c657caf544835d14a4c6490c86.png)

### 3.4 获取第一个值

#### 3.4.1 进入 nessus 的安装路径下

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/d5e0b86a5ad554fc56815588647dfe44.png)

#### 3.4.2 打开管理员 的 cmd 窗口

在左下角的 windows 图标右键

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/818a2121390ed532cd68a2aee2e022ef.png)

复制 nessus 的路径，并在cmd 窗口中 输入 `cd {nessus的所在路径}`

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/7b105bcb077a431887a14708e666e857.png)

输入命令

```powershell
nessuscli.exe fetch --challenge

# 如果报错，就把nessuscli 改为 .\nessuscli.exe 

# 将 这个码复制下来，粘贴到 激活网页的第一个文本框中
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/2333930951045c6314782bce71b1d782.png)

### 3.5 输入激活码

在第二个文本框中输入邮箱当中的激活码，并点击提交

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/715db53c7cdc03dce191e82ff09e3096.png)

提交成功的页面

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/193713fc4392fc5b1e450e33b3295b3c.png)

### 3.6 下载插件

> 点击此链接 进行 下载

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/6325065a172294e3387500ef6233a3ed.png)

### 3.7 复制/下载 license

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/bddc780e83352cfc9d8e946912fe30a3.png)

在配置 nessus 的页面粘贴 license 并点击 `continue`

> 注意：是全部 license 不要只复制中间的字符，否则无效，我这边是样式问题

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/f4d6468302fbc475443b77af14a10e75.png)

### 3.8 自定义账号密码

> 随便输入就行，这边是以后登录 nessus 的账号和密码，需要记下来，点击提交

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/92c7067f9b07e6f3880e7c8ab6700001.png)

四、配置 nessus 插件
--------------

刚进入nessus 的时候是没有插件的，需要在网页上下载，或将下载的插件更新到nessus 中

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/61b36f10e322dda6bda2b46eb4d1162f.png)

### 4.1 停止nessus 的服务

在之前cmd 窗口中，输入

```powershell
net stop “Tenable Nessus”
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/cff3f7a07596db918b6fbac32dfd6394.png)

### 4.2 将插件移动到 nessus 目录中

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/59e936caa9b9e0a8e30d6b1879223d7d.png)

### 4.3 更新插件库

在 cmd 窗口中输入 ，此步骤需要等待一段时间，耐心等待

```powershell
nessuscli.exe update all-2.0-tar.gz

# 如果报错

# 将 nessuscli.exe 改为 .\nessuscli.exe
# all-2.0-tar.gz 改为 .\all-2.0-tar.gz
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/5700df23fc1922fca006fe7e0e6fb25f.png)

### 4.4 重新开启 nessus 服务

在 cmd 窗口中输入

```powershell
net start "Tenable Nessus"
```

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/be874e0e98ea6bb5eb3173132a8a3cba.png)

五、检查插件
------

回到 nessus 网页

等待插件编译 （这里就不放图了）

点击`settings`

![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/0f8e66134b7cf3a81796528d19fe1c15.png)

本文转自 <https://blog.csdn.net/qq_62326247/article/details/137272641>，如有侵权，请联系删除。