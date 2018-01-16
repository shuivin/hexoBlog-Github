---
title: 强力Django+杀手级Xadmin打造在线教育平台(二)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: d2647be6
date: 2018-01-07 03:08:18
---

{% cq %}  老话总是没错的，工欲善其事，苟...{% endcq %}

{% note success %}  
使用Django+Xadmin打造在线教育平台
- 第二章：windows下搭建开发环境
教你安装pycharm,mysql,navicat,python相关环境。
教程仓库地址1: https://github.com/mtianyan/DjangoGetStarted
{% endnote %}

<!--more-->
# windows下搭建开发环境

## 2-1 pycharm,mysql,Navicat安装。

**环境搭建：**

>- pycharm (我：PyCharm 2017.3.2)
>- mysql for windows(mysql-installer-community-5.7.20)
>- navicat for mysql(我：Navicat Premium）
>- python2.7


 **提醒：记住自己设置的mysql密码**

### Mysql

百度"mysql for windows" 直接在百度软件中心下载即可

![mark](http://myphoto.mtianyan.cn/blog/180106/J808E5JA1i.png?imageslim)

如果你的电脑跟我电脑一样空，推荐遵循我的：

1. 点击接受协议
2. 选择Custom选项。(如果默认选项，会发生必要条件缺失：如我电脑没有VS和py3.4)

![mark](http://myphoto.mtianyan.cn/blog/180106/A7Cb96mEce.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180106/66L7DaJJCK.png?imageslim)

- 下图页面点击`next`会显示我们不满足的条件，`back`后点击绿色箭头移除。

![mark](http://myphoto.mtianyan.cn/blog/180106/8C2KL0HaI4.png?imageslim)

- 所有条件都达成，点击`Execute`，等待安装完成。

![mark](http://myphoto.mtianyan.cn/blog/180106/78kgLjJl4F.png?imageslim)

>均为绿色代表安装完成。

- 一直默认选择直到下图页面。设置密码，添加用户(可选)

>**注意：记住自己设置的mysql密码**

![mark](http://myphoto.mtianyan.cn/blog/180106/c8aLD2mdC4.png?imageslim)

>之后全部默认下一步。直到安装完成`Finish`

这时Navicat已经可以正常连接了。如果想让`mysql`命令在cmd下可使用。

`C:\Program Files\MySQL\MySQL Server 5.7\bin` (自行替换为自己的mysql.exe地址)加入环境变量中。

![mark](http://myphoto.mtianyan.cn/blog/180106/DL51BD687G.png?imageslim)

通过`mysql -uroot -p`命令可以进行登入mysql控制台。

![mark](http://myphoto.mtianyan.cn/blog/180106/h1Aa2aJ0G4.png?imageslim)
### Navicat

安装指南：下一步下一步。

下载地址：http://www.navicat.com.cn/download/navicat-for-mysql

我的安装目录: `C:\software\Navicat Premium 12`
### PyCharm 2017.3.2

pycharm官方下载链接：https://www.jetbrains.com/pycharm/download/#section=windows

**我们要选择专业版（Professional）**因为只有专业版才能够新建django项目,免费社区版不能。

**为Pycharm添加解释器：**

`setting` - `Project Interpreter`：

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/E72AIkEB07.png?imageslim)

![mark](http://oerdwodsk.bkt.clouddn.com/blog/180103/D3jB3C6A9g.png?imageslim)

一直定位到 `python.exe` 点击确认。

### Python2.7安装

推荐阅读：**Python开发环境搭建指南(Anaconda2,3共存)**
>推荐选择进阶版本, 方便升级到3.6。

http://blog.mtianyan.cn/post/230a7ad6.html

## 2-2 virtualenv安装和配置

### virtualenv介绍
>每个应用可能需要各自拥有一套`独立`的Python运行环境。virtualenv就是用来为一个应用创建一套`隔离`的Python运行环境。

**virtualenv优点：**

![mark](http://myphoto.mtianyan.cn/blog/180106/AmbE1564gJ.png?imageslim)

它是将全局Python解释器进行私有化复制。
如果不使用虚拟环境，默认的`pip`安装都会安装到同一个目录(java是把自己需要的包放到自己项目目录)，不同项目使用起来会产生问题

### 安装virtualenv
进入cmd，（确保自己的pip已经可用）

```python
pip install virtualenv
virtualenv testvir
# 在当前用户目录(win+r %HOMEPATH%可查看)生成
cd %homepath%
cd testvir
cd Scripts
activate.bat #激活
pip list 
deactivate.bat
```
![mark](http://myphoto.mtianyan.cn/blog/180106/lCIHhf568m.png?imageslim)

默认使用`virtualenv testvir`该命令，会将虚拟环境创建在我们当前用户目录。

**注意：**我的目录在桌面是我的cmder设置的、还请自行`cd %homepath%`前往自己的目录


这样直接使用步骤有写过于繁琐。所以我们使用`virtualenvwrapper`

### virtualenvwrapper安装

```python
pip install virtualenvwrapper-win
pip install virtualenvwrapper(Linux)
```

- 创建虚拟环境

```
mkvirtualenv DjangoTest
```
会创建在`C:\Users\mtian\Envs`当前用户目录下的Envs目录。

修改`mkvirtualenv`创建的目录：新增环境变量`WORKON_HOME`

![mark](http://myphoto.mtianyan.cn/blog/180106/A2im5He9fK.png?imageslim)

- 退出激活状态
```
deactivate
```
- 知道有哪些虚拟环境
```
workon
```
- 直接进入虚拟环境
```
workon DjangoTest
```
![mark](http://myphoto.mtianyan.cn/blog/180107/1cJK2F43I0.png?imageslim)

**注意**前面的`(DjangoTest)`代表进入了虚拟环境。

执行`workon`命令之后，执行`pip install django==1.9.8`安装。

## 2-3 Pycharm和Navicat的简单使用

### pycharm简单使用：

`Setting -> reopen`取消默认打开上一次项目

#### 新建项目并验证成功运行
- 如何新建django项目：

![mark](http://myphoto.mtianyan.cn/blog/180106/d5a87Gid1f.png?imageslim)

>选择好自己的项目的解释器为我们新建的虚拟环境。

新建`project`->`djangotestProj` 。别忘了为我们的虚拟环境安装`Django`


- 检查django环境是否安装好。`interpreter` 

![mark](http://myphoto.mtianyan.cn/blog/180106/6CjH0H1l5c.png?imageslim)

- 点击导航栏的`run`可以直接运行我们的django项目

![mark](http://myphoto.mtianyan.cn/blog/180106/eKh4AC1mhB.png?imageslim)

>上图说明我们的django已经安装并且可以正常运行。

点击浏览器打开`http://127.0.0.1:8000/`进行验证。

![mark](http://myphoto.mtianyan.cn/blog/180106/0cFDmJdChd.png?imageslim)

出现上画面代表我们**大功告成**

#### 设置eclipse快捷键 - keymap

选择`setting`搜索`keymap`设置`eclipse`快捷键

>比如 `ctrl + H` 全局搜索

#### Run edit配置修改

![mark](http://myphoto.mtianyan.cn/blog/180106/ifi4mGE7C9.png?imageslim)

点击上图中`run edit` 可对Django运行时的一些设置进行修改。

比如修改host为`0.0.0.0`，然后就可以设置监听本机ip。然后点击`run`

进入`cmd`下输入`ipconfig`查询自己的ip

![mark](http://myphoto.mtianyan.cn/blog/180106/6lCEGEAJjL.png?imageslim)

>例如我的是`192.168.0.4`

```
192.168.0.4:8000/ 来访问。
```
![mark](http://myphoto.mtianyan.cn/blog/180106/7gBl6DHb6d.png?imageslim)

#### 目录颜色不同的原因

![mark](http://myphoto.mtianyan.cn/blog/180106/JAJCHgBflc.png?imageslim)

可以看到不同的目录颜色不同。这是我们可以进行设置的，为了可以做到智能提示。

![mark](http://myphoto.mtianyan.cn/blog/180106/E2GFBe08Gb.png?imageslim)

右键可以将`template`目录`unmark`

![mark](http://myphoto.mtianyan.cn/blog/180106/3BicA3E8aj.png?imageslim)

可以看到上图目录是灰色的。但是我们`右键mark`为`source Root`目录，会变为蓝色。

![mark](http://myphoto.mtianyan.cn/blog/180106/mLGD68DB8H.png?imageslim)

>这意味着我们在`import`时pycharm会根据设置智能提示。
如果不mark可能会出现很多我们在pycharm中报红色，
但是cmd确可以运行的情况。

### navicat基本使用

### 新建连接

![mark](http://myphoto.mtianyan.cn/blog/180106/D7FEGgIiC6.png?imageslim)

>点击新建一个mysql的连接。

![mark](http://myphoto.mtianyan.cn/blog/180106/hAB7KkaB29.png?imageslim)

>连接名自行设置，密码填自己安装mysql时设置的密码。

### 右键新建数据库

![mark](http://myphoto.mtianyan.cn/blog/180106/maL6ccLG90.png?imageslim)

>数据库名自行设置，`utf-8` `utf_general_ci` 
**注意：这里请与图中选择一致。否则保存中文可能出错**

### 新建数据表

双击数据库`testdjango`使他变绿，然后选中表，然后右键新建表。或使用右侧`新建表`按钮

![mark](http://myphoto.mtianyan.cn/blog/180106/Kd0cAeCj1H.png?imageslim)

输入必要的字段然后使用`ctrl + s` 进行保存并输入表名。

### 增加数据

>双击表，可以展示我们的数据，这时候我们可以自行修改值。
点击左下角可以新增更多行。并且状态栏会显示一些sql语句信息

![mark](http://myphoto.mtianyan.cn/blog/180106/GFCgBHH2fC.png?imageslim)

### 设计表

右键设计表：我们可以添加字段

![mark](http://myphoto.mtianyan.cn/blog/180106/ajiDfHmBim.png?imageslim)

### Sql语句查询

点击查询，新建查询。我们可以输入Sql语句进行查询。

![mark](http://myphoto.mtianyan.cn/blog/180106/1b0h7dh3AC.png?imageslim)


### 表的复制粘贴与数据库传输。数据库导入导出。

>Navicat支持我们把不同数据库的表之间的复制粘贴操作。
>支持数据传输：点击工具数据传输

导出：在数据库上右键我们可以`转储SQL文件`: 可以选择只转存结构。或连带数据一起。
导入：右键点击运行SQL文件。
对于表的操作：删除，清空等，在点击表的右键菜单里。
