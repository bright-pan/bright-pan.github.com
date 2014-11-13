title: 在github中使用hexo定制个人博客
date: 2014-11-12 21:57:12
categories: [hexo]
tags: [hexo,github,nodejs]
---
## 建立开发环境
### 注册github帐号
> 请自行去[github](https://www.github.com/)中注册帐号，并创建一个以(帐号名.github.com)为名称的代码仓库。

### 安装git和node.js
``` sh
$sudo apt-get git-core
$sudo apt-get install nodejs-dev
$sudo apt-get install npm
$sudo apt-get install npm-legacy
```
### 安装hexo并生成初始博客模板
``` sh
$sudo npm install -g hexo
$hexo init <folder>
$cd <folder>
$npm install
$hexo server
```
然后在浏览器里打开[*http://localhost:4000*](http://localhost:4000)
## 配置与部署
### 修改配置文件_config.yml
```
#Hexo Configuration
##Docs: http://hexo.io/docs/configuration.html
##Source: https://github.com/hexojs/hexo/
#Site
title: 图符
subtitle: 一个人的世界
description:
author: Bright Pan
email: bright_pan@163.com
language: zh-CN
#URL
##If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
permalink_defaults:
#Directory
source_dir: source
public_dir: public
#Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
highlight:
  enable: true
    line_number: true
	  tab_replace:
#Category & Tag
default_category: uncategorized
category_map:
tag_map:
#Archives
##2: Enable pagination
##1: Disable pagination
##0: Fully Disable
archive: 2
category: 2
tag: 2
#Server
##Hexo uses Connect as a server
##You can customize the logger format as defined in
##http://www.senchalabs.org/connect/logger.html
port: 4000
server_ip: 192.168.1.12
logger: false
logger_format: dev
#Date / Time format
##Hexo uses Moment.js to parse and display date
##You can customize the date format as defined in
##http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss
#Pagination
##Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page
#Disqus
disqus_shortname:
#Extensions
##Plugins: https://github.com/hexojs/hexo/wiki/Plugins
##Themes: https://github.com/hexojs/hexo/wiki/Themes
theme: pacman
exclude_generator:
#Deployment
##Docs: http://hexo.io/docs/deployment.html
deploy:
type: github
repo: https://github.com/bright-pan/bright-pan.github.com.git #填入第一步里自己创建的代码仓库。
branch: master
```
### 发布到github
``` sh
$hexo generate
$hexo deploy
```

### 添加RSS

hexo提供了RSS的生成插件，需要手动安装和设置。步骤如下：

* 安装RSS插件到本地：`npm install hexo-generator-feed`
* 开启RSS功能：编辑`hexo/_config.yml`，添加如下代码：
```
plugins:
- hexo-generator-feed
```
在站点添加链接：
* 在`themes/light/_config.yml`中，编辑 `rss: /atom.xml`
* 在`themes/light/layout/_partial/header.ejs`中，`<ul></ul>`之间，添加一样代码`<li> <a href="/atom.xml">RSS</a> </li>`

### 添加sitemap

同样的，我们使用hexo提供的插件，方法与添加RSS类似。

* 安装sitemap到本地：`npm install hexo-generator-sitemap`
* 开启sitemap功能：编辑hexo/_config.yml，添加如下代码：
```
plugins:
- hexo-generator-sitemap
```
访问zipperary/sitemap.xml即可看到站点地图。不过，sitemap的初衷是给搜索引擎看。
