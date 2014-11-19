title: find_grep组合使用
date: 2014-11-19 01:10:47
categories: [linux]
tags: [linux,find,grep]
---
### 查找所有".h"文件
``` sh
find /PATH -name "*.h"
```
### 查找所有".h"文件中的含有"helloworld"字符串的文件
``` sh
find /PATH -name "*.h" -exec grep -in "helloworld" {} \;
find /PATH -name "*.h" | xargs grep -in "helloworld"
```
### 查找所有".h"和".c"文件中的含有"helloworld"字符串的文件
``` sh
find /PATH /( -name "*.h" -or -name "*.c" /) -exec grep -in "helloworld" {} \;
```
### 查找非备份文件中的含有"helloworld"字符串的文件
``` sh
find /PATH /( -not -name "*~" /) -exec grep -in "helloworld" {} \;
```
注：/PATH为查找路径，默认为当前路径。带-exec参数时必须以\;结尾，否则会提示“find: 遗漏“-exec”的参数”。
