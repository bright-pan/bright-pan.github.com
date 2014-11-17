title: 为hexo博客添加自动化配置脚本
date: 2014-11-13 23:59:48
categories: [hexo]
tags: [hexo, 脚本]
---
在不同的机器上写博客的时候需要安装和配置开发环境，所以将这些工作写成脚本，放到hexo工程根目录底下方便调用。
``` sh
#!/bin/bash
sudo apt-get install nodejs npm nodejs-legacy
sudo npm install -g hexo
npm install
npm install hexo-generator-feed
npm install hexo-generator-sitemap
```