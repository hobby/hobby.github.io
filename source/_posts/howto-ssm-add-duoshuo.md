---
title: Hexo增加社会化评论系统 - 多说
date: 2016-11-14 00:00:00
categories: HOWTO
---

## 摘要
博客需要有评论模块，否则大家看完后没地方拍砖（吐嘈），那就不好玩了。
静态博客自己不能实现评论模块，否则不叫静态博客了。
不过还好，这个时代有一个社会化评论系统，例如多说。这些社会化评论系统可以做为静态博客的一个补充，实现评论模块。
扫扫盲现在用的就是多说提供的评论系统啦，接下来介绍如何接入多说哈！
<!--more-->

## 注册一个多说账号
注册入口传送门来一个 -> [多说官网](http://duoshuo.com/)

## 创建一个新站点
创建站点入口传送门来一个 -> [创建站点](http://duoshuo.com/create-site/)。
需要注意的是，建议`站点名称`和`多说域名`中的输入框部分保持一致，最好和站点的域名前缀一样咯，例如扫扫盲用的是`saosaomang`。
![image](/uploads/duoshuo-create-site.png)

## 调整hexo配置
创建站之 后，就可以拿着创建站点时填入的`多说域名`输入框的内容配置hexo啦，例如上图中的是`saosaomang`。
配置hexo方式是在hexo目录下，补充`duoshuo_shortname: saosaomang`到`_config.yml`，例如扫扫盲的配置如下。
```bash
$ grep duoshuo_shortname _config.yml
duoshuo_shortname: saosaomang
```
至此，配置基本完成啦！

## 预览一下
在配置完成后，执行一下`hexo s`来预览一下。
### 评论数量区
没有评论的时候
![image](/uploads/duoshuo-preview-nocomment.png)
只有1条评论的时候
![image](/uploads/duoshuo-preview-onecomment.png)
有多条评论的时候
![image](/uploads/duoshuo-preview-multicomment.png)
### 评论编辑区
![image](/uploads/duoshuo-preview-commentlist.png)

## 调整评论数量展示
说实话，笔者不太喜欢默认的评论数量展示风格，于是有了一翻调整过程，最终效果如下。
没有评论的时候
![image](/uploads/duoshuo-preview-nocomment-now.png)
只有1条评论的时候
![image](/uploads/duoshuo-preview-onecomment-now.png)
有多条评论的时候
![image](/uploads/duoshuo-preview-multicomment-now.png)

那么，怎么配置的？见：
![image](/uploads/duoshuo-config-commentnum.png)

还有疑问？留言哈~~~
