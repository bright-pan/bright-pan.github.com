title: ubuntu静态网络配置
date: 2014-11-16 20:25:40
categories: [ubuntu]
tags: [网络配置, ubuntu]
---
有时候服务器需要固定静态的IP时，可以做如下配置来设置服务器的静态ip；
设置/etc/network/interfaces为如下：
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
################################################
auto eth0
iface eth0 inet static
address 192.168.1.135
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.1
dns-nameservers 192.168.1.1
```
然后再执行如下命令：
``` sh
sudo ifdown eth0
sudo ifup eth0
```