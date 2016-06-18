---
title: MKX使用手册
date: 2016-04-27 23:27:44
tags: mkx
custom_title: 下载MKX介绍PDF
custom_url: /uploads/mkx_introduction.pdf?v=20160618
custom_icon: cloud-download
---

## MKX是什么
**MKX**是一个基于`make`/`expect`/`ssh`的命令行工具集，可以实现**自动部署、远程控制**你的**程序**。
这里所说的**程序**，包含但不限于是一个普通/配置文件、so、cgi、daemon程序哟。

有兴趣的同学可以[下载MKX的介绍PDF](/uploads/mkx_introduction.pdf?v=20160618)详细了解一下哈，本文重点向大家展示怎么使用MKX。
<!--more-->

## 安装MKX
### 下载MKX
MKX托管在Github上面，大家可以参考下面的命令将MKX下载到用户HOME目录。
```
$ cd ~
$ git clone https://github.com/hobby/mkx.git
$ cd mkx
```

### 个人使用
如果只是个人使用，你可以将MKX安装到HOME目录（~/bin）。
```
$ cd ~/mkx
$ make install
```

### 小组使用
如果想让小组成员也能享受MKX的高效，建议将MKX安装到系统目录（/usr/bin），**注意需要root权限哟**。
```
$ cd ~/mkx
$ sudo make install prefix=/usr
```

### 更多细节
对于MKX的开发者，建议以**软链方式安装**到HOME目录，方便开发调试、以及小版本快速升级。
```
$ cd ~/mkx
$ make install link=yes   # 软链方式安装
$ git pull                # 小版本升级（没有新增MKX工具）
$ ls -l ~/bin/mk*         # 查看已安装的MKX工具
```