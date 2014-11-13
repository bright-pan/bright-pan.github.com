title: git中文路径乱码
date: 2014-11-13 15:13:26
categories: [git]
tags: [git,中文路径]
---
在执行git status命令的时候，会出现下面的乱码情况
``` sh
$ git status
位于分支 develop
您的分支与上游分支 'origin/develop' 一致。
未跟踪的文件:
  （使用 "git add <file>..." 以包含要提交的内容）
   "source/_posts/\350\207\252\345\212\250\346\270\251\346\260\264\345\205\221\346\215\242\350\243\205\347\275\256\347\232\204\346\203\263\346\263\225.md"
```
解决方法如下：
``` sh
$ git config --global core.quotepath false
$ git status
位于分支 develop
您的分支与上游分支 'origin/develop' 一致。
未跟踪的文件:
  （使用 "git add <file>..." 以包含要提交的内容）
	source/_posts/git中文路径乱码.md
```
