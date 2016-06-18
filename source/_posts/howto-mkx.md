---
title: MKX使用手册
date: 2016-04-27 23:27:44
tags: mkx
custom_title: 下载MKX介绍PDF
custom_url: /uploads/mkx_introduction.pdf?v=20160618
custom_icon: cloud-download
---

## MKX是什么
**MKX**是一组基于`make`/`expect`/`ssh`的脚本，能**自动部署、远程控制**你的**程序**。
这里所说的**程序**，包含但不限于是一个普通/配置文件、so、cgi、daemon程序哟。

有兴趣的同学可以[下载MKX的介绍PDF](/uploads/mkx_introduction.pdf?v=20160618)详细了解一下，本文重点演示怎么使用MKX。
<!--more-->

## 安装MKX
### 下载MKX
MKX托管在Github上面，大家可以参考下面的命令将MKX下载到用户HOME目录。
```bash
$ cd ~
$ git clone https://github.com/hobby/mkx.git
$ cd mkx
```

### 个人使用
如果只是个人使用，你可以将MKX安装到HOME目录（~/bin）。
```bash
$ cd ~/mkx
$ make install
```

### 小组使用
如果想让小组成员也能享受MKX的高效，建议将MKX安装到系统目录（/usr/bin），**注意需要root权限哟**。
```bash
$ cd ~/mkx
$ sudo make install prefix=/usr
```

### 更多细节
#### 开发者
对于MKX的开发者，建议以**软链方式安装**到HOME目录，方便开发调试、以及小版本快速升级。
```bash
$ cd ~/mkx
$ make install link=yes   # 软链方式安装
$ git pull                # 小版本升级（没有新增MKX工具）
$ ls -l ~/bin/mk*         # 查看已安装的MKX工具
```
#### 跨平台
MKX依赖GNU的工具，例如bash、awk、sed、grep、getopt、expect等等，跨平台使用时保持满足依赖即可。
* Linux平台，一般都安装了上述GNU工具，可以直接使用MKX。当然，不排除某些工具是没有安装好的，遇到缺失工具时再安装就行。
* Windows平台，可以安装Cygwin作为MKX的运行环境，详情请移步[Cygwin官网](https://www.cygwin.com/)。
* Mac OS X平台，可以安装Homebrew得到GNU工具（替换Mac系统自带的BSD工具），详情请移步[Homebrew官网](http://brew.sh/)。


## 第一个示例
好的开始是成功的一半。
在成功安装MKX后，现在向大家演示第一个工具 --- **`mk`**。

### makefile
废话少说，先看看这个示例中的makefile。
```makefile
# helloworld程序的makefile

helloworld: helloworld.cpp
        g++ helloworld.cpp -o helloworld
```
该makefile只有一个目标（make的术语，中文叫目标，英文叫target），且执行过程就是将helloworld.cpp编译链接成helloworld程序。

### 如果用make
对于使用make的同学，有两种方式执行helloworld目标。
1. 默认直接运行，例如`make`，此时make会默认执行makefile中第一个目标，也就是helloworld目标。
2. 指定目标运行，例如`make helloworld`，此时make会直接执行makefile中的helloworld目标。

### 如果用mk
哈哈，实不相瞒，就本示例而言，mk和make使用方式没区别，例如`mk helloworld`，**但mk比make少输入2个字母，因此输入过程快了一倍哈（^_^）**。