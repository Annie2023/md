kali虚拟机：历史版本及官方最新

1、修改root密码：

```
sudo passwd root
```

2、换源：

```
vim /etc/apt/sources.list

#阿里云
deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

apt update
apt upgrade(过程有点长，可以no continue)
```



























汉化包？