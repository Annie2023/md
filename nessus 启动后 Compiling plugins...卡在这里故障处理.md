每次nessus启动后，访问首页都卡在这里。我的是free 10.x的版本

![](https://img2020.cnblogs.com/blog/335426/202111/335426-20211124101529601-923157177.png)

 Linux解决方法：

先关闭nessusd服务，然后执行如下：

cd /opt/nessus/sbin/

./nessusd -R

![](https://img2020.cnblogs.com/blog/335426/202111/335426-20211124104714424-1580184008.png)

过程较慢，耐心等待，然后开启服务,进度条会卡一小会，耐心等待刷新，过一会就可以看到登录可。

就可以执行主机扫描了。

本文转自 <https://www.cnblogs.com/netsa/p/15597136.html>，如有侵权，请联系删除。