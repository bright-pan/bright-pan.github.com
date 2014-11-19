title: git基本配置解释
date: 2014-11-18 23:40:36
categories: [git]
tags: [git]
---
``` sh
git config 版本库级配置
git config --global 用户级配置
git config --system 系统级配置
```
# 基本配置
``` sh
git config --global user.name "Bright Pan"
git config --global user.email "bright_pan@163.com"
git config core.paper "less -N"
git config color.diff true
git config --global core.editor emacs
```
# 配置file mode
在linux下载了Qt的软件仓库，拷贝了一份到windows下。在 msysgit 下，发现所有的文件都被修改了。
用 git diff 查看，发现是：
``` sh
$ git diff util/webkit/mkdist-webkit
diff --git a/util/webkit/mkdist-webkit b/util/webkit/mkdist-webkit
old mode 100755
new mode 100644
```
原来是msysgit在windows下需要为文件"仿造"访问权限。由于种种限制，信息不能复原，从而导致原来的755成644了。
解决方法：
``` sh
git config --global core.filemode false
git config core.filemode false
```
# 配置CRLF
CR回车 LF换行
Windows/Dos CRLF \r\n
Linux/Unix LF \n
MacOS CR \r
> 解决方法是：打开命令行，进行设置，如果你是在Windows下开发，建议设置autocrlf为true。
> 2014/08/20 补充：如果你文件编码是UTF8并且包含中文文字，那还是把autocrlf设置为false，
> 并且把所有文件转换为Linux编码（即LF\n），开启safecrlf检查。

## 配置AutoCRLF
提交时转换为LF，检出时转换为CRLF
``` sh
git config --global core.autocrlf true
```
提交时转换为LF，检出时不转换
``` sh
git config --global core.autocrlf input
```
提交检出均不转换
``` sh
git config --global core.autocrlf false
```
## 配置SafeCRLF
拒绝提交包含混合换行符的文件
``` sh
git config --global core.safecrlf true
```
允许提交包含混合换行符的文件
``` sh
git config --global core.safecrlf false
```
提交包含混合换行符的文件时给出警告
``` sh
git config --global core.safecrlf warn
```