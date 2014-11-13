title: gpg加解密的使用
date: 2014-11-13 15:23:18
categories: [加解密]
tags: [gpg, gnupg]
---
## 安装
``` sh
$sudo apt-get install gnupg
$gpg --version
gpg (GnuPG) 1.4.16
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Home: ~/.gnupg
支持的算法：
公钥： RSA, RSA-E, RSA-S, ELG-E, DSA
对称加密： IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256,
TWOFISH, CAMELLIA128, CAMELLIA192, CAMELLIA256
散列： MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
压缩： 不压缩, ZIP, ZLIB, BZIP2
```
## 配置
### 生成密钥对
``` sh
$ gpg --gen-key
gpg (GnuPG) 1.4.16; Copyright (C) 2013 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

请选择您要使用的密钥种类：
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (仅用于签名)
(4) RSA (仅用于签名)
您的选择？ 1
RSA 密钥长度应在 1024 位与 4096 位之间。
您想要用多大的密钥尺寸？(2048)
您所要求的密钥尺寸是 2048 位
请设定这把密钥的有效期限。
0 = 密钥永不过期
<n>  = 密钥在 n 天后过期
<n>w = 密钥在 n 周后过期
<n>m = 密钥在 n 月后过期
<n>y = 密钥在 n 年后过期
密钥的有效期限是？(0)
密钥永远不会过期
以上正确吗？(y/n) y

您需要一个用户标识来辨识您的密钥；本软件会用真实姓名、注释和电子邮件地址组合
成用户标识，如下所示：
“Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>”

真实姓名： Bright Pan
电子邮件地址： bright_pan@163.om
注释：
gpg: Interrupt caught ... exiting
bright@bright-ThinkPad-X200-Tablet:~$ gpg --gen-key
gpg (GnuPG) 1.4.16; Copyright (C) 2013 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
请选择您要使用的密钥种类：
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (仅用于签名)
(4) RSA (仅用于签名)
您的选择？
RSA 密钥长度应在 1024 位与 4096 位之间。
您想要用多大的密钥尺寸？(2048)
您所要求的密钥尺寸是 2048 位
请设定这把密钥的有效期限。
0 = 密钥永不过期
<n>  = 密钥在 n 天后过期
<n>w = 密钥在 n 周后过期
<n>m = 密钥在 n 月后过期
<n>y = 密钥在 n 年后过期
密钥的有效期限是？(0)
密钥永远不会过期
以上正确吗？(y/n) y
您需要一个用户标识来辨识您的密钥；本软件会用真实姓名、注释和电子邮件地址组合
成用户标识，如下所示：
“Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>”
真实姓名： Bright Pan
电子邮件地址： bright_pan@163.com
注释： ShenZhen
您选定了这个用户标识：
“Bright Pan (ShenZhen) <bright_pan@163.com>”
更改姓名(N)、注释(C)、电子邮件地址(E)或确定(O)/退出(Q)？ O
您需要一个密码来保护您的私钥。
gpg: gpg-agent 在此次会话中无法使用
我们需要生成大量的随机字节。这个时候您可以多做些琐事(像是敲打键盘、移动
鼠标、读写硬盘之类的)，这会让随机数字发生器有更好的机会获得足够的熵数。
随机字节不够多。请再做一些其他的琐事，以使操作系统能搜集到更多的熵！
(还需要185字节)
.+++++
.+++++
我们需要生成大量的随机字节。这个时候您可以多做些琐事(像是敲打键盘、移动
鼠标、读写硬盘之类的)，这会让随机数字发生器有更好的机会获得足够的熵数。
随机字节不够多。请再做一些其他的琐事，以使操作系统能搜集到更多的熵！
(还需要68字节)
..........+++++
随机字节不够多。请再做一些其他的琐事，以使操作系统能搜集到更多的熵！
(还需要112字节)
.+++++
gpg: 密钥 6AB74C2A 被标记为绝对信任
公钥和私钥已经生成并经签名。
gpg: 正在检查信任度数据库
gpg: 需要 3 份勉强信任和 1 份完全信任，PGP 信任模型
gpg: 深度：0 有效性：  1 已签名：  0 信任度：0-，0q，0n，0m，0f，1u
pub   2048R/6AB74C2A 2014-11-13
密钥指纹 = B116 BC80 CD97 FA44 85F5  595D BB50 B4F3 6AB7 4C2A
uid                  Bright Pan (ShenZhen) <bright_pan@163.com>
sub   2048R/B97A1CBE 2014-11-13
```
### 生成撤销证书
请注意上面的字符串"B97A1CBE"，这是"用户ID"的Hash字符串，可以用来替代"用户ID"。
``` sh
$gpg --gen-revoke B97A1CBE
```
## 使用
### 打印钥匙列表
``` sh
$ gpg --list-keys
/home/bright/.gnupg/pubring.gpg
-------------------------------
pub   2048R/6AB74C2A 2014-11-13
uid                  Bright Pan (ShenZhen) <bright_pan@163.com>
sub   2048R/B97A1CBE 2014-11-13
```
第一行显示公钥文件名（pubring.gpg），第二行显示公钥特征（4096位，Hash字符串和生成时间），第三行显示"用户ID"，第四行显示私钥特征。
### 删除钥匙
``` sh
$gpg --delete-key [用户ID]
```
### 输出钥匙
公钥文件（.gnupg/pubring.gpg）以二进制形式储存，armor参数可以将其转换为ASCII码显示。
``` sh
$gpg --armor --output public-key.txt --export [用户ID]
```
"用户ID"指定哪个用户的公钥，output参数指定输出文件名（public-key.txt）。
类似地，export-secret-keys参数可以转换私钥。
``` sh
$gpg --armor --output private-key.txt --export-secret-keys
```
### 上传公钥

公钥服务器是网络上专门储存用户公钥的服务器。send-keys参数可以将公钥上传到服务器。
``` sh
$gpg --send-keys [用户ID] --keyserver hkp://subkeys.pgp.net
```
使用上面的命令，你的公钥就被传到了服务器subkeys.pgp.net，然后通过交换机制，所有的公钥服务器最终都会包含你的公钥。
由于公钥服务器没有检查机制，任何人都可以用你的名义上传公钥，所以没有办法保证服务器上的公钥的可靠性。通常，你可以在网站上公布一个公钥指纹，让其他人核对下载到的公钥是否为真。fingerprint参数生成公钥指纹。
``` sh
$gpg --fingerprint [用户ID]
```
### 输入密钥
除了生成自己的密钥，还需要将他人的公钥或者你的其他密钥输入系统。这时可以使用import参数。
``` sh
$gpg --import [密钥文件]
```
为了获得他人的公钥，可以让对方直接发给你，或者到公钥服务器上寻找。
``` sh
$gpg --keyserver hkp://subkeys.pgp.net --search-keys [用户ID]
```
正如前面提到的，我们无法保证服务器上的公钥是否可靠，下载后还需要用其他机制验证．

### 加密
假定有一个文本文件demo.txt，怎样对它加密呢？
encrypt参数用于加密。
``` sh
$gpg --recipient [用户ID] --output demo.en.txt --encrypt demo.txt
```
recipient参数指定接收者的公钥，output参数指定加密后的文件名，encrypt参数指定源文件。运行上面的命令后，demo.en.txt就是已加密的文件，可以把它发给对方。

### 解密
对方收到加密文件以后，就用自己的私钥解密。
``` sh
$gpg --decrypt demo.en.txt --output demo.de.txt
```
decrypt参数指定需要解密的文件，output参数指定解密后生成的文件。运行上面的命令，demo.de.txt就是解密后的文件。
GPG允许省略decrypt参数。
``` sh
$gpg demo.en.txt
```
运行上面的命令以后，解密后的文件内容直接显示在标准输出。

### 对文件签名
有时，我们不需要加密文件，只需要对文件签名，表示这个文件确实是我本人发出的。sign参数用来签名。
``` sh
$gpg --sign demo.txt
```
运行上面的命令后，当前目录下生成demo.txt.gpg文件，这就是签名后的文件。这个文件默认采用二进制储存，如果想生成ASCII码的签名文件，可以使用clearsign参数。
``` sh
$gpg --clearsign demo.txt
```
运行上面的命令后 ，当前目录下生成demo.txt.asc文件，后缀名asc表示该文件是ASCII码形式的。
如果想生成单独的签名文件，与文件内容分开存放，可以使用detach-sign参数。
``` sh
$gpg --detach-sign demo.txt
```
运行上面的命令后，当前目录下生成一个单独的签名文件demo.txt.sig。该文件是二进制形式的，如果想采用ASCII码形式，要加上armor参数。
``` sh
$gpg --armor --detach-sign demo.txt
```
### 签名+加密
上一节的参数，都是只签名不加密。如果想同时签名和加密，可以使用下面的命令。
``` sh
$gpg --local-user [发信者ID] --recipient [接收者ID] --armor --sign --encrypt demo.txt
```
local-user参数指定用发信者的私钥签名，recipient参数指定用接收者的公钥加密，armor参数表示采用ASCII码形式显示，sign参数表示需要签名，encrypt参数表示指定源文件。

### 验证签名
我们收到别人签名后的文件，需要用对方的公钥验证签名是否为真。verify参数用来验证。
``` sh
$gpg --verify demo.txt.asc demo.txt
```
