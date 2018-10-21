---
title: win10WSL关闭声音方法理清
copyright: true
abbrlink: d73bd557
date: 2018-10-22 00:45:34
tags: 网管
categories:
---


# wsl 关闭声音方法网文不行，自己摸索的方法



<!--more-->

## 在vim 里面的关闭方法
在.vimrc的配置里面加入如下行即可
> " set vb t_vb=                                "关闭提示音

## vim外面终端烦人的tab音
网文说在~/inputrc 里面添加如下code,我这边测试无效.
> set bell-style none,
我用如下方法可以解决问题.
> 编辑 /etc/inputrc，找到#set bell-style none这一行，去掉前面的注释符号。
