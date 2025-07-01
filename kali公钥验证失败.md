kali公钥验证失败

![image-20250605202433308](C:\Users\Annie\AppData\Roaming\Typora\typora-user-images\image-20250605202433308.png)

apt-key adv --keyserver pgp.mit.edu --recv-key ED65462EC8D5E4C5

解决

注意keyserver**换成** `pgp.mit.edu`



补充上面方法在第二次试了就不行了

wget -q -O - https://archive.kali.org/archive-key.asc | apt-key add

换成该命令

[Kali在更新国内源时，报错“由于没有公钥，无法验证下列签名...”-CSDN博客](https://blog.csdn.net/2401_87750298/article/details/148467294)



![img](file:///C:\Users\Annie\AppData\Local\Temp\ksohtml2728\wps1.jpg)

**GnuTLS recv error (-54): Error in the pull function. 解决办法**

ip link set dev ens33 mtu 1400



[如何使用命令在Ubuntu 20.04 Linux上安装Vmware Tools - A5IDC - 博客园](https://www.cnblogs.com/a5idc/p/13515678.html)