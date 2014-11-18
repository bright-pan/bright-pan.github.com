title: git diff 的几个主要用法
date: 2014-11-13 15:13:26
categories: [git]
tags: [git]
---
由于git的工作区域有3种：work tree，staged, HEAD
> work tree: 工作区域
> staged: 暂存区域
> HEAD: 提交区域
``` sh
$ git diff (work tree 与 staged)
$ git diff --cached (staged 与 HEAD）
$ git diff HEAD (work tree 与 HEAD)
```
