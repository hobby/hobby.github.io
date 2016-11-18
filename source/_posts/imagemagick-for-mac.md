---
title: MAC 安装imagemagick
date: 2016-11-12 11:42:00
categories: HOWTO
---

## 干嘛呢
最近遇到图片加水印的需求，这个在linux上面可以用imagemagick的convert工具轻松实现。
但是，mac默认没有这个工具，得自己动动手安装一下，本文记录一下安装方法，备忘 & 扫个盲。

<!--more-->


## 使用homebrew安装
`homebrew`就是mac下面的apt-get、yum，能用ta来安装imagemagick的，肯定不会再浪费时间折腾源码安装啦。
如果你的mac还没有安装`homebrew`，那就先来这[瞧一瞧](http://brew.sh/)，把homebrew装上呗。

### 检查可行性
不是说有了homebrew就能安装imagemagick的，得homebrew上面有imagemagick的安装包才行。
检查方法是先执行下面命令，看看输出结果是否包含`imagemagick`。
```
$ brew search imagemagick
```
下图是YIF的输出结果。
![image](/uploads/brew-search-imagemagick.jpg)

### 安装方法
好了，经过上面方法确认可以安装后，可以通过下面命令**一键安装imagemagick**啦。
```
$ brew install imagemagick
```
安装过程无需人工干预哟~~

### 检测是否成功
若下面命令执行正常，说明安装ok，相关工具已到位啦。
```
$ convert --version
Version: ImageMagick 6.9.4-3 Q16 x86_64 2016-05-20 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2016 ImageMagick Studio LLC
License: http://www.imagemagick.org/script/license.php
Features: Cipher DPC Modules
Delegates (built-in): bzlib freetype jng jpeg ltdl lzma png tiff xml zlib
```

## 水印合成示例
安装这么个`imagemagick`的初衷是想加快指定图片加水印的效率，例如能一条命令解决的问题，就不要搞个PhotoShop来完成啦。
在安装成功后，可以用convert命令来合成水印，下面给个示例命令，相关参数请对号入座哈。
```
$ convert 原始图片路径 \
  -gravity 水印位置枚举值(下面有) \
  -compose over 水印图片路径  \
  -composite 最终合成水印的图片保存路径
```

水印位置枚举定义表：

| 枚举值 | 说明 |
| ----- | --- |
| center | 居中，即水印图片压在原始图片的中间区域 |
| southeast | 右下角，即水印图片压在原始图片的右下角区域 |
| southwast | 左下角，即水印图片压在原始图片的左下角区域 |
| northeast | 右上角，即水印图片压在原始图片的右上角区域 |
| northwast | 左上角，即水印图片压在原始图片的左上角区域 |
