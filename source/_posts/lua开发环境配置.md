title: lua开发环境配置
date: 2014-12-22 19:02:25
categories: [lua]
tags: [lua]
---
## 安装curl
``` sh
sudo apt-get install curl
```
## 安装libreadline-dev
``` sh
sudo apt-get install libreadline-dev
```
## lua下载、编译、安装
``` sh
curl -R -O http://www.lua.org/ftp/lua-5.2.3.tar.gz
tar zxf lua-5.2.3.tar.gz
cd lua-5.2.3
make linux test
sudo make install
```