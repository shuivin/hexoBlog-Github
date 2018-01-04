---
title: Python开发环境搭建指南(Anaconda2,3共存)
tags:
  - Python
  - 零基础入门
  - 环境搭建
copyright: true
abbrlink: 230a7ad6
date: 2018-01-02 22:14:08
categories:
---

{% cq %}  工欲利器事必先善其器{% endcq %}

{% note  %} 对于Python环境搭建的指南，分为普通版和进阶版。
推荐进阶版：Windows下Anaconda2(Python2)和Anaconda3(Python3)的共存
- [√] 慕课网Python开发环境搭建: 配开发环境
{% endnote %}


<!--more-->

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/DHImeGED84.png?imageslim)

# Python开发环境搭建

搭建环境分为两个版本：
- 基础版，供初学者快速安装体验。
- 进阶版, 供对于数据科学，机器学习有兴趣者安装。

`推荐：`安装进阶版，一步到位。

## 基础版：Windows下安装python环境(2.7 | 3.x)

>官网： https://www.python.org/


### 安装包下载。
选择download下的windows。点击进入。

![download下的windows](http://upload-images.jianshu.io/upload_images/1779926-6c1b1786c1c2134a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下图中红框为64位版本。32位版本可以选择Windows x86 executable installer

![选择3.7下的executable installer](http://upload-images.jianshu.io/upload_images/1779926-7d2044c2a9c2045c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2.7版本的安装包下载：**

![2.7版本](http://upload-images.jianshu.io/upload_images/1779926-3a24a247dce81ddf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 安装python。

点击下一步下一步进行默认安装即可。（跟平常装个qq啥的没两样）

### 安装完成的测试。

`win（即徽标键）` + `R` 输入`cmd` ：
打开命令行。输入`python`不报错的进入python控制台下。

## 进阶版：Windows下Anaconda2(Python2)和Anaconda3(Python3)的共存

**转载**

原文地址：http://blog.csdn.net/infin1te/article/details/50445217

>Anaconda是一个Python的科学计算发行版，包含了超过300个流行的用于科学、数学、工程和数据分析的Python Packages。由于Python有2和3两个版本，因此Anaconda也在Python2和Python3的基础上推出了两个发行版，即Anaconda2和Anaconda3。

以上文字摘自转载博客。通俗讲就是一个python的各种科学计算包的大合集版本。省去了自己安装大量基本包的过程。

`Tips:` 3.x版本建议选择Python 3.5.1 |Anaconda 4.1.0 (64-bit)

以后如果要使用python进行TensorFlow windows版的配置可以省下时间。

**这是博主自入python坑以来找到的最好的共存方法，没有出过问任何题**！！！

**这是博主自入python坑以来找到的最好的共存方法，没有出过问任何题**！！！

**这是博主自入python坑以来找到的最好的共存方法，没有出过问任何题**！！！

![最终实现](http://oerdwodsk.bkt.clouddn.com/blog/180103/E4H8flhgjA.png?imageslim)


## Linux下的python使用。

- Linux 默认安装python，建议安装IPython；
- `sudo apt-get install ipython`安装Ipython（支持Tab键自动补齐）
- 使用Vim来创建`.py`文件
- 输入`python`即可查看当前版本

>IPython是Python的交互式Shell，提供了代码自动补完，自动缩进，高亮显示，执行Shell命令等非常有用的特性。特别是它的代码补完功能.

## python文件类型(常识)

python执行过程：

`.py`文件 --> python解释器 --> 字节码文件 --> python解释器 --> 二进制文件 --> 内存、运行 --> 打印结果

字节码文件:

- `.pyc` 
转换方式： `python -m py_compile xxx.py`
作用：提高程序的加载速度

- `.pyo`(优化编译的.pyc文件)
转换方式： `python -O -m py_compile xxx.py`
作用：提高程序的运行速度

## eclipse下的python环境安装。

添加python开发环境到eclipse：

- 点击`help`——`install New Software`
- 点击`add`，弹出新窗口：
- Name:填PyDev
- Location:填 http://pydev.org/updates
- 确认后会出现 PyDev，勾选Pydev。
- pydev for eclipse--> next--> accept-->finish
- file--> new--> project -->Pydev下 pydevProject

python的dev下载地址：http://pydev.org/updates
