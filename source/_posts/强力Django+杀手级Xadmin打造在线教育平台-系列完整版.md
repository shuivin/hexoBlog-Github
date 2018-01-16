---
title: 强力Django+杀手级Xadmin打造在线教育平台 - 系列完整版
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: 8b4c6c13
date: 2018-01-17 00:15:31
---

{% cq %} 「比更大还更大」(Bigger than Bigger){% endcq %}

{% note %} 
- 初级复习: 写一个留言板来复习Django基础知识
- 项目实战: 使用Django+xadmin搭建一个在线教育网站
最终成果: http://mxonline.mtianyan.cn

GitHub代码仓库: 
https://github.com/mtianyan/Mxonline2

{% endnote %}

<!--more-->

{% cq %}  请开始你的表演是做一个项目的第一步{% endcq %}

{% note  %}  
使用Django+Xadmin打造在线教育平台
- 第一章：项目介绍和课程介绍

教程仓库地址1:https://github.com/mtianyan/DjangoGetStarted
{% endnote %}

# 项目演示和课程介绍

Django是一个Python中Web开发的主流框架，被许多大型公司使用，如Google，豆瓣，YouTube，知乎，instagram:

![mark](http://myphoto.mtianyan.cn/blog/180107/a5h8mfid18.png?imageslim)

创业公司喜欢的web框架。严格按照互联网公司开发流程，写出优雅简练的代码。
循序渐进，细致入微。独立完成完整项目。学习完课程，找份Python web开发工作不在话下。

教程线上已部署地址: http://mxonline.mtianyan.cn

**系统介绍：**

- 系统具有完整的用户登录注册以及找回密码功能，拥有完整个人中心。
- 个人中心: 修改头像，修改密码，修改邮箱，可以看到我的课程以及我的收藏。可以删除收藏，我的消息。
- 导航栏: 公开课，授课讲师，授课机构，全局搜索。
- 点击`公开课`--> 课程列表，排序-搜索。热门课程推荐，课程的分页。
- 点击`课程`--> 课程详情页中对课程进行收藏，取消收藏。富文本展示课程内容。
- 点击`开始学习`--> 课程的章节信息，课程的评论信息。课程资源的下载链接。
- 点击`授课讲师`-->授课讲师列表页，对讲师进行人气排序以及分页，右边有讲师排行榜。
- 点击`讲师的详情页面`--> 对讲师进行收藏和分享，以及讲师的全部课程。
- 导航栏: 授课机构有分页，排序筛选功能。
- 机构列表页右侧有快速提交我要学习的表单。
- 点击`机构`--> 左侧：机构首页,机构课程，机构介绍，机构讲师。
- 后台管理系统可以`切换主题`。左侧每一个功能都有列表显示, 增删改查，筛选功能。
- 课程列表页可以对不同字段进行排序。选择多条记录进行删除操作。
- 课程列表页：过滤器->选择字段范围等,搜索,导出csv，xml，json。
- 课程新增页面上传图片，富文本的编辑。时间选择，添加章节，添加课程资源。
- 日志记录：记录后台人员的操作

学完后还可以将本网站改造成`电商网站`,`在线旅游`等其他网站

![mark](http://myphoto.mtianyan.cn/blog/180107/2A76h7im9k.png?imageslim)

## 开发环境搭建任务
windows下通过`pycharm`和`virtualenv`搭建开发环境

## django基础知识回顾任务

照顾基础薄弱同学: 通过留言板功能回顾django基础知识。

![mark](http://myphoto.mtianyan.cn/blog/180106/c91fA7Lb5e.png?imageslim)

## 数据库设计和xadmin搭建后台管理系统任务

通过业务分析设计`django`的每个`app`，设计`app`下的`model`。设计`外键关系`，通过django的`migrate`设计生成数据表。

然后将这些`model`注册到`xadmin`当中。为每个model配置`搜索`,`过滤字段`，以及`列表页的显示字段`。配置xadmin的`主题选择`功能。

![后台设计工作](http://upload-images.jianshu.io/upload_images/1779926-5e9910e92bdef649.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 系统功能模块实现任务

**实现所有后台功能 & 面试中经常被提及的web开发知识。**

**几乎所有的django常用模块：**

- `setting`配置
- `url`配置
- `view`书写
- `model`设计
- `form`和`modelform`的使用
- `templates`模板的使用
- `django`常用的内置函数

## web系统知识以及网络安全任务
**防止一些攻击问题：**

- sql注入
- xss攻击
- crsf攻击

这些攻击的原理以及防护措施

## xadmin扩展知识

**掌握更多可定制功能:**

- 权限管理
- 权限配置
- 权限，用户，组之间的关系。
- xadmin常用插件
- 如何自定义xadmin插件
- xadmin的富文本编辑功能
- xadmin的excel导入功能。

还会用到一些开源的django开发库。

![mark](http://myphoto.mtianyan.cn/blog/180106/eGhG2Kk51D.png?imageslim)

不管是想全面学习Django还是想做一个线上教育平台都可以满足要求。学习完Django,我们对于学习其他框架和通过Django搭建我们自己的系统，都会成为很简单的事情。

{% cq %}  老话总是没错的，工欲善其事，苟...{% endcq %}

{% note success %}  
使用Django+Xadmin打造在线教育平台
- 第二章：windows下搭建开发环境
教你安装pycharm,mysql,navicat,python相关环境。
教程仓库地址1: https://github.com/mtianyan/DjangoGetStarted
{% endnote %}

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


{% cq %}  小项目不扫何以扫天下 {% endcq %}

{% note success %}  
使用Django+Xadmin打造在线教育平台
- 第三章：通过留言板功能回顾django基础知识
通过做一个小留言板，学习django基础知识
教程仓库地址1: https://github.com/mtianyan/DjangoGetStarted

{% endnote %}


# 通过留言版功能回顾django基础知识

教程中本章对应上传的仓库为: https://github.com/mtianyan/DjangoGetStarted
>对应第一次commit:留言板仓库初始化。内容截止3-1一章结束。

- 将对于django目录结构，使用Django快速搭建可以提交的表单页面，models.py , urls.py, views.py。
- 从数据库中取出数据展示到html中：Django Template的配置。
- 即django的基础知识通过这个留言板项目进行一个全面细致的学习。

## 3-1 django目录结构

django目录：

    projectname : 保存Django项目的urls,setting，uwsgi文件

如下图新建一个Django项目`DjangoGetStarted`，使用我们上章节中已存在的虚拟环境`DjangoTest` (里面已经装好了django)

![mark](http://myphoto.mtianyan.cn/blog/180106/BKLg4JDJCe.png?imageslim)



### django自动生成的目录

初始化完成后的目录如下：(如果不是，那么你们可能创建的不是django项目)

![mark](http://myphoto.mtianyan.cn/blog/180106/3aIIDddEmc.png?imageslim)

可以看到主目录`DjangoGetStarted`与项目目录`DjangoGetStarted`

- DjangoGetStarted(文件夹)：	
	- setting.py： 项目全局配置文件
	- urls.py： 主要的urls配置入口
	- wsgi.py： 是Django启动需要的文件。
- templates(文件夹)： 放置html文件
- manage.py： 启动Django需要的主要文件。(主要的Django命令都通过manage.py运行)

### 还需要我们自己创建的目录

app是Django里一个一个应用的文件夹单位。

通过 `Tools -> Run manage.py Task`创建app：

![mark](http://myphoto.mtianyan.cn/blog/180106/lFgLChlhdc.png?imageslim)

#### startapp message

可以看到当输入`startapp message`之后，创建了`message`应用。并存放在了：与项目目录同级目录。

![mark](http://myphoto.mtianyan.cn/blog/180106/Ef2F5Bf7FA.png?imageslim)

#### 新建static目录

使用`static`目录来存放网站的静态文件：js，css，图片等。

#### 新建log目录

使用`log`目录来存放网站的日志文件

#### 新建media目录

使用`media`目录存放用户上传的图片等资源。

#### 解决项目大了之后app过多问题

1. 新建文件夹 `apps`
2. 将`message`文件夹拖入`apps`文件夹内：会自动生成`__init__.py`文件表明这是一个包。使得apps文件夹可导入。

![mark](http://myphoto.mtianyan.cn/blog/180106/3625a0imed.png?imageslim)

>这时我们就会发现在导入我们的message的内容就得配置较长的路径。

![mark](http://myphoto.mtianyan.cn/blog/180107/k10eEBg357.png?imageslim)

>每次前面都得加上`apps.`，这可烦死人啦。

**解决方案奉上**
>将`apps`目录右键`mark`成`Source Root`(Mark 方法查看第一章pycharm简单使用：目录颜色不同的原因)

![mark](http://myphoto.mtianyan.cn/blog/180107/I9255edkaF.png?imageslim)

mark成功之后**变蓝**(变绿的话，只能摸摸头了，当然选择原谅)，然后可以直接使用短路径进行import

#### Mark后Pycharm 不报错，Cmd下运行报错。

Mark后pycharm知道这是一个项目的`Souce Root`路径了，但是cmd并不知道。

>在项目目录下通过cmd命令行使用`python manage.py runserver`

![mark](http://myphoto.mtianyan.cn/blog/180107/2043A3KagE.png?imageslim)

>pycharm中mark只是pycharm自身可以进行识别短路径。

**解决方案：**

>我们在setting文件中配置我们的`apps`路径:

![mark](http://myphoto.mtianyan.cn/blog/180107/IhD2bJDI6K.png?imageslim)

>图解读：我们需要在setting中向上图一样设置,程序就会接着报错。(换了一个错误了，滑稽脸)

```python
import sys
sys.path.insert(0,os.path.join(BASE_DIR,'apps'))
```

上述代码为将apps拼接项目绝对路径后的路径插入当前系统的环境变量path中，这样就可以成功解决(个屁屁啊)。

成功性测试(测试已失败)：

>这个import放到manage.py文件是不行的 你把manage.py中这行删除 因为django整个的配置还没有启动好 import django的model是不行的，

插播：忘了失败吧，我偷学下面方法养你。

**终极解决：将这个`import`方法比如urls.py.等可以成功启动。**或者自行删除该import。

![mark](http://myphoto.mtianyan.cn/blog/180107/b230j2d65e.png?imageslim)

红色警告：
```
You have unapplied migrations; your app may not work properly 
until they are applied. Run 'python manage.py migrate' to apply them.
```
是因为我们没有进行数据库`models`进行初始化`migrate`.

`python manage.py migrate`我们之后会用到，现在不要做。

### github仓库项目初始化第一次commit。

![mark](http://myphoto.mtianyan.cn/blog/180107/aFheliD18B.png?imageslim)

>输入用户名密码，点击login。

![mark](http://myphoto.mtianyan.cn/blog/180107/ci4AKb7Lb0.png?imageslim)

>选择左侧导航中`Git` 设置你的git.exe的路径

![mark](http://myphoto.mtianyan.cn/blog/180107/6Af7m9cI0i.png?imageslim)

点击`Share project on GitHub`会弹出下图窗口

![mark](http://myphoto.mtianyan.cn/blog/180107/JjH1FjmB0i.png?imageslim)

填写你的项目`名称`，`描述`。点击`share`。

会弹窗让你选择需要上传的项目文件与commit信息。然后将项目上传至github。

**我教程中上传的仓库为:  https://github.com/mtianyan/DjangoGetStarted**

>对应第一次commit:留言板仓库初始化。内容截止3-1一章结束。

## 3-2 配置表单页面

>上节教程(来学习本节前置条件):

- 对应第一次commit: 留言板仓库初始化。内容截止3-1一章结束。

**github仓库地址：https://github.com/mtianyan/DjangoGetStarted**

> 本节我们学习将表单页面配置进django项目中

### 必要的该说的，该了解的

**前置条件：**

>你已经学习了前面教程。将项目的文件夹目录结构，setting配置等修改完毕与我保持一致。

本节通过Django快速的配置一个**留言板页面**来学习

Django从请求到响应的整个完整流程。为我们开发在线教育平台打下基础。

![mark](http://myphoto.mtianyan.cn/blog/180107/ghebBaKDDa.png?imageslim)

上图便是本节教程所要用到的静态页面: 前往Github下载：`form.html`

>具体的业务：填写信息 -> 然后点击提交 ->数据被存储到数据库。

这个`html`是一个单文件，里面已经包含了`css` `js`内容。

### 将html文件整合进项目操作步骤

#### 将`html`文件直接复制进`templates`目录.

![mark](http://myphoto.mtianyan.cn/blog/180107/bd7L9HEbB1.png?imageslim)

#### 创建`static目录下的css文件夹` 和 `static/js`

-  在css中再新建一个`style.css`

![mark](http://myphoto.mtianyan.cn/blog/180107/7L3m4291JK.png?imageslim)

-  `form.html`中点击`<style>`标签左侧减号。将style内容收成一行。然后把这一行内容**剪切粘贴到**`style.css`

![mark](http://myphoto.mtianyan.cn/blog/180107/EJHc2DdkK2.png?imageslim)

- 粘贴进去之后，**将首尾两个`<style>`删除**,`shift + tab`可以将css格式化更整齐。

- 在`form.html`新建`<link>`来引入css。(文件里其实已经先加上了，学一种操作而已)

```html
<link rel="stylesheet" href="/static/css/style.css">
```
### 配置Django连接Mysql数据库

在`setting.py` 大概80行找到:

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
```

这是Django默认与自己项目根目录下的`db.sqlite3`连接的设置。

![mark](http://myphoto.mtianyan.cn/blog/180107/00e3abbbFJ.png?imageslim)

我们的项目是与`mysql`连接，所以我们要改成如下：

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'testdjango',
        'USER': 'root',
        'PASSWORD': '密码',
        'HOST': "127.0.0.1"
    }
}
```

其中的`name`应设置为我们中在Navicat中新建的数据库名字。**名字一定要保持一致**

这时要将我们之前建的表提前**全部删除**掉。

![mark](http://myphoto.mtianyan.cn/blog/180107/g8l89KCfam.png?imageslim)

#### 配置mysql驱动和seeting文件。
点击`Tools 菜单下 Run manage.py Task`我们会发现报错了：

```
    raise ImproperlyConfigured("Error loading MySQLdb module: %s" % e)
django.core.exceptions.ImproperlyConfigured: Error loading MySQLdb module: No module named MySQLdb
```

>由错误信息我们可以看出是因为没有安装数据库驱动模块`MySQLdb`

![mark](http://myphoto.mtianyan.cn/blog/180107/lJKDjik9Cb.png?imageslim)

`cmd`下`workon`进我们的虚拟环境目录。`pip install mysql-python`
然后会发现报错：

![mark](http://myphoto.mtianyan.cn/blog/180107/65Gad4D4l9.png?imageslim)

```
_mysql.c(42) : fatal error C1083: Cannot open include file: 'config-win.h': 
No such file or directory error: command 
'"C:\Users\mtian\AppData\Local\Programs\Common\Microsoft\Visual C ++ 
for Python\9.0\VC\Bin\amd64\cl.exe"' failed with exit status 2
```
前往地址 https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python

下载`MySQL_python_1.2.5_cp27_none_win_amd64.whl`到本地,放到桌面。
然后使用下面命令进行安装：注意是在虚拟环境下。

```
cd Desktop
pip install MySQL_python-1.2.5-cp27-none-win_amd64.whl
```
![mark](http://myphoto.mtianyan.cn/blog/180107/G60aadGLkJ.png?imageslim)

这个时候我们再次点击`Tools 菜单下 Run manage.py Task `会看到已经没有刚才的错误。
![mark](http://myphoto.mtianyan.cn/blog/180107/4mF5KmaCKj.png?imageslim)
但是会有红框里的警告，**面向强迫症解决方案是**在`setting.py` 新增`STATIC_ROOT = '/static/'`

但其实现在还没有用到这个参数。后面用到我们再配置。(推荐自行克服强迫症)

输入下面命令来生成表:
```
makemigrations
migrate
```
![mark](http://myphoto.mtianyan.cn/blog/180107/gaaL4hlAGj.png?imageslim)

这时我们去Navicat查看会发现为我们生成了很多表。

![mark](http://myphoto.mtianyan.cn/blog/180107/bK273a3j4D.png?imageslim)

这些都是Django系统默认的**内置**数据表。

做完这些操作我们可以点击`Run`来运行项目，
然后到`http://127.0.0.1:8000/`来访问看是否运行成功。成功页面(It worked)

### 配置form页面展示出来：

`DjangoGetStarted/urls.py`修改如下:

```python
urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^form/$', getform) #这行是新增加的.
]
```

新增加`url(r'^form/$', getform)`,`^`是代表以`form`为开头，`$`代表以`/`结尾的地址。
这里`getform` 是对于这个`url`的相应处理的`view`。我们先去创建一个.

`message/views.py`添加如下代码：

```python
def getform(request):
    return render(request, 'message_form.html')
```
`request` 参数是一个django的`http request`对象。(基础)
这里我们可以按住`ctrl` + `左键` 跟踪到我们的`render`函数里面。
`Alt + 左箭头` 回来。

```python
def render(request, template_name,...):
```
源代码解读：可以看到我们的`render`需要一个`request对象`和`template_name`参数

**注意：记性好的还记得我们提供的源文件是form.html**

>知识点：django内置了很多html页面，form会先从内置中寻找。所以我们得改。

因此我们需要右键如下图`Refactor`修改`from.html` 为`message_form`

![mark](http://myphoto.mtianyan.cn/blog/180107/l0I7CGB2Be.png?imageslim)

如果我们的项目在运行，`ctrl + s`会自动重启我们的项目。

这时我们有了view，我们可以去配置完整的url了(前面已经配完整的检查一遍)：

`DjangoGetStarted/urls.py`
```
from message.views import getform

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^form/$', getform)
]
```
**这里我们不能加括号**否则会变成方法的调用。

按住`ctrl` + `render` 跟踪到我们的`url`函数里面查看源码如下:可以看到它除过一组正则表达式，还需要接收一个view对象。

```
def url(regex, view,...):
```
如果`getform`加上括号会报错：

```
TypeError: getform() takes exactly 1 argument (0 given)
```

访问`http://127.0.0.1:8000/` 正常结果：Page not found

```
Using the URLconf defined in DjangoGetStarted.urls, Django tried these URL patterns, in this order:

^admin/
^form/$
```
是因为我们在url中加入了个人的配置`^form/$`,它就不会采用默认配置了。

原因：(源码探究标记点)

这时访问：http://127.0.0.1:8000/form/

旧版本pycharm会报：`TemplateDoesNotExist`错误。我的新版本pycharm并没有出现。

重要代码在`DjangoGetStarted/settings.py` 60行左右

```
# 指明我们的templates目录路径
'DIRS': [os.path.join(BASE_DIR, 'templates')]
# 老版本pycharm创建django项目该值为空。
```
现在再次访问 http://127.0.0.1:8000/form/

**页面出来了但是样式没有。static目录下的css文件提示没有找到。**

![mark](http://myphoto.mtianyan.cn/blog/180107/73EjmflBe9.png?imageslim)

Setting中静态文件的配置，这是因为我们setting中的

```
STATIC_URL = '/static/'
```
只说明了目录的名称。并没有指明查找的根路径。添加下面代码：

```
STATIC_URL = '/static/'
STATICFILES_DIRS = [
    os.path.join(BASE_DIR, 'static')
]
```

**过程中看似不停的出错**，其实是为了让大家更好记住该记住的。

### 项目配置流程图

我们刚才是以倒序：

1. 把html文件放进来
2. 通过简单的url配置来访问html。
3. 发现找不到页面，所以我们设置setting中`DIRS`
4. 文件找到了又说找不到静态文件，我们设置了`STATICFILES_DIRS`

![mark](http://myphoto.mtianyan.cn/blog/180107/ihf44icl9d.png?imageslim)

这是我们的整体流程图，推荐新建一个项目再按照正向流程图来一遍。

后面我们的工作会围绕从`migration生成数据表往下的内容`展开。

GitHub地址：https://github.com/mtianyan/DjangoGetStarted

>本节结束对应于commit：

## 3-3 django orm介绍与model设计
上节教程完成后代码(来学习本节前置条件):

**github仓库地址：https://github.com/mtianyan/DjangoGetStarted**

- 对应commit: 留言板前端页面展示。本次内容截止教程3-2结束。

>可能现在你还在通过手写sql语句来操作数据库，当我们有了orm，数据库操作变得很简单。这一小节我们来学习Django中的orm。

### 原生sql 与 orm

没有orm 的情况下message/views.py代码：

```
import MySQLdb

# 使用原生sql获取书的列表
def book_list(request):
    # 创建到数据库的连接: 指明用户名，数据库，密码
    db = MySQLdb.connect(user = 'me', db='mydb', passwd='secret', host='localhost')
    # 创建一个游标对象执行器
    cursor = db.cursor()
    # 书写我们需要的sql语句
    cursor.execute('SELECT name FROM books ORDER BY name')
    # 对于fetchall()的结果做遍历，将遍历回来的结果当做数组，取第0个值name。
    names = [row[0] for row in cursor.fetchall()]
    db.close()
```

可不可以让数据库字段的查询和使用类的一个属性一样简单？没错登登登：orm上场了

```
book:name

book.name
book.save()
```

Django的orm就是为了让我们不再写上面那样的语句，而是像使操作数据库像使用类和类属性一样。

### 创建我们的models

>verbose_name:对象的人类可读的名称，单数:
```python
verbose_name = "pizza"
```

```
class Meta，内嵌于 UserMessage 这个类的定义中
如果 class Publisher 是顶格的，那么 class Meta 在它之下要缩进4个空格－－按 Python 的传统
你可以在任意一个 模型 类中使用 Meta 类，来设置一些与特定模型相关的选项。
如：设置ordering = ['name']，默认地都会按 name 字段排序
```
message/models.py：

```python
# 继承于django.db.models.Model
class UserMessage(models.Model):
    # 设置最大长度，verbose_name在后台显示字段会用到
    name = models.CharField(max_length=20, verbose_name=u"用户名")
    # Django提供内置的邮箱字段会帮忙验证` default_validators = [validators.validate_email]`
    email = models.EmailField(verbose_name=u"邮箱")
    address = models.CharField(max_length=100, verbose_name=u"联系地址")
    message = models.CharField(max_length=500, verbose_name=u"留言信息")


    class Meta:
        verbose_name = u"用户留言信息"
        # db_table ，这里我们让它自动生成所以不用指定
```

这时我们执行`makemigrations messages`会发现并没有改动。

![mark](http://myphoto.mtianyan.cn/blog/180107/bCK3e2eF9C.png?imageslim)

>因为setting中我们没有注册我们的app: message

**注意：新建的app都要在setting中注册**

### 在setting中注册我们的app
DjangoGetStarted/settings.py 大概36行`INSTALLED_APPS`:

```
`INSTALLED_APPS`
[
    前面的不用变，后面新增下一行
    'message'
]
```

这时候我们重新运行`Tools 菜单下 Run manage.py Task `会提示：

如果提示：
```
SyntaxError: Non-ASCII character '\xe7' in file D:\CodeSpace\PythonProject\DjangoGetStarted\apps\message\models.py on line
```
请注意可能你忘记在写过中文的地方加上:

```
#coding: utf-8
```

**注意必须加在第一或二行。**

然后执行下面命令：

```
makemigrations message
```
![mark](http://myphoto.mtianyan.cn/blog/180107/7j9GC32b44.png?imageslim)

```
migrate message 生成数据表
```
![mark](http://myphoto.mtianyan.cn/blog/180107/dbKECKEBFg.png?imageslim)

前往Navicat验证：

![mark](http://myphoto.mtianyan.cn/blog/180107/26GK5BjhCd.png?imageslim)

>可以看到我们的数据表已经创建成功。默认数据表名称为`app名称_类名转换为小写`
自动生成的id作为主键。

### Models讲解

除过普通的对应数据库的字段类型如`CharField`，还有很多高级类型。如`EmailField`提供email验证。

```
    models.ForeignKey     # 外键
    models.DateTimeField  # 时间字段
    models.IntegerField   # 整型
    models.IPAddressField # IP地址
    models.FileField      # 上传文件
    models.ImageField     # 图片
```

>ctrl按住+左键点击`models` 进入之后点击`fields`拖到文件开始可以看到所有字段：

```
__all__ = [str(x) for x in (
    'AutoField', 'BLANK_CHOICE_DASH', 'BigIntegerField', 'BinaryField',
    'BooleanField', 'CharField', 'CommaSeparatedIntegerField', 'DateField',
    'DateTimeField', 'DecimalField', 'DurationField', 'EmailField', 'Empty',
    'Field', 'FieldDoesNotExist', 'FilePathField', 'FloatField',
    'GenericIPAddressField', 'IPAddressField', 'IntegerField', 'NOT_PROVIDED',
    'NullBooleanField', 'PositiveIntegerField', 'PositiveSmallIntegerField',
    'SlugField', 'SmallIntegerField', 'TextField', 'TimeField', 'URLField',
    'UUIDField',
)]
```

#### 介绍字段参数

`CharField`必须指明默认最大长度。`null=True,blank=True`指明字段可以为空
`defalut = " "`指定默认值。
```
name = models.CharField(max_length=20,null=True,blank=True, verbose_name=u"用户名")
```

id是自动生成的，如果需要自定义主键,message/models.py中添加字段：

```
object_id = models.CharField(primary_key=True, verbose_name="主键")
```

此时点击`Tools 菜单下 Run manage.py Task `输入`makemigrations message`

![mark](http://myphoto.mtianyan.cn/blog/180107/IA82jEgmAG.png?imageslim)

**知识点：CharField必须指明最大长度**

object_id改为：

```
    object_id = models.CharField(primary_key=True, max_length=50 ,verbose_name="主键")
```

这时点击`Tools 菜单下 Run manage.py Task `输入`makemigrations message`

```python
You are trying to add a non-nullable field 'object_id' to usermessage without a default; we can't do that (the database needs something to populate existing rows).
Please select a fix:
 1) Provide a one-off default now (will be set on all existing rows)
 2) Quit, and let me add a default in models.py
```

根据提示信息，我们需要给`object_id`添加默认值：

```
    object_id = models.CharField(primary_key=True, max_length=50,default="", verbose_name="主键")
```
**get新知识点：object_id必须有默认值**

输入`2` 退出：然后输入`makemigrations message`

![mark](http://myphoto.mtianyan.cn/blog/180107/0HhH9l2B9G.png?imageslim)

再输入下面命令生成数据表
```
migrate message 
```

>可以看到上图过程中会告诉我们做了哪些变化，如删除了默认系统生成的主键`id`
,变更了`name`。新增了我们的`object_id`


前往Navicat验证右键设计表：

![mark](http://myphoto.mtianyan.cn/blog/180107/0hADe4ggDG.png?imageslim)

可以看到`object_id`已经成为我们的新主键。

#### 介绍Meta信息：

Meta信息中我们可以指定常见的类型：

```
db_table = "user_meassage"
```

自定义后生成表，表名会与我们的保持一致。而不会前缀`appname`如：`message_`

>这里因为我们已经生成过了，就不要做验证改变表名了。

```
ordering = '-object_id'
```
ordering指定默认排序字段,如：就会以object_id倒序

```
verbose_name_plural = u"用户留言信息"
```
verbose_name_plural：复数信息，便于人阅读。否则会在后台显示`用户留言信息s`

已经学习完毕了`orm`将数据表映射表。
github地址：https://github.com/mtianyan/DjangoGetStarted
此节结束对应github commit:

>留言板数据库orm映射成表完成。内容截止教程3-3结束。

## 3-4 django model的增删改

**github仓库地址：https://github.com/mtianyan/DjangoGetStarted**

- 上小节完成代码对应commit: 留言板数据库orm映射成表完成。内容截止教程3-3结束。

在`message/views.py`中:

```python
from .models import UserMessage
```

将我们刚才创建的model，import进来。`.`代表是与当前同级的目录。

按照下图所示添加一条测试数据。

![mark](http://myphoto.mtianyan.cn/blog/180107/IBga4E2FGh.png?imageslim)

然后再我们的`getform`方法内部添加下面代码：
```
def getform(request):
    # UserMessage默认的数据管理器objects。
    # 方法all()是将所有数据返回成一个queryset类型(django的内置类型)
    all_message = UserMessage.objects.all()

    #我们可以对于all_message进行遍历操作
    for message in all_message:
        # 每个message实际就是一个UserMessage对象（这时我们就可以使用对象的相关方法）。
        print message.name

    return render(request, 'message_form.html')
```

调试过程：

![mark](http://myphoto.mtianyan.cn/blog/180107/FGChlB50k7.png?imageslim)

- 点击上图小红框位置，打上断点。

- 点击Run -> debug后：在浏览器里打开：`http://127.0.0.1:8000/form/`

![mark](http://myphoto.mtianyan.cn/blog/180107/mAebKF06m9.png?imageslim)

- 弹出上图代表已进入断点。

![mark](http://myphoto.mtianyan.cn/blog/180107/0cb6GGiGDa.png?imageslim)

- 此时鼠标左键点击：all_message.可以看到这是一个`{QuerySet}类型的对象，里面存放着[<UserMessage: UserMessage object>]`

- 按`f6`使运行到下一步。此时下方的值窗口内可以看到message的值。说明我们成功取到了数据库的值。

![mark](http://myphoto.mtianyan.cn/blog/180107/hJgD3AC3c2.png?imageslim)


### filter取出指定要求值
```
all_message = UserMessage.objects.filter(name=' mtianyan', address='西安')
```
![mark](http://myphoto.mtianyan.cn/blog/180107/Eal2Ldj6e8.png?imageslim)

按照上面调试过程重新调试可以看到我们同样取出了值。

小练习：将名字改为与自己数据库存放值不同的。查看结果。

![mark](http://myphoto.mtianyan.cn/blog/180107/IChf8L7ecd.png?imageslim)

>变成了空列表，说明一切正确。

### 将数据存入数据库

了解：django/db/models/base.py 源码中提供save方法
```python
def save(self, force_insert=False, force_update=False, using=None,
             update_fields=None):
```

getform方法中添加代码：

```python
 # 存储部分

    # 首先实例化一个对象
    user_message = UserMessage()

    # 为对象增加属性
    user_message.name = "mtianyan2"
    user_message.message = "blog.mtianyan.cn"
    user_message.address = "西安"
    user_message.email = "1147727180@qq.com"
    user_message.object_id = "efgh"

    # 调用save方法进行保存
    user_message.save()
```

- 打上断点：如下图。

![mark](http://myphoto.mtianyan.cn/blog/180107/3b7aeEg0KE.png?imageslim)

- 一直惦记f6单步调试，直到如下图：蓝色到`return`语句

![mark](http://myphoto.mtianyan.cn/blog/180107/m2fF7j38dC.png?imageslim)

可以在下方值窗口查看到值

![mark](http://myphoto.mtianyan.cn/blog/180107/bg6ICDcI9I.png?imageslim)

### Navicat进行验证

>可以看到成功的添加了数据`mtianyan2`

![mark](http://myphoto.mtianyan.cn/blog/180107/DiBKcaJd8A.png?imageslim)

### 如何从html的提交中取到数据并保存进数据库

templates/message_form.html：

![mark](http://myphoto.mtianyan.cn/blog/180107/glha3bHaC8.png?imageslim)

>method是post。action就是指向我们在urls.py中配置的`/form/`
**前面必须加斜杠指根路径下form**
里面的input会自动把值传递给后台：这时我们就可以在getform中取到刚才传递过来的值。

运行项目：然后输入需要填写的值。点击提交：出现403错误

```
Forbidden (403)
CSRF verification failed. Request aborted.
```

>根据提示：我们的页面没有进行crsf的验证，这时django的安全机制，不允许任意form都往后台提交。

**知识点：所以我们需要在html页面中加入csrf_token**

```
    {% csrf_token %}
```

![mark](http://myphoto.mtianyan.cn/blog/180107/chCamk6JDk.png?imageslim)

原有那行删除掉。打上断点

![mark](http://myphoto.mtianyan.cn/blog/180107/3cCBcF96eC.png?imageslim)

刷新页面并提交。这时候在值窗口可以看到request对象下的POST中存放着我们提交的数据。内容如下

```
<QueryDict: {u'message': [u'\u54c8\u54c8'], u'address': [
u'\u897f\u5b89\u5e02'], u'csrfmiddlewaretoken': [
u'uIYSMOTWPJBPOPucRwd3uDaWtCzeEaem'], u'name': [
u'\u5929\u6daf\u660e\u6708\u7b19'], u'email': [u'1147727180@qq.com']}>
```

![mark](http://myphoto.mtianyan.cn/blog/180107/3BL02H2ljG.png?imageslim)

>数据以dict：key-value 形式存储 key是由如下图html中的name所决定对应的。

![mark](http://myphoto.mtianyan.cn/blog/180107/c2lIdeH2A1.png?imageslim)

### 数据库新增。

`request.POST`中数据取出，存入`user_message`对象

```python
 # html表单部分

    # 此处对应html中的method="post"，表示我们只处理post请求
    if request.method == "POST":
        # 就是取字典里key对应value值而已。取name，取不到默认空
        name = request.POST.get('name', '')
        message = request.POST.get('message', '')
        address = request.POST.get('address', '')
        email = request.POST.get('email', '')

        # 实例化对象
        user_message = UserMessage()

        # 将html的值传入我们实例化的对象.
        user_message.name = name
        user_message.message = message
        user_message.address = address
        user_message.email = email
        user_message.object_id = "ijkl"

        # 调用save方法进行保存
        user_message.save()
```

- 打断点在下图位置：

![mark](http://myphoto.mtianyan.cn/blog/180107/gblC5dg219.png?imageslim)

- 进入调试：点击点击method：是get请求。因为我们并没有按提交按钮，而是get这个网页

![mark](http://myphoto.mtianyan.cn/blog/180107/heblbcAf4h.png?imageslim)

- 点击f8继续运行我们的项目 浏览器中填写表单内容点提交。

![mark](http://myphoto.mtianyan.cn/blog/180107/33ECK331eE.png?imageslim)

>因为这次是表单提交，已经变成了post方式。按`f6`进行单步调试。

一直单步到如下图蓝色

![mark](http://myphoto.mtianyan.cn/blog/180107/4Ck700a9Ea.png?imageslim)

这时候值浏览窗口可以看到

![mark](http://myphoto.mtianyan.cn/blog/180107/i22jKb99Bh.png?imageslim)

>检查我们的user_message对象的属性是否已经全部添加进去，

使用f8 继续项目并前往Navicat验证

![mark](http://myphoto.mtianyan.cn/blog/180107/0mJgFKbi9k.png?imageslim)

>可以看到我们的数据库中已经新增，标志着我们已经成功存入数据。

### 删除数据。

对于查询到的数据做删除：

```python
# 方法2 :filter取出指定条件值，逗号代表and 必须同时满足两个条件才返回。
all_message = UserMessage.objects.filter(name='mtianyan', address='西安')

# 我的数据库里保存着可以匹配到该条数据的一行。

# 删除操作：使用delete方法删除all_message

all_message.delete()

    for message in all_message:
        # 删除取到的message对象
        message.detele()
        # print message.name
```

点击run并访问：http://127.0.0.1:8000/form/
进入Navicat进行验证。

![mark](http://myphoto.mtianyan.cn/blog/180107/BamdmLI1Ec.png?imageslim)

>可以看到我们的那条mtianyan + 西安的数据已经被删除。

**至此：我们已经学会了新增，删除，查询。**

本节结束github对应commit：

>django model的增删改数据库。本次内容截止教程3-4。 

## 3-5 django url templates配置

>项目Github地址：https://github.com/mtianyan/DjangoGetStarted
>本节开始对应对应Github的commit：django model的增删改数据库。本次内容截止教程3-4。

本节将介绍url的配置，以及如何将数据库数据填充回前台html页面。

情景：只允许用户修改`mtianyan`，如果没有就添加，如果有就回填使用户可以修改。

### 取出数据

message/views.py中的getform方法中

```python
    message = None
    all_message = UserMessage.objects.filter(name='mtianyan', address='西安')

    # if 判断是否存在数据
    if all_message:
        # all_message是一个list，可以使用切片。
        message = all_message[0]

```

>这里注意把前几节写的删除掉


### 将数据回填至html中

#### 修改return render

```
return render(request, 'message_form.html',{
        "my_message" : message
})   
```

>这里前面的"my_meassage"是我们可以自行命名的。会有一个`my_message`对象随着返回前端页面。

#### 在前端页面中放入值。

为input系列标签添加`value`: 使用`my_message.name`取到我们传递过来的`my_message`对象的属性值。

```
        <input id="name" type="text" name="name"  
        value="{{ my_message.name }}" class="error" placeholder="请输入您的姓名"/>
```

>请自行完成姓名，邮箱，联系地址三个`input`标签。

为`textarea`标签添加值

![mark](http://myphoto.mtianyan.cn/blog/180107/F60Dl7jf93.png?imageslim)

```
        <textarea id="message" name="message"  
        placeholder="请输入你的建议">{{ my_message.message }}</textarea>
```

运行项目，访问：http://127.0.0.1:8000/form/

![mark](http://myphoto.mtianyan.cn/blog/180107/27BFK0ieIL.png?imageslim)

>成功！！我们已经将后台数据库数据成功展示到前台。

### template模板渲染中的一些用法。

>在我们的template模板中也就是form.html中，不允许我们写Python的语法，
它提供了一套自己的内建标签。

[官方文档中template内建标签用法传送门](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/)

#### 常用的几种模板标签介绍：

##### `if - else`

官方提供模板如下：

![mark](http://myphoto.mtianyan.cn/blog/180107/mhJlLmCiLh.png?imageslim)

个人实践：

![mark](http://myphoto.mtianyan.cn/blog/180107/Ahch4LBcKd.png?imageslim)

满足if运行结果：

![mark](http://myphoto.mtianyan.cn/blog/180107/kBb2Ak6ec0.png?imageslim)

不满足if：如改为`my_message.name == "mtianyan1"`运行结果：

![mark](http://myphoto.mtianyan.cn/blog/180107/5c6fK8mDAK.png?imageslim)

##### `ifequal` & `ifnotequal`

![mark](http://myphoto.mtianyan.cn/blog/180107/he6fBLk1le.png?imageslim)

官方文档解释：`ifequal a b` 相当于`f a == b `.`ifnotequal`则相当于`if a != b `

个人实践：
![mark](http://myphoto.mtianyan.cn/blog/180107/ihKmHmCLcD.png?imageslim)

结果为：未找到中文昵称

##### slice

![mark](http://myphoto.mtianyan.cn/blog/180107/DccKL0EB4C.png?imageslim)

官方文档解释：其实就是切片操作。从头开始切到第n个。

个人实践：

![mark](http://myphoto.mtianyan.cn/blog/180107/m8jJE8KEae.png?imageslim)

>本来`mtianyan` 与 `mtianyan1`是不同的，但是切片后前八位相同。
运行结果显示 ：`对应中文昵称：天涯明月笙`

### URl的别名设置技巧

DjangoGetStarted/urls.py：

为`r'^form/$'`添加别名：

```python
    url(r'^form/$', getform, name = "form_new")
```

前往html中修改action地址为下面所示：

```
<form action="{% url "form_new" %}" method="post" class="smart-green">
```

这时我们如果改动urls.py中的`r'^form/$'`不需要再修改前端代码中值。

### url先后顺序问题

**注意**url匹配规则中一定不要忘记`/$`符号代表以`form/`结束的才会有效。不会向后继续匹配。比如没有`/$`

```
    url(r'^form', getform, name="form_new")
```

这时我们进入浏览器访问时输入`http://127.0.0.1:8000/formemmm`都可以被响应。

![mark](http://myphoto.mtianyan.cn/blog/180107/aehl7G2K20.png?imageslim)

特别是如果底下还配置有被这个规则包含的条目，会产生被写在更靠前的拦截住得不到正确处理的Bug。

![mark](http://myphoto.mtianyan.cn/blog/180107/jm5AJLLmGd.png?imageslim)

>上图我们是想要让formtest响应admin.site.urls。但是会被form提前拦截住。

所以我们一定要注意加上`/$`符号。

至此我们完成了留言板项目：学习到了Django必备的基础知识。
下一章我们将开始我们的进阶学习：开发在线教育平台网站。

本章结束：

>对应Commit: 留言板项目学习完成，本次内容截止教程3-5。完结，撒花。
项目Github地址：https://github.com/mtianyan/DjangoGetStarted


{% cq %}  数据基础决定上层建筑 {% endcq %}

{% note warning %} 设计数据库是整个项目的第一项工作:
- 完成django的app设计 & 完成app中的models设计

Django1.9.8对应github: https://github.com/mtianyan/Mxonline2
Django2.0.1对应github: https://github.com/mtianyan/Mxonline3
{% endnote %}

# 完成django的app设计 & 完成app中的models设计

## 4-1 使用py3.6和django1.11开发系统前注意事项

直接通过Python3.6和django最新版本来开发我们的系统的一些注意事项。

>原版本: Python 2.7 & django 1.9.8
现在版本：Python 3.6 & django 1.11

我个人使用: 3.5 + django2.0.1 & 2.7 + django 1.9.8

直接从3.6上手，开始工作，而不用做完2.7再转换。

>代码几乎100%兼容2.7 & 3.6

### 虚拟环境问题

>Python2.7 与 Python3.x共存并创建虚拟环境。

```
mkvirtualenv -p C:\...\python.exe mxonline
```

### 设计model的时候的`__unicode__`方法

Python2.7 中:

```python
def __unicode__:
	return self.name
```
Python 3.x中:
```python
def __str__(self):
	return self.name
```

>3.x下重载Unicode不会报错，但是会在后台显示有问题。

### 安装Python的mysql驱动时不能用之前的 MYSQL python

>这个网址是windows下python包安装的居家必备良品，建议收藏。

https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python

应该改用`Mysqlclient`来替换我们的`MySQl-python`

>接口是一样的。所以以后建议直接用Mysqlclient，因为它2, 3版本都有。

### 通过源码方式安装xadmin时。

>Github 搜索 `mxonline_resources`，将里面的Xadmin放进extras_apps中。
就不用官方的了。

django 2.0.1 的修复bug版可以使用我的:

https://github.com/mtianyan/xadmin_django2.0.1

>也可以直接使用官方的新版，已经支持了Python3.6

Xadmin安装一定要安装依赖包

```
django-crispy-forms=1.6.0
django-import-export>=0.5.1
django-reversion~=2.0.0
django-formtools
future==0.15.2
httplib2==0.9.2
six==1.10.0
```
### 使用DjangoUeditor

官方的不支持Python3, 去`mxonline_resource`目录下载兼容Python3的版本。
放入`extras_apps`

## 4-2 django-app 设计

>数据库设计

### 根据app设计 models

### 数据表生成与修改

授课机构提供讲师录制课程，学员完成在线学习。

- 全局头部：用户消息 & 个人中心: 没有登录时，就是登录注册
- 对于公开课，授课讲师，授课机构进行搜索。
- 轮播图，课程，机构，页脚
- 公开课：分页公开课，右边热门推荐。
- 点进课程：课程详情页。详情: 后台富文本。右边是课程机构的介绍。收藏 或学习
- 章节信息 & 课程资源下载 & 评论
- 授课讲师: 授课讲师列表页,  讲师排行榜。分页。
- 点进讲师: 看到课程。
- 授课机构: 类别筛选，机构性质，所在地区 & 排序。用户提交表单，我要学习, 机构排名.
- 个人中心: 修改密码, 修改头像, 个人信息, 我的课程, 我的收藏, 我的消息。

app大致会有`用户模块`,`课程模块`,`授课教师`与`授课机构`。

![mark](http://myphoto.mtianyan.cn/blog/180108/DB9D66LmaJ.png?imageslim)

多一个operation app 是因为数据库的需要。后面会讲。

## 4-3 新建项目

### Python2.7 创建虚拟环境。

```
mkvirtualenv mxonline2
```

安装django

```
pip install django==1.9.8 
```

>注意Python2下此处必须用1.9.8

![mark](http://myphoto.mtianyan.cn/blog/180108/JJamFecfhC.png?imageslim)

### Python3.x 创建虚拟环境

如果你已经通过我的博文《Python开发环境搭建指南(Anaconda2,3共存)》
搭建了完美的共存环境使用下面命令创建虚拟环境

```
mkvirtualenv -p D:\softEnvDown\Anaconda2\envs\py3\python.exe mxonline3
```
>-p后面路径为自己的Python3的exe文件路径。

![mark](http://myphoto.mtianyan.cn/blog/180108/i6lKIGdE93.png?imageslim)

>官方说明的最新稳定版为2.0.1(2018-01-08 19:37:06)

```
workon mxonline3
pip install django==2.0.1
```

![mark](http://myphoto.mtianyan.cn/blog/180108/I1fF3aL00H.png?imageslim)

至此我们的两个虚拟环境都已经准备好了。

### 新建Python2 下Project

为Mxonline2 配置环境 `mxonline2`

![mark](http://myphoto.mtianyan.cn/blog/180108/3Ic2ehmkGK.png?imageslim)

注意一直定位到Python.exe。


#### 安装mysql驱动。

下载https://www.lfd.uci.edu/~gohlke/pythonlibs/#mysql-python中
mysqlclient‑1.3.12‑cp34‑cp34m‑win_amd64.whl进行本地安装

```
workon mxonline2
pip install mysqlclient-1.3.12-cp27-cp27m-win_amd64.whl

```

![mark](http://myphoto.mtianyan.cn/blog/180108/8dK5e5clJB.png?imageslim)


### 新建Python3 下Project


为Mxonline3 配置环境 `mxonline3`

![mark](http://myphoto.mtianyan.cn/blog/180108/383ceKe92C.png?imageslim)

>注意一直定位到Python.exe。


#### 安装mysql驱动。

```
workon mxonline3
pip install mysqlclient
```

### setting中配置

Mxonline2/settings.py:
Mxonline3/settings.py:

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mxonline2',
        'USER': 'root',
        'PASSWORD': '你的密码',
        'HOST':'127.0.0.1'

    }
}
```

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mxonline3',
        'USER': 'root',
        'PASSWORD': '你的密码',
        'HOST':'127.0.0.1'

    }
}
```

### 前往Navicat新建数据库

mxonline2 & mxonline3

#### 进行数据库初始化makemigrations

点击`Tools 菜单下 Run manage.py Task `

```
makemigrations
migrate
```

>2,3操作一致

点击 RUn edit

![mark](http://myphoto.mtianyan.cn/blog/180108/al0KDCbiK6.png?imageslim)

可以为2,3配置不同的port。比如2: 8002 & 3: 8003

2: 点击run运行: django1.9.8成功画面如下。

![mark](http://myphoto.mtianyan.cn/blog/180108/628mmAGLID.png?imageslim)

3: 点击run运行: django2.0.1成功画面如下。

![mark](http://myphoto.mtianyan.cn/blog/180108/GeEcJgAbEA.png?imageslim)

这时我们的项目就新建成功。

此处对应commit:

>项目初始化成功: 完成数据库Migration初始化。 对应4-3

## 4-4 自定义userprofile

点击`Tools 菜单下 Run manage.py Task `

```
startapp users
```

### 编写我们的model设计user表。

系统自动生成的user表如下:

![mark](http://myphoto.mtianyan.cn/blog/180108/H6jBl0IKjb.png?imageslim)

- id: 主键, password 密码, last_login Django自动记录用户最后登录时间,。
- is_superuser 表明用户是否是超级用户(后台管理会用到)。
- username 用户名字段不要随便改动, email 邮箱, 
- is_staff 表示是否是员工(后台管理会用到)。
- is_active 用户是否是激活状态, date_joined 注册时间。

>我们需要扩展我们自己的需求字段。

个人中心页面中:

![mark](http://myphoto.mtianyan.cn/blog/180108/mghmfD45hJ.png?imageslim)

可以看到我们还需要的有：

- 昵称: nickname
- 生日: birthday
- 性别: gender

User表的自定义方法可以查看django官方文档。
我们既想保留原有字段，又想有新字段。

users/models.py(3把Unicode改为str)添加代码:

```python
from django.contrib.auth.models import AbstractUser

class UserProfile(AbstractUser):
    # 自定义的性别选择规则
    GENDER_CHOICES = (
        ("male", u"男"),
        ("female", u"女")
    )
    # 昵称
    nick_name = models.CharField(max_length=50, verbose_name=u"昵称", default="")
    # 生日，可以为空
    birthday = models.DateField(verbose_name=u"生日", null=True, blank=True)
    # 性别 只能男或女，默认女
    gender = models.CharField(
        max_length=5,
        verbose_name=u"性别",
        choices=GENDER_CHOICES,
        default="female")
    # 地址
    address = models.CharField(max_length=100, verbose_name="地址", default="")
    # 电话
    mobile = models.CharField(max_length=11, null=True, blank=True)
    # 头像 默认使用default.png
    image = models.ImageField(
        upload_to="image/%Y/%m",
        default=u"image/default.png",
        max_length=100
    )
    
    # meta信息，即后台栏目名
    class Meta:
        verbose_name = "用户信息"
        verbose_name_plural = verbose_name

    # 重载Unicode方法，打印实例会打印username，username为继承自abstractuser
    def __unicode__(self):
        return self.username
```

点进`AbstractUser`可以看到这个models里面就有我们默认表的那些字段。

因为Image字段需要用到`pillow`所以需要安装该库

```
pip install pillow
```
**注意：CharField必须有max_length, Imagefield实际也是charfield所以也要有max_length**

#### setting设置INSTALLED_APPS & AUTH_USER_MODEL。

- INSTALLED_APPS注册app

```
'users'
```

- 重载AUTH_USER_MODEL

```
# 此处重载是为了使我们的UserProfile生效
AUTH_USER_MODEL = "users.UserProfile"
```

![mark](http://myphoto.mtianyan.cn/blog/180108/JDik7FIb8k.png?imageslim)

点击`Tools 菜单下 Run manage.py Task `

```
makemigrations users
migrate users
```

![mark](http://myphoto.mtianyan.cn/blog/180108/ijGBh98JL6.png?imageslim)

>上图中可以看到数据库做出的改动。输入: yes

### 进入Navicat进行验证

![mark](http://myphoto.mtianyan.cn/blog/180108/79bbD88gJD.png?imageslim)

如上图可以看到我们的表已经生成成功。

### 附加Python3下不同与报错：

将Unicode方法改为str方法
```
    # 重载__str__方法，打印实例会打印username，username为继承自AbstractUser
    def __str__(self):
        return self.username
```

报错: 

```
django.db.migrations.exceptions.InconsistentMigrationHistory: Migration
admin.0001_initial is applied before its dependency users.0001_initial on
database 'default'
```

解决方案:

```
删除数据库中 除了auth_user的其他表
```

然后执行命令:

```
makemigrations
migrate
makemigrations users
migrate users
```
![mark](http://myphoto.mtianyan.cn/blog/180108/gBLe65jc53.png?imageslim)

>共11张表，同期django1.9.8会产生13张表

![mark](http://myphoto.mtianyan.cn/blog/180108/C3h6f7d4J5.png?imageslim)

>我推测是因为在django2.0版本中。我们如果自定义了userProfile并且在setting中进行了设置。那么auth_user将不再拥有多的表。

下次不要再初始化时执行makemigrations & migrate。当我们设计userProfile完成之后再执行。

本小节完成对应commit:

>完成USerProfile models书写。makemigrations & migrate 建表成功。对应4-4


## 4-5 user modesl.py设计

循环引用:

>设计app时每个app都有model

![mark](http://myphoto.mtianyan.cn/blog/180109/LedJLC8e34.png?imageslim)

如图：我们在user中定义usercourse记录用户学习的课程。会有两个外键：user和course。
我们就会`import Courses.models`

如果用户对课程的评论：会放在 `Courses.models`当中。评论我们需要保存相应的用户。
我们就会`import User.models`

循环import会出错。a与b相互调用，造成等待。

### 解决循环引用: 分层设计

目前已有app：users courses organization

另外一个app高于这些app的层级。`operation`.上一层app可以import下层的app。

![mark](http://myphoto.mtianyan.cn/blog/180109/kmDB89IcFF.png?imageslim)

上节中: 自定义`userprofile` 覆盖默认`user`表

user中还需要添加的(前提是这些功能比较独立):

- EmailVerifyRecord - 邮箱验证码
- PageBanner - 轮播图

观察轮播图:

>1. 图片 2. 点击图片地址 3. 轮播图序号(控制前后)

![mark](http://myphoto.mtianyan.cn/blog/180109/fg4J5a2Kb5.png?imageslim)

users/models.py中添加代码:

```python
from datetime import datetime

# 邮箱验证码model


class EmailVerifyRecord(models.Model):
    SEND_CHOICES = (
        ("register", u"注册"),
        ("forget", u"找回密码")
    )
    code = models.CharField(max_length=20, verbose_name=u"验证码")
    # 未设置null = true blank = true 默认不可为空
    email = models.EmailField(max_length=50, verbose_name=u"邮箱")
    send_type = models.CharField(choices=SEND_CHOICES, max_length=10)
    # 这里的now得去掉(),不去掉会根据编译时间。而不是根据实例化时间。
    send_time = models.DateTimeField(default=datetime.now)

    class Meta:
        verbose_name = "邮箱验证码"
        verbose_name_plural = verbose_name

# 轮播图model


class Banner(models.Model):
    title = models.CharField(max_length=100, verbose_name=u"标题")
    image = models.ImageField(
        upload_to="banner/%Y/%m",
        verbose_name=u"轮播图",
        max_length=100)
    url = models.URLField(max_length=200, verbose_name=u"访问地址")
    # 默认index很大靠后。想要靠前修改index值。
    index = models.IntegerField(default=100, verbose_name=u"顺序")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"轮播图"
        verbose_name_plural = verbose_name
```

从上往下: 第一块区域import官方包，第二块import第三方。(PEP8)

![mark](http://myphoto.mtianyan.cn/blog/180109/8cmDm7ADf8.png?imageslim)

如下图: 我们一共创建了三个数据表: Structure可以查看到

![mark](http://myphoto.mtianyan.cn/blog/180109/7ABfdDCf7C.png?imageslim)

>与用户相关的评论啊，点赞啊。学习的课程啊并没有放进来，因为那些独立性不高。
容易产生循环引用。我们把那些放到operation中。

本小节完成，对应commit:

> Usermodel添加邮箱验证码，首页轮播图。对应4-5

## 4-6 course models.py编写

点击 `Tools 菜单下 Run manage.py Task `

```
startapp courses
```

course中需要那些表:

- 课程本身需要一张表

![mark](http://myphoto.mtianyan.cn/blog/180109/c9eBEHb0mL.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180109/75hlgK7481.png?imageslim)

- 点进去之后点击开始学习。

- 课程基本信息需要一张表, 章节表与课程表存在(一个课程对应多个章节)
- 章节表中：章节的名称。 章节与视频(一个章节对应多个视频)

结构: 课程本身--(一对多)>章节-(一对多)->视频信息

资源下载放在课程里面的。一个课程对应多个资源

共四张表：课程本身--(一对多)>章节-(一对多)->视频信息 & 资源表

![mark](http://myphoto.mtianyan.cn/blog/180109/Kec5994359.png?imageslim)

courses/models.py:

```python
from datetime import datetime

# 课程信息表
class Course(models.Model):
    DEGREE_CHOICES = (
        ("cj", u"初级"),
        ("zj", u"中级"),
        ("gj", u"高级")
    )
    name = models.CharField(max_length=50, verbose_name=u"课程名")
    desc = models.CharField(max_length=300, verbose_name=u"课程描述")
    # TextField允许我们不输入长度。可以输入到无限大。暂时定义为TextFiled，之后更新为富文本
    detail = models.TextField(verbose_name=u"课程详情")
    degree = models.CharField(choices=DEGREE_CHOICES, max_length=2)
    # 使用分钟做后台记录(存储最小单位)前台转换
    learn_times = models.IntegerField(default=0, verbose_name=u"学习时长(分钟数)")
    # 保存学习人数:点击开始学习才算
    students = models.IntegerField(default=0, verbose_name=u"学习人数")
    fav_nums = models.IntegerField(default=0, verbose_name=u"收藏人数")
    image = models.ImageField(
        upload_to="courses/%Y/%m",
        verbose_name=u"封面图",
        max_length=100)
    # 保存点击量，点进页面就算
    click_nums = models.IntegerField(default=0, verbose_name=u"点击数")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"课程"
        verbose_name_plural = verbose_name
```

下面来编写章节 & 视频 & 课程资源:`courses/models.py`

一对多, 多对一都可以使用django的外键来完成。

```python
# 章节
class Lesson(models.Model):
    # 因为一个课程对应很多章节。所以在章节表中将课程设置为外键。
    # 作为一个字段来让我们可以知道这个章节对应那个课程
    course = models.ForeignKey(Course, verbose_name=u"课程")
    name = models.CharField(max_length=100, verbose_name=u"章节名")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"章节"
        verbose_name_plural = verbose_name


# 每章视频
class Video(models.Model):
    # 因为一个章节对应很多视频。所以在视频表中将章节设置为外键。
    # 作为一个字段来存储让我们可以知道这个视频对应哪个章节.
    lesson = models.ForeignKey(Lesson, verbose_name=u"章节")
    name = models.CharField(max_length=100, verbose_name=u"视频名")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"视频"
        verbose_name_plural = verbose_name


# 课程资源
class CourseResource(models.Model):
    # 因为一个课程对应很多资源。所以在课程资源表中将课程设置为外键。
    # 作为一个字段来让我们可以知道这个资源对应那个课程
    course = models.ForeignKey(Course, verbose_name=u"课程")
    name = models.CharField(max_length=100, verbose_name=u"名称")
    # 这里定义成文件类型的field，后台管理系统中会直接有上传的按钮。
    # FileField也是一个字符串类型，要指定最大长度。
    download = models.FileField(
        upload_to="course/resource/%Y/%m",
        verbose_name=u"资源文件",
        max_length=100)
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"课程资源"
        verbose_name_plural = verbose_name
```

通过Structure可以看到我们刚才设计的四张表

![mark](http://myphoto.mtianyan.cn/blog/180109/e3081f8bJh.png?imageslim)

本小节完毕, 对应commit:

>设计完成课程app中四张数据表: 课程，章节，视频，资源。对应4-6

## 4-7 organization modesl.py设计

新建课程机构app:

点击`Tools 菜单下 Run manage.py Task `

```
startapp organization
```

课程是属于机构的, 机构有机构类别，城市等字段。讲师实体。
我要学习的提交表单会与用户关联，存放在机构。

![mark](http://myphoto.mtianyan.cn/blog/180109/K1faIbEA3A.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180109/1L2lebKCl0.png?imageslim)

其中课程数，学习人数可以动态统计。机构地址，机构经典课程。

>机构讲师，机构课程可以通过外键获取到, 不保存到机构中。

![mark](http://myphoto.mtianyan.cn/blog/180109/DlgdiG6K16.png?imageslim)

>讲师大概所需要的字段如图所示。

organization/models.py 代码如下：

```python
# encoding : utf-8
from datetime import datetime

from django.db import models

# Create your models here.


# 城市字典
class CityDict(models.Model):
    name = models.CharField(max_length=20, verbose_name=u"城市")
    # 城市描述：备用不一定展示出来
    desc = models.CharField(max_length=200, verbose_name=u"描述")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"城市"
        verbose_name_plural = verbose_name


# 课程机构
class CourseOrg(models.Model):
    name = models.CharField(max_length=50, verbose_name=u"机构名称")
    # 机构描述，后面会替换为富文本展示
    desc = models.TextField(verbose_name=u"机构描述")
    click_nums = models.IntegerField(default=0, verbose_name=u"点击数")
    fav_nums = models.IntegerField(default=0, verbose_name=u"收藏数")
    image = models.ImageField(
        upload_to="org/%Y/%m",
        verbose_name=u"封面图",
        max_length=100)
    address = models.CharField(max_length=150, verbose_name=u"机构地址")
    # 一个城市可以有很多课程机构，通过将city设置外键，变成课程机构的一个字段
    # 可以让我们通过机构找到城市
    city = models.ForeignKey(CityDict, verbose_name=u"所在城市")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"课程机构"
        verbose_name_plural = verbose_name


# 讲师
class Teacher(models.Model):
    # 一个机构会有很多老师，所以我们在讲师表添加外键并把课程机构名称保存下来
    # 可以使我们通过讲师找到对应的机构
    org = models.ForeignKey(CourseOrg, verbose_name=u"所属机构")
    name = models.CharField(max_length=50, verbose_name=u"教师名称")
    work_years = models.IntegerField(default=0, verbose_name=u"工作年限")
    work_company = models.CharField(max_length=50, verbose_name=u"就职公司")
    work_position = models.CharField(max_length=50, verbose_name=u"公司职位")
    points = models.CharField(max_length=50, verbose_name=u"教学特点")
    click_nums = models.IntegerField(default=0, verbose_name=u"点击数")
    fav_nums = models.IntegerField(default=0, verbose_name=u"收藏数")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"教师"
        verbose_name_plural = verbose_name
```

![mark](http://myphoto.mtianyan.cn/blog/180109/fi284KlfDk.png?imageslim)

>可以看到我们一共创建了三张表：分别是城市，课程机构，讲师。

本小节对应commit:

>课程机构app：城市，机构，讲师表书写完毕。对应4-7

##  4-8 operation models.py设计

分析需要那些表:

- 用户可以提交我要学习的个人需求。
- 学员的课程评论信息
- 收藏：可以收藏公开课, 授课讲师, 授课机构, 用户消息提醒。
- 个人中心：我的课程说明用户和课程之间的学习关系也需要保存。

![mark](http://myphoto.mtianyan.cn/blog/180109/5k6HkC49im.png?imageslim)

新建操作app:

点击`Tools 菜单下 Run manage.py Task `

```
startapp operation
```
operation/models.py添加代码:

```python
# encoding: utf-8
from datetime import datetime

# 引入我们CourseComments所需要的外键models
from users.models import UserProfile
from courses.models import Course

# 用户我要学习表单
class UserAsk(models.Model):
    name = models.CharField(max_length=20, verbose_name=u"姓名")
    mobile = models.CharField(max_length=11, verbose_name=u"手机")
    course_name = models.CharField(max_length=50, verbose_name=u"课程名")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"用户咨询"
        verbose_name_plural = verbose_name


# 用户对于课程评论
class CourseComments(models.Model):

    # 会涉及两个外键: 1. 用户， 2. 课程。import进来
    course = models.ForeignKey(Course, verbose_name=u"课程")
    user = models.ForeignKey(UserProfile, verbose_name=u"用户")
    comments = models.CharField(max_length=250, verbose_name=u"评论")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"评论时间")

    class Meta:
        verbose_name = u"课程评论"
        verbose_name_plural = verbose_name


# 用户对于课程,机构，讲师的收藏
class UserFavorite(models.Model):
    # 会涉及四个外键。用户，课程，机构，讲师import
    TYPE_CHOICES = (
        (1, u"课程"),
        (2, u"课程机构"),
        (3, u"讲师")
    )

    user = models.ForeignKey(UserProfile, verbose_name=u"用户")
    # course = models.ForeignKey(Course, verbose_name=u"课程")
    # teacher = models.ForeignKey()
    # org = models.ForeignKey()
    # fav_type =

    # 机智版
    # 直接保存用户的id.
    fav_id = models.IntegerField(default=0)
    # 表明收藏的是哪种类型。
    fav_type = models.IntegerField(
        choices=TYPE_CHOICES,
        default=1,
        verbose_name=u"收藏类型")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"评论时间")

    class Meta:
        verbose_name = u"用户收藏"
        verbose_name_plural = verbose_name


# 用户消息表
class UserMessage(models.Model):
        # 因为我们的消息有两种:发给全员和发给某一个用户。
        # 所以如果使用外键，每个消息会对应要有用户。很难实现全员消息。

        # 机智版 为0发给所有用户，不为0就是发给用户的id
    user = models.IntegerField(default=0, verbose_name=u"接收用户")
    message = models.CharField(max_length=500, verbose_name=u"消息内容")

    # 是否已读: 布尔类型 BooleanField False未读,True表示已读
    has_read = models.BooleanField(default=False, verbose_name=u"是否已读")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"用户消息"
        verbose_name_plural = verbose_name


# 用户课程表
class UserCourse(models.Model):
    # 会涉及两个外键: 1. 用户， 2. 课程。import进来
    course = models.ForeignKey(Course, verbose_name=u"课程")
    user = models.ForeignKey(UserProfile, verbose_name=u"用户")
    add_time = models.DateTimeField(default=datetime.now, verbose_name=u"添加时间")

    class Meta:
        verbose_name = u"用户课程"
        verbose_name_plural = verbose_name
```

至此：我们的五张operation下的数据表models设计完成

![mark](http://myphoto.mtianyan.cn/blog/180109/BHHfi6Gj2J.png?imageslim)

### setting中配置添加app

![mark](http://myphoto.mtianyan.cn/blog/180109/9IJa5kgFAG.png?imageslim)

本小节对应commit:

>operation下的models设计,用户: 课程&消息&收藏&评论&我要学习.并在setting中进行了注册。对应4-8

## 4-9 数据表生成以及apps目录建立

>学习如何通过刚才设计的models生成数据库对应的表

点击`Tools 菜单下 Run manage.py Task `:

### Python2与Python3不同:

Python2下可能会报一些`noASCII`错误:

只需要在对应你写了中文的第一行加上:

```
# encoding: utf-8
```

### Python3(django2.0.1)会报错:

```
org = models.ForeignKey(CourseOrg, verbose_name=u"所属机构")
TypeError: __init__() missing 1 required positional argument: 'on_delete'
```

>这是因为在2.0.1中，外键关系必须指明删除时的操作。

比如：出租车都归属于出租车公司。如果出租车公司倒闭了，那这些汽车该怎么处理。
必须自己指明: 我觉得可以直接进行级联删除。

django提供了:

- `CASCADE`
- `PROTECT`
- `SET_NULL`
- `SET_DEFAULT`

等选项。我选择了`CASCADE`删除。

将(dajngo 2.0.1)项目中所有的外键修改为如下面代码所示：
>也就是添加了`on_delete=models.CASCADE`使其级联删除。

```python
org = models.ForeignKey(CourseOrg, on_delete=models.CASCADE, verbose_name=u"所属机构")
```

### makemirgration & migrate生成表

```
makemirgration
migrate
```

![mark](http://myphoto.mtianyan.cn/blog/180109/mdib8gdGHc.png?imageslim)

上图为makemirgration过程中输出的信息。可以看到我们做出的改动

![mark](http://myphoto.mtianyan.cn/blog/180109/B01J3JChmd.png?imageslim)

此时我们查看app目录中migrations文件夹可以看到产生的新文件。

`operation/migrations/0001_initial.py:`

>可以看到里面也是Python的语法。他会帮我们生成数据表。
以后每次`migrations`时都会生成新的initial文件。这是很重要的变动文件，不能随意删除。

打开Navicat可以看到django的数据库中有它默认的django_migrations表

![mark](http://myphoto.mtianyan.cn/blog/180109/i7Cc4HHBgh.png?imageslim)

双击django_migrations表可以看到我们migration的记录。

![mark](http://myphoto.mtianyan.cn/blog/180109/kE5Fc9kjc7.png?imageslim)

>会记录哪个app下的哪个initial.py已经运行了。

进入Navicat进行成功性验证:

![mark](http://myphoto.mtianyan.cn/blog/180109/Bd16J68e9k.png?imageslim)

>可以看到我们的表已经生成成功,命名规则为: app名称 + 我们的类名变成小写

### 把我们的四个app放到一个文件夹下。

- 新建Python的package: apps 

![mark](http://myphoto.mtianyan.cn/blog/180109/7l4AG2maAD.png?imageslim)

- 把四个app都拖进apps中去。

![mark](http://myphoto.mtianyan.cn/blog/180109/mGLjCiL8aj.png?imageslim)

去掉`searchfor`的勾选。拖进去之后会报错，说找不到那些import的模块了。

解决方案：右键`Mark`为`sourceRoot`。根目录下找不到的，会去apps下搜索。

但是这时候cmd下还是会报错。

解决方案(图来源于我的`DjangoGetStarted`教程):

![mark](http://myphoto.mtianyan.cn/blog/180107/IhD2bJDI6K.png?imageslim)

同理,插入第0是希望它先搜索我们app下东西：

![mark](http://myphoto.mtianyan.cn/blog/180109/biF9eAhLHi.png?imageslim)

#### 成功性验证

![mark](http://myphoto.mtianyan.cn/blog/180109/hJc05K1b28.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180109/BH84IH9beb.png?imageslim)

>可以看到Django已经可以正常run成功了。

### 第四章总结

- 我们设计了app

![mark](http://myphoto.mtianyan.cn/blog/180109/bbbKglA0LI.png?imageslim)

- 设计了user models.py

![mark](http://myphoto.mtianyan.cn/blog/180109/5ehi0hDB3C.png?imageslim)

- 循环引用

![mark](http://myphoto.mtianyan.cn/blog/180109/8f32C0imcE.png?imageslim)

>得出我们需要创建一个更高层次的app。分层设计，operation在更高层。

- Courses models.py 

![mark](http://myphoto.mtianyan.cn/blog/180109/e60fJjHeEa.png?imageslim)

- organization models.py

![mark](http://myphoto.mtianyan.cn/blog/180109/jg51D6Baj7.png?imageslim)

- operation models.py

![mark](http://myphoto.mtianyan.cn/blog/180109/3CLeJ5LCeD.png?imageslim)

通过makemigrations 生成表的变动 & migrate 
每个app下的migration目录的用途，和数据库中django_migration
将所有app放到同一个目录之下。

本章结束对应commit:

>数据表全部生成，migration目录&表django_migration。将app放到apps目录。对应4-9.
第四章结束！撒花。


{% cq %} 总之，我们要拿来。我们要或使用，或存放，或毁灭。 - 鲁迅 {% endcq %}

{% note  %} 既然有django提供的强大admin,我们便要拿来用喽。
- 使用xadmin，通过adminx,将已有model注册进后台。快速搭建可用的后台系统。
{% endnote %}

# xadmin快速搭建可用的后台系统

## django admin介绍

上一章我们进行了需求分析和数据库设计。本章我们来快速搭建一个可用的后台管理系统。

后台管理系统特点：

- 权限管理
- 少前端样式。(样式一般不是很看重)，
- 快速开发

django的后台管理系统是一套智能的管理系统。
django的杀手锏之一就是admin管理系统。

admin在项目新建时就已经为我们生成好了。

![mark](http://myphoto.mtianyan.cn/blog/180109/97kgi66hBJ.png?imageslim)

Django的admin也是一个app，在我们新建项目时就创建好了。
而且会自动在url中配置好了链接。

![mark](http://myphoto.mtianyan.cn/blog/180109/BdL32DBc99.png?imageslim)

访问:http://127.0.0.1:8000/admin/

可以看到admin的登录窗口。

Django是不会自动生成admin的用户的，需要我们自己去命令生成。

### createsuperuser 

点击`Tools 菜单下 Run manage.py Task `

```
createsuperuser 
```

![mark](http://myphoto.mtianyan.cn/blog/180109/ggemFK9lAJ.png?imageslim)

输入自己的用户名密码。

报错:

```
django.db.utils.DataError: (1406, "Data too long for column 'gender' at row 1")
```

>gender中female是6位。而我们最大长度只有5.

![mark](http://myphoto.mtianyan.cn/blog/180109/ie29f0bI0a.png?imageslim)

修改后

```
makemigrations users
migrate users
```

然后重新`createsuperuser`

使用自己定义的用户名密码可以登进系统。

![mark](http://myphoto.mtianyan.cn/blog/180109/C0h63A68F5.png?imageslim)

>默认是用户名 + 密码。后面会讲到如何实现用户名 或 邮箱和密码登录。

### 修改setting中对应语言，时区，以及数据库写入时间。

修改

```
# 语言改为中文
LANGUAGE_CODE = 'zh-hans'

# 时区改为上海
TIME_ZONE = 'Asia/Shanghai'
# 数据库存储使用时间，True时间会被存为UTC的时间
USE_TZ = False
```

点击运行可以看到如下图被换成汉语的效果:

![mark](http://myphoto.mtianyan.cn/blog/180109/L3fGhdb7C6.png?imageslim)

注意: django 2.0.1 并不会看到汉化后的默认页面。只有admin被汉化了。

组对应数据表: auth_group

在Django的admin中可以把上章的表都注册进来。对于表进行任意的增删改查。

默认其实会把user也注册进来的，但是因为我们通过userProfile覆盖了user。所以没有显示。

### 注册UserProfile进来

users/admin.py:

```python
# encoding: utf-8

# 因为同一个目录，所以可以直接.models
from .models import UserProfile


# 写一个管理器:命名, model+Admin
class UserProfileAdmin(admin.ModelAdmin):
    pass


# 将UserProfile注册进我们的admin中, 并为它选择管理器
admin.site.register(UserProfile,UserProfileAdmin)
```
![mark](http://myphoto.mtianyan.cn/blog/180109/c58F6dg549.png?imageslim)

>可以看到我们的用户信息就注册进来了。

`USERS` 是用户所在表名称。

![mark](http://myphoto.mtianyan.cn/blog/180109/Fk7G3EkDC4.png?imageslim)

进入页面可以看到Django为我们把每个不同类型的字段生成了不同的前端样式。

![mark](http://myphoto.mtianyan.cn/blog/180109/761bBAhbJl.png?imageslim)

>Django会自动帮我们把密码加密，而且不能反解。单向性。

如果出现错误, 可能是`initial`文件在我们拖入apps时路径被改变。之后我们添加了环境变量, 前面再加上apps就会报错。

这时把`initial.py` 中路径进行修改。

错误2：

```
新增用户信息提示：
Cannot add or update a child row: a foreign key constraint fails
(1452, 'Cannot add or update a child row: a foreign key constraint fails 
`mxonline`.`django_admin_log`, CONSTRAINT `django_admin_log_user_id_c564eba6_fk_auth_user_id` 
FOREIGN KEY (`user_id`) REFERENCES `auth_user` (`id`))')
```

>解决方案1: 不用解决，之后换Xadmin就好了。

解决方案2: 在setting的databases中添加以下代码取消外键检查

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'mxonline2',
        'USER': 'root',
        'PASSWORD': '你的密码',
        'HOST':'127.0.0.1',
        'OPTIONS': {
          "init_command": "SET foreign_key_checks=0;",
      }

    },

}

```
![mark](http://myphoto.mtianyan.cn/blog/180109/l4mGKFaGm4.png?imageslim)

实验成功为了不影响后面，把options删除

本小节结束对应commit:

>admin中添加管理器&注册。时区,语言,utc(False).数据库中选项参数。female的长度修改, createsuperuser.对应5-1

## xadmin的安装

一套基于admin, 比admin更强大的系统。

1. 通过pip安装

```
pip install xadmin
```

### Python3 & Django2.0.1安装官方适配Django2.0的包

```
pip install git+git://github.com/sshwsfc/xadmin.git@django2
```

xadmin可以把我们的后台做的很强大，可扩展。

![mark](http://myphoto.mtianyan.cn/blog/180109/2c3el2afjg.png?imageslim)

可以看到它同时下载了很多其他依赖包。

### 注册Xadmin 与 crispy-forms

Mxonline2/settings.py的INSTALLED_APPS中

```
    'xadmin',
    'crispy_forms'
```

然后把urls中默认admin指向Xadmin


```python
# 导入x admin，替换admin
import xadmin
urlpatterns = [
    url(r'^xadmin/', xadmin.site.urls),
]
```

Python3 Django2.0.1 的url的配置中

```
path('xadmin/', xadmin.site.urls),
```

**注意：Django 2.0.1中不需要加`r`也不需要加`^`**

将我们原来写的user/admin.py中代码注释掉。

此时直接运行项目会报错，因为我们Xadmin的默认数据表并没有migarte

```
ProgrammingError: (1146, "Table 'mxonline2.xadmin_usersettings' doesn't exist")
[09/Jan/2018 06:40:27] "GET /xadmin/ HTTP/1.1" 500 150414
```

点击`Tools 菜单下 Run manage.py Task `

```
makemigrations
migrate
```
![mark](http://myphoto.mtianyan.cn/blog/180109/bgleKlg6kJ.png?imageslim)

>可以看到已经被应用成功。

前往Navicat进行验证。

![mark](http://myphoto.mtianyan.cn/blog/180109/Al734ikfA4.png?imageslim)

>可以看到新增的表。

Xadmin的后台采用的是bootstrap。

![mark](http://myphoto.mtianyan.cn/blog/180109/7ccm6L5BG7.png?imageslim)

>后面我们会介绍如何制作插件

### 源码安装：

github: https://github.com/sshwsfc/xadmin

下载或`git clone`将源码下载到本地。

![mark](http://myphoto.mtianyan.cn/blog/180109/KFaKi4gC3C.png?imageslim)

>解压后将Xadmin文件夹复制到我们的项目中。

![mark](http://myphoto.mtianyan.cn/blog/180109/FbJeCbijh4.png?imageslim)

#### Python3版本源码安装:与url配置不同

```
git clone -b django2 https://github.com/sshwsfc/xadmin.git
```

其余操作一样。



### 新建extra_apps，并在setting中注册地址

新建new package:  extra_apps

>使用该目录存放我们的第三方插件，将Xadmin移入。
右键mark为SourceRoot, 但是这时候cmd下回报错。

所以在setting.py中加入。

```python
sys.path.insert(0,os.path.join(BASE_DIR, 'extra_apps'))
```

>因为我们的source目录已经有Xadmin了，就不会再去系统环境中找了。这时候卸载我们的Xadmin。

```
workon mxonline2
pip uninstall xadmin
```

但是他的依赖包我们还需要，所以只需要卸载Xadmin。此时我们运行会报错

```
    from future.utils import iteritems
ImportError: No module named future.utils
```

安装必要的包:

```
pip install future
pip install six
pip install httplib2
pip install django-import-export
```

此时又可以成功运行了

![mark](http://myphoto.mtianyan.cn/blog/180109/kmCI61m81H.png?imageslim)

日志记录：后台管理人员做的操作都会生成一条记录。

源码安装优点:

- xadmin新特性
- 对于源码进行自己的修改。



本小节结束对应commit:

>Xadmin的安装与源码安装，配置setting中extra_apps. 对应5-2

## users app 的model注册

### 遗留问题: django2.0.1使用xadmin时。如验证码等带dateTimefield区域出错。
xadmin/widgets.py

![mark](http://myphoto.mtianyan.cn/blog/180109/I3F7K6KhLf.png?imageslim)

```python
input_html = [ht for ht in super(AdminSplitDateTime, self).render(
    name, value, attrs).split('/><') if ht != '']
        if (len(input_html) > 1):
            input_html[0] = input_html[0] + "/>"
            input_html[1] = "<" + input_html[1]
```

![mark](http://myphoto.mtianyan.cn/blog/180109/KiBgGKCgLI.png?imageslim)

>此时可以看到已经运行正常

### 真正开始

Xadmin是基于Django的admin来开发的，所以Xadmin也继承了许多admin的用法。

- 比如: models的注册。

UserProfile已经被自动注册进去了，我们从验证码开始注册。

我们需要新建一个`adminx.py`文件，Xadmin会自动搜寻这种命名的文件。

### 新建py文件的初始化模板

![mark](http://myphoto.mtianyan.cn/blog/180109/22J8la5G8c.png?imageslim)

新建users/adminx.py：

```
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/9 0009 08:02'

import xadmin

from .models import EmailVerifyRecord


# 创建admin的管理类,这里不再是继承admin，而是继承object
class EmailVerifyRecordAdmin(object):
    pass


xadmin.site.register(EmailVerifyRecord, EmailVerifyRecordAdmin)
```
![mark](http://myphoto.mtianyan.cn/blog/180109/3LEG0j7e2h.png?imageslim)

>可以看到这时候访问已经有邮箱验证码了。

邮箱验证码这几个字就是我们代码中Meta中verbose_name定义的:

```python
    class Meta:
        verbose_name = "邮箱验证码"
        verbose_name_plural = verbose_name
```

`verbose_name_plural`是`verbose_name`的复数形式。

字段的verbose_name会直接显示在后台。`sendtype`和`sendtime`没有设置所以直接显示了英文。

![mark](http://myphoto.mtianyan.cn/blog/180109/BL45eAhd66.png?imageslim)

>可以看到我们添加验证码成功。注意:上节版本中我们进行了: makemigaration & migrate。
但是它是pip安装的Xadmin的数据表生成。我们卸载之后，源码安装需要重新运行进行数据迁移。(django需要通过app文件夹下的init文件来记录表的更改记录，pip的都卸了，所以就没法找到了)

会报错:

>Xadmin_log不存在错误。只需要运行这两条命令即可。

![mark](http://myphoto.mtianyan.cn/blog/180109/8A5cED00eC.png?imageslim)


#### 解决后台部分英文显示

>全部models中字段自行添加verbose_name

![mark](http://myphoto.mtianyan.cn/blog/180109/GG009ClkEE.png?imageslim)

这里就不贴出来了，自行检查都加上(没写出的请自行修改全部加上verbose_name)。

#### 解决EmailVerifyRecord object显示

>**全部**(没写出的请自行修改)model，py2:重载`__unicode` py3:重载`__str__`

```python
    # 重载Unicode方法使后台不再直接显示object
    def __unicode__(self):
        return '{0}({1})'.format(self.code,self.email)
```

>上面代码是python的自身基础语法。

![mark](http://myphoto.mtianyan.cn/blog/180109/F45LiKCF16.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180109/gb0kBFIJKH.png?imageslim)


#### 配置显示列

![mark](http://myphoto.mtianyan.cn/blog/180109/0mbjJe5ImK.png?imageslim)

users/adminx.py的管理器中设置list_display:

```
# 创建admin的管理类,这里不再是继承admin，而是继承object
class EmailVerifyRecordAdmin(object):
    # 配置后台我们需要显示的列
    list_display = ['code', 'email','send_type', 'send_time']
```

>list_display可以使用列表或元祖，建议使用列表。否则元组只有一个元素，忘记加逗号就会报错。

![mark](http://myphoto.mtianyan.cn/blog/180109/aj9gJbeJJJ.png?imageslim)

选择框的生成是因为我们加上了`choices`

#### 配置搜索searchfield

users/adminx.py的管理器中EmailVerifyRecordAdmin添加

```python
    # 配置搜索字段,不做时间搜索
    search_fields =  ['code', 'email','send_type']
```

![mark](http://myphoto.mtianyan.cn/blog/180109/fDclFJl6el.png?imageslim)

再添加一条数据验证搜索功能

![mark](http://myphoto.mtianyan.cn/blog/180109/8lLa4IIadB.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180109/FcAJjJcAAm.png?imageslim)


#### xadmin导出csv中文乱码解决

![mark](http://myphoto.mtianyan.cn/blog/180109/am4cLCB69D.png?imageslim)

>将`charset=utf-8` 改为`charset=gbk`

#### xadmin导出xml报错

```
TypeError at /xadmin/users/emailverifyrecord/
unicode argument expected, got 'str'
```
>io.StringIO这个库新版本的python3直接往这个库中加入了一些新的内容，使得该库在Python2.7中较为混乱。


![mark](http://myphoto.mtianyan.cn/blog/180109/HcG0a8g2Ef.png?imageslim)

>将StringIo变为BytesIO

#### 通过时间筛选字段。

users/adminx.py的管理器中EmailVerifyRecordAdmin添加

```
    # 配置筛选字段
    list_filter =  ['code', 'email','send_type', 'send_time']
```

![mark](http://myphoto.mtianyan.cn/blog/180109/FhLLheAi2f.png?imageslim)

### Django的admin, Xadmin和其他系统区别

>不像php等其他语言是一个功能模块一个功能设计的。
Django是对于每张表增删改查的管理器，我们可以在增删改成的基础上加上我们自己的后台逻辑。
因此某种程度可以说他是不依赖于具体业务的。不管啥系统后台都是由表组成。

不依赖于后台逻辑，又可以加上逻辑。

### user/models的注册

users/adminx.py中

```
# 创建banner的管理类
class BannerAdmin(object):
    list_display = ['title', 'image', 'url','index', 'add_time']
    search_fields = ['title', 'image', 'url','index']
    list_filter = ['title', 'image', 'url','index', 'add_time']
```

```
# 将model与admin管理器进行关联注册
xadmin.site.register(Banner, BannerAdmin)
```

此时后台页面。

![mark](http://myphoto.mtianyan.cn/blog/180109/0L58d277Ba.png?imageslim)

>可以自行测试轮播图是否可以新建成功。

本小节结束对应commit:

>usersmodels三张表注册进xadmin, 配置搜索过滤展示字段，修复xadmin导出xml错误,导出csv乱码，Unicode重载。对应5-3

py3(django2.0.1):

>usersmodels三张表注册进xadmin, 配置搜索过滤展示字段，修复xadmin导出csv乱码，修复django2.0.1的indexError, str重载。对应5-3

## 剩余app model注册

### courses注册

新建courses/adminx.py:

```python
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/9 0009 20:10'

from .models import Course, Lesson, Video, CourseResource
import xadmin

# Course的admin管理器


class CourseAdmin(object):
    list_display = [
        'name',
        'desc',
        'detail',
        'degree',
        'learn_times',
        'students']
    search_fields = ['name', 'desc', 'detail', 'degree', 'students']
    list_filter = [
        'name',
        'desc',
        'detail',
        'degree',
        'learn_times',
        'students']


class LessonAdmin(object):
    list_display = ['course', 'name', 'add_time']
    search_fields = ['course', 'name']

    # __name代表使用外键中name字段
    list_filter = ['course__name', 'name', 'add_time']


class VideoAdmin(object):
    list_display = ['lesson', 'name', 'add_time']
    search_fields = ['lesson', 'name']
    list_filter = ['lesson', 'name', 'add_time']


class CourseResourceAdmin(object):
    list_display = ['course', 'name', 'download', 'add_time']
    search_fields = ['course', 'name', 'download']
    # __name代表使用外键中name字段
    list_filter = ['course__name', 'name', 'download', 'add_time']


# 将管理器与model进行注册关联
xadmin.site.register(Course, CourseAdmin)
xadmin.site.register(Lesson, LessonAdmin)
xadmin.site.register(Video, VideoAdmin)
xadmin.site.register(CourseResource, CourseResourceAdmin)

```

![mark](http://myphoto.mtianyan.cn/blog/180109/H8eLIc73d9.png?imageslim)

>注意：对应后台显示英文的字段自行检查`verbosename`，自行加上。
>注意: py2下重载`__unicode__`方法，py3下重载`__str__`方法

如(注意缩进):

```python
    def __str__(self):
        return '《{0}》课程的章节 >> {1}'.format(self.course,self.name)
```
![mark](http://myphoto.mtianyan.cn/blog/180109/ICGm5c3acB.png?imageslim)

`int`类型后台会生成如下图区间取值:

![mark](http://myphoto.mtianyan.cn/blog/180109/9mcfFD7kml.png?imageslim)

可以看到有外键关系的会有一个小符号。

![mark](http://myphoto.mtianyan.cn/blog/180109/dH8Kblkmaj.png?imageslim)

### 注册机构app的adminx

新建`organization/adminx.py`:

```python
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/9 0009 21:01'

import xadmin

from .models import CityDict, CourseOrg, Teacher


# 机构所属城市名后台管理器
class CityDictAdmin(object):
    list_display = ['name', 'desc', 'add_time']
    search_fields = ['name', 'desc']
    list_filter = ['name', 'desc', 'add_time']


# 机构课程信息管理器
class CourseOrgAdmin(object):
    list_display = ['name', 'desc', 'click_nums', 'fav_nums','add_time' ]
    search_fields = ['name', 'desc', 'click_nums', 'fav_nums']
    list_filter = ['name', 'desc', 'click_nums', 'fav_nums','city__name','address','add_time']


class TeacherAdmin(object):
    list_display = [ 'name','org', 'work_years', 'work_company','add_time']
    search_fields = ['org', 'name', 'work_years', 'work_company']
    list_filter = ['org__name', 'name', 'work_years', 'work_company','click_nums', 'fav_nums', 'add_time']


xadmin.site.register(CityDict, CityDictAdmin)
xadmin.site.register(CourseOrg, CourseOrgAdmin)
xadmin.site.register(Teacher, TeacherAdmin)
```

>注意：对应后台显示英文的字段自行检查verbosename，自行加上。
>注意: py2下重载`__unicode__`方法，py3下重载`__str__`方法

如(注意缩进):

```python
      def __str__(self):
        return "[{0}]的教师: {1}".format(self.org, self.name)
```

如果注册后没有显示： 重新登录，或重启项目

![mark](http://myphoto.mtianyan.cn/blog/180109/cIe1LjK7gC.png?imageslim)

### operation app注册xadmin
新建`operation/adminx.py`

```python
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/9 0009 22:12'

import xadmin

from .models import UserAsk, UserCourse, UserMessage, CourseComments, UserFavorite


# 用户表单我要学习后台管理器
class UserAskAdmin(object):
    list_display = ['name', 'mobile', 'course_name', 'add_time']
    search_fields = ['name', 'mobile', 'course_name']
    list_filter = ['name', 'mobile', 'course_name', 'add_time']


# 用户课程学习后台管理器
class UserCourseAdmin(object):
    list_display = ['user', 'course', 'add_time']
    search_fields = ['user', 'course']
    list_filter = ['user', 'course', 'add_time']


# 用户消息后台管理器
class UserMessageAdmin(object):
    list_display = ['user', 'message', 'has_read', 'add_time']
    search_fields = ['user', 'message', 'has_read']
    list_filter = ['user', 'message', 'has_read', 'add_time']


# 用户评论后台管理器
class CourseCommentsAdmin(object):
    list_display = ['user', 'course', 'comments', 'add_time']
    search_fields = ['user', 'course', 'comments']
    list_filter = ['user', 'course', 'comments', 'add_time']


# 用户收藏后台管理器
class UserFavoriteAdmin(object):
    list_display = ['user', 'fav_id', 'fav_type', 'add_time']
    search_fields = ['user', 'fav_id', 'fav_type']
    list_filter = ['user', 'fav_id', 'fav_type', 'add_time']


# 将后台管理器与models进行关联注册。
xadmin.site.register(UserAsk, UserAskAdmin)
xadmin.site.register(UserCourse, UserCourseAdmin)
xadmin.site.register(UserMessage, UserMessageAdmin)
xadmin.site.register(CourseComments, CourseCommentsAdmin)
xadmin.site.register(UserFavorite, UserFavoriteAdmin)
```
>注意：对应后台显示英文的字段自行检查`verbosename`，自行加上。
>注意: py2下重载`__unicode__`方法，py3下重载`__str__`方法

如(注意缩进):

```python
      def __str__(self):
        return "[{0}]的教师: {1}".format(self.org, self.name)
```

成功性验证:

![mark](http://myphoto.mtianyan.cn/blog/180109/E6il5E9j86.png?imageslim)

本小节结束对于commit:

>5:4 注册完成operation,机构，课程app。注意:自行重载str/unicode。补全verbosename。

## xadmin全局配置

将全局配置修改:

- 如左上角：django Xadmin。下面的我的公司
- 主题修改，app名称汉化，菜单收叠。

### 使用Xadmin的主题功能。

把全站的配置放在users\adminx.py中:

```python
from xadmin import views
# 创建X admin的全局管理器并与view绑定。
class BaseSetting(object):
    # 开启主题功能
    enable_themes = True
    use_bootswatch = True

# 将全局配置管理与view绑定注册
xadmin.site.register(views.BaseAdminView, BaseSetting)
```

### 解决django1.9(python2)下Xadmin主题不生效问题。

https://my.oschina.net/u/2396236/blog/1083251

- 安装requests

```
pip install requests
```
- /xadmin/plugins/themes.py 引入requests

```
import requests
```

- 修改block_top_navmenu方法：

```
 def block_top_navmenu(self, context, nodes):

        themes = [
            {'name': _(u"Default"), 'description': _(u"Default bootstrap theme"), 'css': self.default_theme},
            {'name': _(u"Bootstrap2"), 'description': _(u"Bootstrap 2.x theme"), 'css': self.bootstrap2_theme},
            ]
        select_css = context.get('site_theme', self.default_theme)

        if self.user_themes:
            themes.extend(self.user_themes)

        if self.use_bootswatch:
            ex_themes = cache.get(THEME_CACHE_KEY)
            if ex_themes:
                themes.extend(json.loads(ex_themes))
            else:
                ex_themes = []
                try:
                    flag = False#假如为True使用原来的代码，假如为Flase，使用requests库来访问
                    if flag:
                        h = httplib2.Http()
                        resp, content = h.request("http://bootswatch.com/api/3.json", 'GET', '',
                            headers={"Accept": "application/json", "User-Agent": self.request.META['HTTP_USER_AGENT']})
                        if six.PY3:
                            content = content.decode()
                        watch_themes = json.loads(content)['themes']
                    else:
                        content = requests.get("https://bootswatch.com/api/3.json")
                        if six.PY3:
                            content = content.text.decode()
                        watch_themes = json.loads(content.text)['themes']

                    ex_themes.extend([
                        {'name': t['name'], 'description': t['description'],
                            'css': t['cssMin'], 'thumbnail': t['thumbnail']}
                        for t in watch_themes])
                except Exception as e:
                    print(e)

                cache.set(THEME_CACHE_KEY, json.dumps(ex_themes), 24 * 3600)
                themes.extend(ex_themes)

        nodes.append(loader.render_to_string('xadmin/blocks/comm.top.theme.html', {'themes': themes, 'select_css': select_css}))
```

### 修改django admin 和下面的我的公司收起菜单

```
# x admin 全局配置参数信息设置
class GlobalSettings(object):
    site_title = "天涯明月笙: 慕课后台管理站"
    site_footer = "mtianyan's mooc"
    # 收起菜单
    menu_style = "accordion"
# 将头部与脚部信息进行注册:
xadmin.site.register(views.CommAdminView, GlobalSettings)
```

### apps.py配置app的显示名称

每个app下执行同样操作:

```python
# encoding: utf-8
from django.apps import AppConfig


class CoursesConfig(AppConfig):
    name = 'courses'
    verbose_name = u"课程"
```

**注意自行找猫画虎为每个app添加中文名**

>新建app时并没有引用apps的配置

在app下的init.py中添加:

```python
default_app_config = "operation.apps.OperationConfig"
```
![mark](http://myphoto.mtianyan.cn/blog/180109/14kIeC7dbA.png?imageslim)

注意对应关系。

**注意为每个都添加对应的default_app_config**

最终大功告成：

![mark](http://myphoto.mtianyan.cn/blog/180110/KGcFbA85d9.png?imageslim)

### 自定义导航菜单顺序

```
class GlobalSetting(object):
     def get_site_menu(self):
        return (
            {'title': '课程管理', 'menus': (
                {'title': '课程信息', 'url': self.get_model_url(Course, 'changelist')},
                {'title': '章节信息', 'url': self.get_model_url(Lesson, 'changelist')},
                {'title': '视频信息', 'url': self.get_model_url(Video, 'changelist')},
                {'title': '课程资源', 'url': self.get_model_url(CourseResource, 'changelist')},
                {'title': '课程评论', 'url': self.get_model_url(CourseComments, 'changelist')},
            )},
            {'title': '机构管理', 'menus': (
                {'title': '所在城市', 'url': self.get_model_url(CityDict, 'changelist')},
                {'title': '机构讲师', 'url': self.get_model_url(Teacher, 'changelist')},
                {'title': '机构信息', 'url': self.get_model_url(CourseOrg, 'changelist')},
            )},
            {'title': '用户管理', 'menus': (
                {'title': '用户信息', 'url': self.get_model_url(UserProfile, 'changelist')},
                {'title': '用户验证', 'url': self.get_model_url(EmailVerifyRecord, 'changelist')},
                {'title': '用户课程', 'url': self.get_model_url(UserCourse, 'changelist')},
                {'title': '用户收藏', 'url': self.get_model_url(UserFavorite, 'changelist')},
                {'title': '用户消息', 'url': self.get_model_url(UserMessage, 'changelist')},
            )},


            {'title': '系统管理', 'menus': (
                {'title': '用户咨询', 'url': self.get_model_url(UserAsk, 'changelist')},
                {'title': '首页轮播', 'url': self.get_model_url(Banner, 'changelist')},
                {'title': '用户分组', 'url': self.get_model_url(Group, 'changelist')},
                {'title': '用户权限', 'url': self.get_model_url(Permission, 'changelist')},
                {'title': '日志记录', 'url': self.get_model_url(Log, 'changelist')},
            )},

xadmin.site.register(views.CommAdminView, GlobalSetting)
```

最终成型菜单:

![mark](http://myphoto.mtianyan.cn/blog/180110/314L2DdfGB.png?imageslim)

### 日志记录的使用

>日志记录会记录下我们进行过什么操作。

![mark](http://myphoto.mtianyan.cn/blog/180110/34EdEDHgac.png?imageslim)

通过点击动作，进入当时修改的某条信息

第五章完结对应commit:

>5-5 (第五章完结),配置了页头页脚信息，修改了菜单的顺序，配置apps中文名，修复Python2下，xadmin主题不生效问题。 完结撒花。


{% cq %} 矛盾的普遍性是指矛盾存在于一切事物的发展过程之中，矛盾存在于一切事物发展过程的始终。 {% endcq %}

{% note  %} 我想只要是个系统，就少不了登录注册。这是我们需要首先处理的主要矛盾。
- 完成登录 注册 找回密码 激活 验证码集成
{% endnote %}

# 完成登录 注册 找回密码 激活 验证码集成

## 6-1 首页和登录页面的配置

用户访问我们的根目录，我们需要把html文件返回给用户。因此我们第一步把html文件放入template目录。

![mark](http://myphoto.mtianyan.cn/blog/180110/fBkbi7968D.png?imageslim)

在html中找到首页的html。拷贝到我们的template目录

![mark](http://myphoto.mtianyan.cn/blog/180110/1EJD2hFc7E.png?imageslim)

### 新建static目录

>用来存放css, js等静态文件

![mark](http://myphoto.mtianyan.cn/blog/180110/ECL5dmKFkc.png?imageslim)

#### 配置处理静态文件的url。

Django2.0.1版本下:

Mxonline3/urls.py：

```
from django.views.generic import TemplateView

urlpatterns = [
    path('xadmin/', xadmin.site.urls),
    # TemplateView.as_view会将template转换为view
    path('', TemplateView.as_view(template_name= "index.html"), name=  "index")
]
```
Django1.9.8版本下:

Mxonline2/urls.py：

```
from django.views.generic import TemplateView

urlpatterns = [
    url(r'^xadmin/', xadmin.site.urls),
    url('^$', TemplateView.as_view(template_name="index.html"), name="index")

]

```

此时运行访问就可以访问到我们的index页面，不过会没有样式。

### 设置static文件

```python
# 说明静态文件放在哪个目录

STATIC_URL = '/static/'

STATICFILES_DIRS = (
    os.path.join(BASE_DIR, "static")
)
```

### 修改index页面中前端样式的引用地址

![mark](http://myphoto.mtianyan.cn/blog/180110/LflfkaA3Kj.png?imageslim)

使用ctrl+f查找出所有`../`,全部替换为`/static/`

然后点击运行，刷新页面可以看到我们的页面已经显示正常了。

### 拷贝登录页面到template

![mark](http://myphoto.mtianyan.cn/blog/180110/cJ8c3l41H4.png?imageslim)

使用ctrl+f查找出所有`../`,全部替换为`/static/`

>将css，js，图片全部替换完。

#### url配置跳转登录页面

Mxonline2/urls.py：

```python
    # 登录页面跳转url
    url('^login/$', TemplateView.as_view(template_name="login.html"), name="login")
```
Mxonline3/urls.py:

```python
    # TemplateView.as_view会将template转换为view
    path('', TemplateView.as_view(template_name= "index.html"), name=  "index"),
    path('login/', TemplateView.as_view(template_name= "login.html"), name=  "login")
```
在index页面，ctrl+f找到登录。将a标签中地址替换为login的url。

![mark](http://myphoto.mtianyan.cn/blog/180110/CBIAK2cjH0.png?imageslim)

取消注释后，将login.html改为`/login/`

![mark](http://myphoto.mtianyan.cn/blog/180110/ejcbBB0diJ.png?imageslim)

点击左侧减号收起。然后使用`<!--`与`-->`将个人中心暂时注释。

![mark](http://myphoto.mtianyan.cn/blog/180110/889BdI0a2g.png?imageslim)

可以看到登录注册，点击登录。

>根路径下的所有url都不需要斜杠

>此时我们的首页已经可以成功显示，通过首页点击登录也可以成功跳转登录页面

本小节完成对应commit:

>6-1: 完成首页与登录页面配置，设置了STATICFILES_DIRS。注意：dirs是一个元组，不要少逗号。删除了前面上传头像等直接传到根目录的目录。

## 6-2 用户登录-1

>配置url之前我们要书写好对应处理的view

Django的view实际就是一个函数，接收request请求对象，处理后返回response对象。

users/views.py:

```python
# encoding: utf-8
# 当我们配置url被这个view处理时，自动传入request对象.
def login(request):
    # 前端向后端发送的请求方式: get 或post

    # 登录提交表单为post
    if request.method == "POST":
        pass
    # 获取登录页面为get
    elif request.method == "GET":
        # render就是渲染html返回用户
        # render三变量: request 模板名称 一个字典写明传给前端的值
        return render(request, "login.html", {})
```
django1.9.8/urls.py
```python
from users.views import user_login
    # 登录页面跳转url login不要直接调用。而只是指向这个函数对象。
    url('^login/$',login, name="login")
```
django2.0.1/urls.py:

```python
from users.views import login
    path('login/', login, name="login")
```


在两行返回语句的位置打上断点:

![mark](http://myphoto.mtianyan.cn/blog/180110/lm6DF2CE02.png?imageslim)

点击debug，进入首页后点击登录。可以看到

![mark](http://myphoto.mtianyan.cn/blog/180110/5LiGiKh2ID.png?imageslim)

说明确实是通过get请求请求页面的。

通过值浏览器窗口可以看到这是一个`<WSGIRequest: GET '/login/'>`对象

![mark](http://myphoto.mtianyan.cn/blog/180110/I2C4i7FFj4.png?imageslim)

`path:`是指向的地址。

`f8`继续运行。跳转到登录页面。

## 6-3 用户登录2

### html form基础知识
templates/login.html:

>可以看到form表单中有input。点击提交会把值提交到后台。我们需要修改action让它指向我们的后台相应地址。

![mark](http://myphoto.mtianyan.cn/blog/180110/IkkaFHhGAl.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180110/ddDBg58ek1.png?imageslim)

>input中的name值会被传递到后台。回组成键值对形式。

submit类型的input

![mark](http://myphoto.mtianyan.cn/blog/180110/KAFII10hf9.png?imageslim)

只保留post这里的断点。输入用户名密码。查看debug情况

![mark](http://myphoto.mtianyan.cn/blog/180110/mEjmk6c1j9.png?imageslim)

`403禁止访问`错误: html页面内必须加上`crsf token` 才能传值到后台。

>我会随机的给前端发一串符号，你必须把这串符号带回来，我才允许你post。

![mark](http://myphoto.mtianyan.cn/blog/180110/CgEm92B9Ig.png?imageslim)

from表单之前写上`crsf token`

此时我们查看前端页面：

![mark](http://myphoto.mtianyan.cn/blog/180110/4aBegCbaAk.png?imageslim)

可以看到html中登录下面有一个隐藏着的值：crsf token, 不会显示。

此时点击登录跳转到pass位置。

![mark](http://myphoto.mtianyan.cn/blog/180110/cc82F1f1kE.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180110/F7JgIA41me.png?imageslim)

可以看到request中的POST中是一个queryset的对象。我们可以把它当成一个字典来用。
来取到前端的数据

```python
    if request.method == "POST":
        # 取不到时为空，username，password为前端页面name值
        user_name = request.POST.get("username", "")
        pass_word = request.POST.get("password", "")
```

取到用户名和密码我们就要开始进行验证登录。使用Django自带的`auth`方法。

```python
from django.contrib.auth import authenticate, login

    # 登录提交表单为post
    if request.method == "POST":
        # 取不到时为空，username，password为前端页面name值
        user_name = request.POST.get("username", "")
        pass_word = request.POST.get("password", "")

        # 成功返回user对象,失败返回null
        user = authenticate(username= user_name, password= pass_word)

        # 如果不是null说明验证成功
        if user is not None:
            # login_in 两参数：request, user
            # 实际是对request写了一部分东西进去，然后在render的时候：
            # request是要render回去的。这些信息也就随着返回浏览器。完成登录
            login(request, user)
            # 跳转到首页 user request会被带回到首页
            return render(request, "index.html")
        # 没有成功说明里面的值是None，并再次跳转回主页面
        else:
            return render(request, "login.html", {})
```

>authenticate调用只需要传入用户名和密码。成功会返回user对象，失败返回null


html中通过

![mark](http://myphoto.mtianyan.cn/blog/180110/Gcia8G8fgG.png?imageslim)

>设置成如果登录显示个人中心那段，未登录显示登录注册

打上断点

![mark](http://myphoto.mtianyan.cn/blog/180110/AeBb1BJE9m.png?imageslim)

点击debug后可以看到

![mark](http://myphoto.mtianyan.cn/blog/180110/J4caJi44DG.png?imageslim)

>我们成功的取到了值。

Django默认我们使用用户名和密码来登录

成功的登录user值如下

![mark](http://myphoto.mtianyan.cn/blog/180110/741Ia99FLf.png?imageslim)

但是继续执行报错:

```
login() takes exactly 1 argument (2 given)
```

这时因为我们处理登录的自定义函数也叫login。就直接调用了自身，而不是调用Django提供的login。**所以我们一定不要把自定义view函数命名与Django提供的冲突**

>解决方案：将我们的login改为`def user_login(request):`

并且前往urls.py中将login也一并改了

此时运行可以看到我们的个人中心已经出来了。

### 改造为使用邮箱用户名均可。Setting中重载变量

>自定义authenticate方法

```python
from django.contrib.auth.backends import ModelBackend
from .models import UserProfile
# 并集运算
from django.db.models import Q

# 实现用户名邮箱均可登录
# 继承ModelBackend类，因为它有方法authenticate，可点进源码查看
class CustomBackend(ModelBackend):
    def authenticate(self, username=None, password=None, **kwargs):
        try:
            # 不希望用户存在两个，get只能有一个。两个是get失败的一种原因 Q为使用并集查询

            user = UserProfile.objects.get(Q(username=username)|Q(email=username))

            # django的后台中密码加密：所以不能password==password
            # UserProfile继承的AbstractUser中有def check_password(self, raw_password):

            if user.check_password(password):
                return user
        except Exception as e:
            return None
```
Mxonline2/settings.py

```python
# 设置邮箱和用户名均可登录
AUTHENTICATION_BACKENDS = (
    'users.views.CustomBackend',

)
```

![mark](http://myphoto.mtianyan.cn/blog/180110/g1Hb79JKGK.png?imageslim)

>使用xadmin的退出，注销当前用户的退出。

此时我们可以通过邮箱和用户名都可以完成登录。

### 用户提示：return页面时提供它的错误信息

![mark](http://myphoto.mtianyan.cn/blog/180110/l55JiK9Cmh.png?imageslim)

```python
return render(request, "login.html", {"msg":"用户名或密码错误! "})
```

Html中如何取到这个值;

login html中这段是用来做错误提示的。

![mark](http://myphoto.mtianyan.cn/blog/180110/3i7BF5edj8.png?imageslim)

```
<div class="error btns login-form-tips" id="jsLoginTips">{{ msg }}</div>
```

验证：

![mark](http://myphoto.mtianyan.cn/blog/180110/7I9gdJ5DLj.png?imageslim)

本小节结束对应commit:

>6-2&3 完成了用户登录，登录验证自定义：邮箱用户名均可。错误信息返回前端。设置登录显示个人中心判断，注意不要把自定义方法写成login。


## 6-4 用form实现登录-1

上面我们的用户登录的方法是基于函数来做的。本节我们做一个基于类方法的版本。
要求对类的继承有了解。

基础教程中基本上都是基于函数来做的，其实更推荐基于类来做。基于类可以带来不少好处


```python
# 基于类实现需要继承的view
from django.views.generic.base import View
class LoginView(View):
    # 直接调用get方法免去判断
    def get(self, request):
        # render就是渲染html返回用户
        # render三变量: request 模板名称 一个字典写明传给前端的值
        return render(request, "login.html", {})
    def post(self, request):
        # 取不到时为空，username，password为前端页面name值
        user_name = request.POST.get("username", "")
        pass_word = request.POST.get("password", "")

        # 成功返回user对象,失败返回null
        user = authenticate(username=user_name, password=pass_word)

        # 如果不是null说明验证成功
        if user is not None:
            # login_in 两参数：request, user
            # 实际是对request写了一部分东西进去，然后在render的时候：
            # request是要render回去的。这些信息也就随着返回浏览器。完成登录
            login(request, user)
            # 跳转到首页 user request会被带回到首页
            return render(request, "index.html")
        # 没有成功说明里面的值是None，并再次跳转回主页面
        else:
            return render(request, "login.html", {"msg": "用户名或密码错误! "})
```

![mark](http://myphoto.mtianyan.cn/blog/180110/9mKFBk0Fc8.png?imageslim)

>继承的view中的方法。

django1.9.8 urls中的配置:

```python
# 换用类实现
from users.views import LoginView
    # 基于类方法实现登录,这里是调用它的方法
    url('^login/$', LoginView.as_view(), name="login")
```

Django2.0.1 urls配置:

```python
    # 基于类方法实现登录,这里是调用它的方法
    path('login/', LoginView.as_view(), name="login")
```

## 6-5 form字段验证

验证最大长度，是否为空等一系列。

users下新建forms文件。

```python
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/10 0010 04:44'
# 引入Django表单
from  django import forms

# 登录表单验证
class LoginForm(forms.Form):
    # 用户名密码不能为空
    username = forms.CharField(required=True)
    password = forms.CharField(required=True, min_length=5)

```

定义好forms之后我们来使用它做验证。

```python
def post(self, request):
        # 类实例化需要一个字典参数dict:request.POST就是一个QueryDict所以直接传入
        # POST中的usernamepassword，会对应到form中
        login_form = LoginForm(request.POST)
		#is_valid判断我们字段是否有错执行我们原有逻辑，验证失败跳回login页面
        if login_form.is_valid():
            # 取不到时为空，username，password为前端页面name值
            user_name = request.POST.get("username", "")
            pass_word = request.POST.get("password", "")

            # 成功返回user对象,失败返回null
            user = authenticate(username=user_name, password=pass_word)

            # 如果不是null说明验证成功
            if user is not None:
                # login_in 两参数：request, user
                # 实际是对request写了一部分东西进去，然后在render的时候：
                # request是要render回去的。这些信息也就随着返回浏览器。完成登录
                login(request, user)
                # 跳转到首页 user request会被带回到首页
                return render(request, "index.html")
        # 验证不成功跳回登录页面
        # 没有成功说明里面的值是None，并再次跳转回主页面
        else:
            return render(request, "login.html", {"msg": "用户名或密码错误! "})
```

### 完善错误提示

比如：既然表单都验证失败了，就不用显示密码出错了

![mark](http://myphoto.mtianyan.cn/blog/180110/Ca0lhc68He.png?imageslim)

```python
# 仅当用户真的密码出错时
            else:
                return render(request, "login.html",{"msg":"用户名或密码错误!"})
        # 验证不成功跳回登录页面
        # 没有成功说明里面的值是None，并再次跳转回主页面
        else:
            return render(
                request, "login.html", {
                    "login_form": login_form })
```

forms中的名称username和password必须和html中的一致。毕竟他是使用的request.POST
而request是从前面传过来的。

实例化`LoginView`时已经对于我们的字段进行了验证。

打上断点:

![mark](http://myphoto.mtianyan.cn/blog/180110/aelBLBFBG3.png?imageslim)

`debug`后`f6`运行到

![mark](http://myphoto.mtianyan.cn/blog/180110/F86386mI15.png?imageslim)

此时可以看到`errors(ErrorDict)`中的错误

![mark](http://myphoto.mtianyan.cn/blog/180110/EefmGb08e9.png?imageslim)

将form传回前端:

![mark](http://myphoto.mtianyan.cn/blog/180110/CKdB5L49dc.png?imageslim)

前端中取值：

![mark](http://myphoto.mtianyan.cn/blog/180110/C6AajKcm51.png?imageslim)

给这个class加上errorput会显示红色外框。

![mark](http://myphoto.mtianyan.cn/blog/180110/G89gGl2G75.png?imageslim)

>注意:写在class里面

### 将forms错误信息显示出来

```python
<div class="error btns login-form-tips" id="jsLoginTips">
{% for key, error in login_form.errors.items %}
{{ error }}
{% endfor %}
{{ msg }}</div>
```


![mark](http://myphoto.mtianyan.cn/blog/180110/a3CjlEhC9B.png?imageslim)



- 写了一个类继承Django的view，然后写了get post方法(get/post的if是Django替我们完成的)
- 在url中调用Loginview的as_view方法需要加上括号，进行调用。
- Django的form进行表单验证并把error值传到前台。
- is_valid方法，验证表单

本小节完毕对应commit:

>6-4 & 5 登录换用类继承view实现,使用Django form进行表单验证并把错误信息提示到前台。

## 6-6 session和cookie自动登录机制

>我们本节来讲session和cookie

User1如何实现登录的。

### cookie的存储

cookie是浏览器支持的一种本地存储方式。以dict，键值对方式存储。

```
{"sessionkey": "123"}
```

浏览器会自动对于它进行解析。

### http请求是一种无状态的请求

用户向服务器发起的两次请求之间是没有状态的。也就是服务器并不知道这是同一个用户发的。

做到记住用户:

>浏览器a在向服务器发起请求，服务器会自动给浏览器a回复一个id，浏览器a把id放到cookie当中，在下一次请求时带上这个cookie里的id值向浏览器请求，服务器就知道你是哪个浏览器发过来的了。

### 有状态请求(cookie)

![mark](http://myphoto.mtianyan.cn/blog/180110/4F22diHeF6.png?imageslim)

服务器`a`发回来的`id`会放到服务器`a`的域之下。**不能跨域访问cookie。**

使用浏览器随便打开一个网页，然后`f12`打开。

比如我使用的`Chrome`浏览器

![mark](http://myphoto.mtianyan.cn/blog/180110/Bb6elgf96A.png?imageslim)

会找到存储在浏览器本地的cookie值

![mark](http://myphoto.mtianyan.cn/blog/180110/b3CH160G9h.png?imageslim)

点击`clear all `清空所有的`cookie` `f5`刷新页面，会发现又把这些cookie值进来。

如果将用户名和密码直接保存在cookie，可以实现**最垃圾最简略版本的**自动登录。

### 解决cookie放在本地不安全的问题(session)

>用户在第一次请求后，浏览器回复的id既可以是用户的user id。
也可以一段任意的字符串，我们把它叫做session id

根据用户名和密码，服务器会采用自己的规则生成`session id`。这个`session id`保存在本地cookie。浏览器请求服务器会携带。

- 输入用户名 & 密码
- 调用 login(), 后端程序会根据用户名密码生成session id。保存在数据库中。
- 用户登录之后，需要通过这个`session id`取出这些基本信息。

![mark](http://myphoto.mtianyan.cn/blog/180110/F6d3AkdJB0.png?imageslim)

Django的默认表中的`session`表就记录了用户登录时，后端我们Django为用户生成的`sessionid`。

![mark](http://myphoto.mtianyan.cn/blog/180110/9L54Emf6md.png?imageslim)

可以看到`session key value` 和过期时间。

我们可以清空这张表的数据。运行项目进行登录。

![mark](http://myphoto.mtianyan.cn/blog/180110/kLdLLALGB1.png?imageslim)

>可以看到我们刚刚生成的session id。

此时通过`f12`查看浏览器在本地存储的`session id`。可以看到如下图和我们数据库中的一致。

![mark](http://myphoto.mtianyan.cn/blog/180110/2Hee7I5fIl.png?imageslim)

>**session_key 发到浏览器叫做session id**

通过session id 用户访问任何一个页面都会携带，服务器就会认识。

Setting.py中，

![mark](http://myphoto.mtianyan.cn/blog/180110/Gi40A0FFhB.png?imageslim)

这个app会拦截我们每次的request请求，在`request`中找到session id，然后去数据表中进行查询。
然后通过`session key` 去找到`session data`。此时直接为我们取出了user。

在服务器返回浏览器的`response`中也会直接加上`session id`

>cookie是浏览器本地存储机制，存在域名之下，存储不安全。
服务器在返回id时通过规则生成一串字符，并设置了过期时间。存储在服务器端(数据库)

文章: http://projectsedu.com/2016/10/17/django%E4%BB%8E%E8%AF%B7%E6%B1%82%E5%88%B0%E8%BF%94%E5%9B%9E%E9%83%BD%E7%BB%8F%E5%8E%86%E4%BA%86%E4%BB%80%E4%B9%88/


## 6-7 用户注册

### 拷贝注册页面进入template目录

### 书写我们对应要处理的view(RegisterView)

users/views.py

```python
# 注册功能的view
class RegisterView(View):
    # get方法直接返回页面
    def get(self, request):
        return render(request, "register.html", {})
```
### 配置对应的url

Django1.9.8 url配置如下:

```python
from users.views import RegisterView
    # 注册url
    url("^register/", RegisterView.as_view(), name="register"),
```

Django2.0.1 url配置如下

```python
from users.views import RegisterView
    # 注册url
    path("register/", RegisterView.as_view(), name = "register" )
```

### 修改index页面中注册url

![mark](http://myphoto.mtianyan.cn/blog/180110/BJl97lJ8bd.png?imageslim)

此时访问首页发现可以成功跳转到注册页面

### 修改静态文件中static目录引用

#### 关键步骤load staticfile

![mark](http://myphoto.mtianyan.cn/blog/180110/Hm54EJ7IH9.png?imageslim)

#### 然后修改路径为一个相对于static的相对路径

![mark](http://myphoto.mtianyan.cn/blog/180110/ackf2LaLJ8.png?imageslim)

>他会自动根据setting中配置，为我们加上前缀

![mark](http://myphoto.mtianyan.cn/blog/180110/3FDhdl2aiH.png?imageslim)

>如果我们把目录在setting中改到mystatic。url中会自动添加指定的前缀

可以看到可以访问成功。

![mark](http://myphoto.mtianyan.cn/blog/180110/0KkhH7b8Bm.png?imageslim)

#### 将目前的三个html中的静态文件全部修改目录

>枯燥但是要有耐心。

这时候访问三个页面，查看样式是否完好。

### 验证码库实现验证码

https://github.com/mbi/django-simple-captcha

#### 安装配置

```
workon mxonline3
pip install  django-simple-captcha
workon mxonline2
pip install  django-simple-captcha==0.4.6
```

- Add `captcha` to the `INSTALLED_APPS` in your `settings.py`

- Add an entry to your `urls.py`:

django1.9.8如下:

```python
from django.conf.urls import url, include
urlpatterns += [
    url(r'^captcha/', include('captcha.urls')),
]
```

django2.0.1如下；

```
    # 验证码url
    path("captcha/", include('captcha.urls'))
```

```python
makemigrations
migrate
```

![mark](http://myphoto.mtianyan.cn/blog/180110/0Igb4IgB0F.png?imageslim)

进入数据库查看生成的表

![mark](http://myphoto.mtianyan.cn/blog/180110/JiI713cAdd.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/ac8KFHkCBc.png?imageslim)

### 将验证码展示到页面

users/forms.py:

#### 定义我们的register form:

```python
# 引入验证码field
from captcha.fields import CaptchaField

# 验证码form & 注册表单form
class RegisterForm(forms.Form):
    # 此处email与前端name需保持一致。
    email = forms.EmailField(required=True)
    # 密码不能小于5位
    password = forms.CharField(required=True, min_length=5)
    # 应用验证码
    captcha = CaptchaField()

```

users/views.py

#### 在我们的registerform中实例化并传送到前端:

```
# form表单验证 & 验证码
from .forms import LoginForm, RegisterForm

# 注册功能的view
class RegisterView(View):
    # get方法直接返回页面
    def get(self, request):
        # 添加验证码
        register_form = RegisterForm()
        return render(request, "register.html", {'register_form':register_form})

```

#### 前端获取验证码值

![mark](http://myphoto.mtianyan.cn/blog/180110/d55glDI9E1.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180110/DL7ejk8EcF.png?imageslim)

找到上图验证码部分。修改为下图

![mark](http://myphoto.mtianyan.cn/blog/180110/01gC20eabk.png?imageslim)

Forms中的field会生成不同的框。

![mark](http://myphoto.mtianyan.cn/blog/180110/ChgL88Ed76.png?imageslim)

我们只有label但是前端可以查看到input框等，也就是Registerform会为我们生成输入框+验证码。

>隐藏的字符串的框会被带到后台，由Django为我们进行验证。验证该验证码是否保存过。

![mark](http://myphoto.mtianyan.cn/blog/180110/547cdji7Gl.png?imageslim)

>可以看得我们数据库中将这个hashkey进行了保存。这个key与验证码内容对应。

后台会把验证码值 和 hashkey进行联合查询。

### 编写register view的后台逻辑(RegisterView)

users/views.py的RegisterView中添加post方法：

```
    def post(self, request):
        # 实例化form
        register_form = RegisterForm(request.POST)
        if register_form.is_valid():
            pass
```

![mark](http://myphoto.mtianyan.cn/blog/180110/BKIjc06AF3.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180110/bA0KEd7bhc.png?imageslim)

修改form表单提交方式与提交到哪个url

![mark](http://myphoto.mtianyan.cn/blog/180110/ahg7KfbCAi.png?imageslim)

前端的form提交加上对应的crsf token

刷新验证码是前端帮我们完成的：

```
//刷新验证码
function refresh_captcha(event){
    $.get("/captcha/refresh/?"+Math.random(), function(result){
        $('#'+event.data.form_id+' .captcha').attr("src",result.image_url);
        $('#id_captcha_0').attr("value",result.key);
    });
    return false;
}
```

#### 获取前端页面值并封装成一个user_profile对象，保存到数据库。

```
from django.contrib.auth.hashers import make_password

        if register_form.is_valid():
            user_name = request.POST.get("email", "")
            pass_word = request.POST.get("password", "")

            # 实例化一个user_profile对象，将前台值存入
            user_profile = UserProfile()
            user_profile.username = user_name
            user_profile.email = user_name

            # 加密password进行保存
            user_profile.password = make_password(pass_word)
            user_profile.save()
            pass

```

#### 发送邮件实现

setting中配置；

```python
# 发送邮件的setting设置

EMAIL_HOST = "smtp.qq.com"
EMAIL_PORT = 25
EMAIL_HOST_USER = "mxonline.mtianyan.cn"
EMAIL_HOST_PASSWORD = " "
EMAIL_USE_TLS= True
EMAIL_FROM = "mxonline.mtianyan.cn"
```

新建package后新建文件。

`apps：utils/email_send.py`:

```python
# encoding: utf-8
from random import Random

__author__ = 'mtianyan'
__date__ = '2018/1/10 0010 20:47'
from  users.models import EmailVerifyRecord
# 导入Django自带的邮件模块
from django.core.mail import send_mail
# 导入setting中发送邮件的配置
from Mxonline2.settings import EMAIL_FROM

# 生成随机字符串
def random_str(random_length=8):
    str = ''
    # 生成字符串的可选字符串
    chars = 'AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz0123456789'
    length = len(chars) - 1
    random = Random()
    for i in range(random_length):
        str += chars[random.randint(0, length)]
    return str

# 发送注册邮件
def send_register_eamil(email, send_type="register"):
    # 发送之前先保存到数据库，到时候查询链接是否存在

    # 实例化一个EmailVerifyRecord对象
    email_record = EmailVerifyRecord()
    # 生成随机的code放入链接
    code = random_str(16)
    email_record.code = code
    email_record.email = email
    email_record.send_type = send_type

    email_record.save()

    # 定义邮件内容:
    email_title = ""
    email_body = ""

    if send_type == "register":
        email_title = "mtianyan慕课小站 注册激活链接"
        email_body = "请点击下面的链接激活你的账号: http://127.0.0.1:8000/active/{0}".format(code)

        # 使用Django内置函数完成邮件发送。四个参数：主题，邮件内容，从哪里发，接受者list
        send_status = send_mail(email_title, email_body, EMAIL_FROM, [email])
        # 如果发送成功
        if send_status:
            pass
```



![mark](http://myphoto.mtianyan.cn/blog/180110/8leIJ2l6LD.png?imageslim)

上图为qq邮箱开启smtp服务

点击生成授权码

![mark](http://myphoto.mtianyan.cn/blog/180110/6fDDI979Dk.png?imageslim)

def post中加上发送邮件

`users/views.py`：

```
# 发送邮件
from utils.email_send import send_register_eamil
            # 发送注册激活邮件
            send_register_eamil(user_name, "register")
```

点击注册提交，因为我们没有return。一直在转圈圈。

但是数据库中已经添加了字段。

![mark](http://myphoto.mtianyan.cn/blog/180110/FL04F47985.png?imageslim)

可以看到我们的邮件已经被发送到邮箱中。

如果注册成功返回login页面:不成功，返回register页面并报错。

#### 完善错误提示。

>找猫画虎：将login中的错误提示搬运到register中来。

- register_form的报错信息。

![mark](http://myphoto.mtianyan.cn/blog/180110/gmDlEB0L2G.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180110/e7a65cgj8D.png?imageslim)

- 邮箱 & 密码 form验证

![mark](http://myphoto.mtianyan.cn/blog/180110/ElHe2gdDAL.png?imageslim)

#### 完善用户值回填逻辑

![mark](http://myphoto.mtianyan.cn/blog/180110/DGHbaLBkd3.png?imageslim)

如果传回的有值则，显示传回来值。

密码也做同样操作

#### 修改默认的激活状态为false

post方法中

```
            # 默认激活状态为false
            user_profile.is_active = False
```

书写处理激活的view。


```
# 激活用户的view
class ActiveUserView(View):
    def get(self, request, active_code):
        # 查询邮箱验证记录是否存在
        all_record = EmailVerifyRecord.objects.filter(code = active_code)
        # 激活form负责给激活跳转进来的人加验证码
        active_form = ActiveForm(request.GET)
        # 如果不为空也就是有用户
        if all_record:
            for record in all_record:
                # 获取到对应的邮箱
                email = record.email
                # 查找到邮箱对应的user
                user = UserProfile.objects.get(email=email)
                user.is_active = True
                user.save()
                # 激活成功跳转到登录页面
                return render(request, "login.html", )
        # 自己瞎输的验证码
        else:
            return render(request, "register.html", {"msg": "您的激活链接无效","active_form": active_form})

```

配置用户激活的url并通过url提取到变量:

django1.9.8:

```
    # 激活用户url
    url(r'^active/(?P<active_code>.*)/$',ActiveUserView.as_view(), name= "user_active")
```

django2.0.1：

```
    # 激活用户url
    re_path('active/(?P<active_code>.*)/', ActiveUserView.as_view(), name= "user_active")
```

这里通过`?p`将后面`.*`代表全部提取的正则，符合的内容传入参数active_code中`/$`代表以`/$`为结尾

![mark](http://myphoto.mtianyan.cn/blog/180111/i7DdIaB5bd.png?imageslim)

>其他细节根据自己需要进行优化。

注册功能制作完毕。对应commit:

>注册功能实现完毕，流程:注册，发邮件，激活，登录。对应6-6,7,8,9,10

## 6-8 找回密码

>这个6-8对应对应6-11,6-12

### 拷入forgetpassword页面

### 书写处理忘记密码的view

users/views.py

```python
# 用户忘记密码的处理view
class ForgetPwdView(View):
    # get方法直接返回页面
    def get(self, request):
        return render(request, "forgetpwd.html", { })

```

django2.0.1 urls中配置:

```
    # 忘记密码
    path('forget/', ForgetPwdView.as_view(), name= "forget_pwd"),
```

Django1.9.8 urls中配置:

```
    # 忘记密码
    url('forget/$', ForgetPwdView.as_view(), name="forget_pwd"),
```

#### login html中忘记密码

![mark](http://myphoto.mtianyan.cn/blog/180111/cgk66mgd35.png?imageslim)

#### 配置忘记密码页面中静态文件。

```
load static
修改static的目录
修改其中的url
```

#### 定义一个给forget的form
users/forms.py:

```python
# 注册验证码实现
class ForgetForm(forms.Form):
    # 此处email与前端name需保持一致。
    email = forms.EmailField(required=True)
    # 应用验证码 自定义错误输出key必须与异常一样
    captcha = CaptchaField(error_messages={"invalid": u"验证码错误"})
```

#### 添加验证码

```
# 用户忘记密码的处理view
class ForgetPwdView(View):
    # get方法直接返回页面
    def get(self, request):
        forget_from = ForgetForm()
        return render(request, "forgetpwd.html", {"forget_from":forget_from })

```

#### html中加上验证码

![mark](http://myphoto.mtianyan.cn/blog/180111/Cf24GA16g0.png?imageslim)

#### post中逻辑

```python
    # post方法实现
    def post(self, request):
        forget_form = ForgetForm(request.POST)
        # form验证合法情况下取出email
        if forget_form.is_valid():
            email = request.POST.get("email","")
            # 发送找回密码邮件
            send_register_eamil(email, "forget")
            # 发送完毕返回登录页面并显示发送邮件成功。
            return render(request, "login.html", {"msg":"重置密码邮件已发送,请注意查收"})
        # 如果表单验证失败也就是他验证码输错等。
        else:
            return render(request, "forgetpwd.html", {"forget_from": forget_form })
```

#### 邮箱重置密码邮件发送

```
 elif send_type == "forget":
        email_title = "mtianyan慕课小站 找回密码链接"
        email_body = loader.render_to_string(
            "email_forget.html",  # 需要渲染的html模板
            {
                "active_code": code  # 参数
            }
        )
        msg = EmailMessage(email_title, email_body, EMAIL_FROM, [email])
        msg.content_subtype = "html"
        send_status = msg.send()

```

![mark](http://myphoto.mtianyan.cn/blog/180111/4e60888a7F.png?imageslim)

#### 前端页面添加错误信息

已经重复很多遍这个操作了。

![mark](http://myphoto.mtianyan.cn/blog/180111/fl8Dhg5B2H.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/KEmkdk9c3b.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/FI5fafG9a8.png?imageslim)

>上述三图进行改正，不一一列举

#### 书写重置密码view

```python
# 重置密码的view
class ResetView(View):
    def get(self, request, active_code):
        # 查询邮箱验证记录是否存在
        all_record = EmailVerifyRecord.objects.filter(code=active_code)
        # 如果不为空也就是有用户
        active_form = ActiveForm(request.GET)
        if all_record:
            for record in all_record:
                # 获取到对应的邮箱
                email = record.email
                # 将email传回来
                return render(request, "password_reset.html", {"email":email})
        # 自己瞎输的验证码
        else:
            return render(
                request, "forgetpwd.html", {
                    "msg": "您的重置密码链接无效,请重新请求", "active_form": active_form})
```

#### 配置重置密码url

```python
# Django1.9.8:
    # 重置密码urlc ：用来接收来自邮箱的重置链接
    url('reset/(?P<active_code>.*)/$', ResetView.as_view(), name="reset_pwd"),
# django2.0.1:

    # 重置密码urlc ：用来接收来自邮箱的重置链接
    re_path('reset/(?P<active_code>.*)/', ResetView.as_view(), name="reset_pwd"),
```

#### 拷贝进来password reset页面

![mark](http://myphoto.mtianyan.cn/blog/180111/LFKlj0CLAb.png?imageslim)

>添加一个隐藏的input框，以便于我们知道到底是哪个用户在重置密码

![mark](http://myphoto.mtianyan.cn/blog/180111/BfaLgiG5k3.png?imageslim)

配置html中三大变化加url配置。

![mark](http://myphoto.mtianyan.cn/blog/180111/AiiGBEkJLj.png?imageslim)


`reset`的`url`需要我们传参进来,但是`modify`的不需要。
所以url配置和view都得分开。

#### 创建改变密码的forms:

```python
# 重置密码form实现
class ModifyPwdForm(forms.Form):
    # 密码不能小于5位
    password1 = forms.CharField(required=True, min_length=5)
    # 密码不能小于5位
    password2 = forms.CharField(required=True, min_length=5)
```

#### 书写改变密码的view；

```python
 # 改变密码的view
class ModifyPwdView(View):
    def post(self, request):
        modiypwd_form = ModifyPwdForm(request.POST)
        if modiypwd_form.is_valid():
            pwd1 = request.POST.get("password1", "")
            pwd2 = request.POST.get("password2", "")
            email = request.POST.get("email", "")
            # 如果两次密码不相等，返回错误信息
            if pwd1 != pwd2:
                return render(request, "password_reset.html", {"email": email, "msg": "密码不一致"})
            # 如果密码一致
            user = UserProfile.objects.get(email=email)
            # 加密成密文
            user.password = make_password(pwd2)
            # save保存到数据库
            user.save()
            return render(request, "login.html", {"msg": "密码修改成功，请登录"})
        # 验证失败说明密码位数不够。
        else:
            email = request.POST.get("email", "")
            return render(request, "password_reset.html", {"email": email, "modiypwd_form":modiypwd_form})

```

#### 配置modify的url。

django2.0.1:

```python
    # 修改密码url; 用于passwordreset页面提交表单
    path('modify_pwd/', ModifyPwdView.as_view(), name="modify_pwd"),
```

django1.9.8:

```python
    # 修改密码url; 用于passwordreset页面提交表单
    url(r'^modify_pwd/$', ModifyPwdView.as_view(), name="modify_pwd"),
```

建议自行走一遍注册，登录，忘记密码。重置密码。
错误的激活链接，错误的重置链接。值回填，form报错

更多: 重置密码链接是否被点击过，过期时间。

>对应commit忘记密码重置功能实现完毕，并进行了必要的测试。对应6-11,6-12



{% cq %} 在绝望中寻找希望，人生终将辉煌 - 新东方 {% endcq %}

{% note default %} 
作为一个正经的教育网站，我们更是拥有正规的机构合作: 比如来自火星的星星优培。
- 完成授课机构的功能实现。
{% endnote %}

# 完成授课机构的功能实现。

## 7-1 django templates模板继承1

- 机构可以筛选类别
- 机构可以根据所在地区进行分类

右侧我要学习功能: form表单提交
右下：授课机构排名

页面头部与底部为全局头和全局底部。

### Django template 共用头部底部机制

将head和foot放在两个html中，然后在写其他需要这两个部分的页面时include进来。

Django也是支持include机制的。

### include的问题

include的进来的死页面，这时候该怎么办？

解决这种问题：进行模板的继承机制。定义一个父类的框架，子类可以替换其中一部分block，子类只需要重写自己需要改变的block。

### template中新建base.html

将课程机构列表页。orglist拷贝进template目录

将orglist内容替换base内容。

![mark](http://myphoto.mtianyan.cn/blog/180111/Idbj8d04h5.png?imageslim)

将div收起来

![mark](http://myphoto.mtianyan.cn/blog/180111/4gb7aiICk7.png?imageslim)


loadstaticfiles & 修改静态文件路径为static

>这个步骤做过太多遍了，自行完成。耐心就行了。

### 定义父模板: 包含head & footer


title应该是可以被子页面替换的所以要包起来。

![mark](http://myphoto.mtianyan.cn/blog/180111/3e96fGcGma.png?imageslim)

css有共用的部分，也有可以被子页面替换的部分。

![mark](http://myphoto.mtianyan.cn/blog/180111/14mBAlhH8D.png?imageslim)

js同理

![mark](http://myphoto.mtianyan.cn/blog/180111/bBjf5DBLh2.png?imageslim)

面包屑是需要被各个页面自己替换的。

![mark](http://myphoto.mtianyan.cn/blog/180111/IekmEbK9A8.png?imageslim)

将正文内容包起来；

![mark](http://myphoto.mtianyan.cn/blog/180111/hbhi9lBah2.png?imageslim)

此时base页面就制作好了

## 7-2 开始orglist编写

第一步:清空所有内容

- 继承base页面

![mark](http://myphoto.mtianyan.cn/blog/180111/9AL06C2hjh.png?imageslim)

- 覆盖父类的title

![mark](http://myphoto.mtianyan.cn/blog/180111/BL8G2CkmGl.png?imageslim)

- 书写课程机构view
organization/views.py

```
# encoding: utf-8
from django.views.generic.base import View
# 处理课程机构列表的view
class OrgView(View):
    def get(self,request):
        return render(request, "org-list.html", { })

```

- Django2.0.1配置课程机构首页url

```
    # 课程机构首页url
    path('org_list/', OrgView.as_view(), name="org_list"),
```
- Django1.9.8配置url：

```
    # 课程机构首页url
    url(r'^org_list/$', OrgView.as_view(), name="org_list"),
```

### 修改面包屑

- base中只保留首页
- org中重写block custom_bread
- block之间没有先后顺序。

- 将base中block content拿到orglist重写

![mark](http://myphoto.mtianyan.cn/blog/180111/emCCcfGcEd.png?imageslim)

- 然后将base中block中间section删除掉

![mark](http://myphoto.mtianyan.cn/blog/180111/7KKbaGb97i.png?imageslim)

>orglist开始loadstaticfiles

`ctrl+d`快速删除

![mark](http://myphoto.mtianyan.cn/blog/180111/D5hBDAjHeA.png?imageslim)

页面的继承关系使得变量也可以直接用

>比如user中的form数据传递到register文件当中.如果register继承的是base页面。
base页面当中也是可以用这些数据的。`参数的向上传递`

每个request对象都会传递到html中来，如果继承了base，request也会向上传递到base。
base中就可以加入我们的逻辑: 用户是否登录等。

小节结束对应commit:

>完成Django templates的继承关系了解，机构列表展示页。对应7-1 & 2

## 7-3 课程机构列表页数据展示1

确定由后台传过来的动态数据:

授课机构列表本身， 授课机构的排名，所在地区(后台取出所有地区), 机构类别写成静态，因为一般不怎么变动。

在xadmin中添加城市信息，课程信息。

添加城市

![mark](http://myphoto.mtianyan.cn/blog/180111/CJG79b8JJ5.png?imageslim)

添加机构。

插播知识点：

![mark](http://myphoto.mtianyan.cn/blog/180111/325Id7l954.png?imageslim)

这里指定的路径是一个相对路径

setting中要配置我们把文件存放在哪个根目录之下


```
# 设置我们上传文件的路径

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

在项目根目录创建media文件夹

在后台上传图片

![mark](http://myphoto.mtianyan.cn/blog/180111/EG198BJgi3.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/I4A16CDal5.png?imageslim)

修改机构信息中封面图为logo

自行添加十个课程机构

### models中添加机构类别


organization/models.py：

```python
class CourseOrg(models.Model):
    ORG_CHOICES =(
        ("pxjg", u"培训机构"),
        ("gx", u"高校"),
        ("gr", u"个人"),
    )

    name = models.CharField(max_length=50, verbose_name=u"机构名称")
    # 机构描述，后面会替换为富文本展示
    desc = models.TextField(verbose_name=u"机构描述")
    # 机构类别:
    category = models.CharField(max_length=20, choices=ORG_CHOICES, verbose_name=u"机构类别", default="pxjg")
```

修改了models之后做数据库的变动:

```python
makemigrations organization
migrate organization
```

![mark](http://myphoto.mtianyan.cn/blog/180111/lFLGKIH5fE.png?imageslim)

完成之后打开Navicat进行验证：

![mark](http://myphoto.mtianyan.cn/blog/180111/C6B1Hb7LKD.png?imageslim)

可以看到新增了。

### 完善我们的view

将列表里的静态数据变成后台获取的动态数据

organization/views.py

```python
from .models import CourseOrg, CityDict


class OrgView(View):
    def get(self,request):
        # 查找到所有的课程机构
        all_orgs = CourseOrg.objects.all()
        # 取出所有的城市
        all_citys = CityDict.objects.all()

        return render(request, "org-list.html", {
            "all_orgs":all_orgs,
            "all_citys": all_citys,
        })
```

## 7-4 课程机构列表页数据展示2

### 前去html中进行数据填充

![mark](http://myphoto.mtianyan.cn/blog/180111/amEhg6kFbf.png?imageslim)

>可以看到所有城市是通过a标签，当前选中城市为active。

![mark](http://myphoto.mtianyan.cn/blog/180111/LcIB9jeKem.png?imageslim)

之后把下面的写死的城市删除掉。

![mark](http://myphoto.mtianyan.cn/blog/180111/hg5g6Cc7f0.png?imageslim)

这时就是我们在后台添加的数据了

![mark](http://myphoto.mtianyan.cn/blog/180111/8D6a8Dl3h3.png?imageslim)

可以看到每个课程机构都是一个dl

同理使用for循环。

### 如何将imageField转换为图片地址

数据库中img存放的是字符串：相对路径

![mark](http://myphoto.mtianyan.cn/blog/180111/k1DG3bflLH.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/L7d5cE3D7h.png?imageslim)

上图这种取法会取出一个相对地址。

![mark](http://myphoto.mtianyan.cn/blog/180111/6ejHjBFb9c.png?imageslim)

将setting中配置的mediaurl放在前面可以补全地址。

### 设置media处理器

![mark](http://myphoto.mtianyan.cn/blog/180111/H0Gjeci29F.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/E18ecbCEEI.png?imageslim)

>注册之后，mediaurl将可以在html中使用

![mark](http://myphoto.mtianyan.cn/blog/180111/c2kA33KE9E.png?imageslim)

图片还是没有显示。因为url中没有处理图片相应路径的url

Django1.9.8 urls.py:

```python
from django.views.static import serve
    # 处理图片显示的url,使用Django自带serve,传入参数告诉它去哪个路径找，我们有配置好的路径MEDIAROOT
    url(r'^media/(?P<path>.*)$', serve, {"document_root": MEDIA_ROOT })
```

![mark](http://myphoto.mtianyan.cn/blog/180111/cKmHj6E9gi.png?imageslim)

Django2.0.1 urls.py:

```python
from django.views.static import serve
# 处理图片显示的url,使用Django自带serve,传入参数告诉它去哪个路径找，我们有配置好的路径MEDIAROOT
    re_path(r'^media/(?P<path>.*)', serve, {"document_root": MEDIA_ROOT })

```

### 完善xadmin的adminx为机构添加分类索引字段
organization/adminx.py

```python
# 机构课程信息管理器
class CourseOrgAdmin(object):
    list_display = ['name', 'desc','category', 'click_nums', 'fav_nums','add_time' ]
    search_fields = ['name', 'desc', 'category','click_nums', 'fav_nums']
    list_filter = ['name', 'desc','category' ,'click_nums', 'fav_nums','city__name','address','add_time']
```

### 去除加载小圈圈

static/css/style.css中scrollLoading置为空:

```
.scrollLoading {
}
```

>完成后台数据添加，列表页数据展示。对应7-3&7-4

## 7-5 列表分页功能

github搜索django-pure-pagination

```python
pip install django-pure-pagination
```

![mark](http://myphoto.mtianyan.cn/blog/180111/cA22hF4fi7.png?imageslim)

install app中添加:

```python
'pure_pagination',
```

可设置参数；

```
PAGINATION_SETTINGS = {
    'PAGE_RANGE_DISPLAYED': 10,
    'MARGIN_PAGES_DISPLAYED': 2,
    'SHOW_FIRST_PAGE_WHEN_INVALID': True,
}
```
![mark](http://myphoto.mtianyan.cn/blog/180111/8KAAL61KBk.png?imageslim)

`PAGE_RANGE_DISPLAYED`是总共会显示多少个page。(包括省略号，包括两边和中间)
`MARGIN_PAGES_DISPLAYED`是旁边会显示多少个。
`SHOW_FIRST_PAGE_WHEN_INVALID`:当输入页数不合法是否要跳到第一页

官方实例；

```python
from django.shortcuts import render_to_response

from pure_pagination import Paginator, EmptyPage, PageNotAnInteger

	# 尝试获取页数参数
    try:
        page = request.GET.get('page', 1)
    except PageNotAnInteger:
        page = 1
    # objects是取到的数据
    objects = ['john', 'edward', 'josh', 'frank']

    # Provide Paginator with the request object for complete querystring generation
    # 对于取到的数据进行分页处理。
    p = Paginator(objects, request=request)
    # 此时前台显示的就应该是我们此时获取的第几页的数据
    people = p.page(page)

    return render_to_response('index.html', {
        'people': people,
    }
```

我们对照着的实现：


```python
from pure_pagination import Paginator, EmptyPage, PageNotAnInteger
class OrgView(View):
    def get(self,request):
        # 查找到所有的课程机构
        all_orgs = CourseOrg.objects.all()
        # 总共有多少家机构使用count进行统计
        org_nums = all_orgs.count()
        # 取出所有的城市
        all_city = CityDict.objects.all()
        # 对课程机构进行分页
        # 尝试获取前台get请求传递过来的page参数
        # 如果是不合法的配置参数默认返回第一页
        try:
            page = request.GET.get('page', 1)
        except PageNotAnInteger:
            page = 1
        # 这里指从allorg中取五个出来，每页显示5个
        p = Paginator(all_orgs, 5, request=request)
        orgs = p.page(page)

        return render(request, "org-list.html", {
            "all_orgs":orgs,
            "all_city": all_city,
            "org_nums": org_nums,
        })

```

### 对于html中分页进行配置
>不再是objects，而是objectlist

![mark](http://myphoto.mtianyan.cn/blog/180111/jadkKHKkbI.png?imageslim)

>使用默认的render
![mark](http://myphoto.mtianyan.cn/blog/180111/fcae2A0E0c.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180111/8gcmfdHb4J.png?imageslim)


### 自定义html的样式

![mark](http://myphoto.mtianyan.cn/blog/180112/DmC94JAmh3.png?imageslim)

本小节完成对应commit:

>7-3, 4 & 5:完成列表数据展示列表分页功能：使用pure_pagination

## 7-6 分类筛选功能

![mark](http://myphoto.mtianyan.cn/blog/180112/jIL4FAdjJb.png?imageslim)

当用户点击某一个city时对应加上参数city的id

### 在后台处理这个city

![mark](http://myphoto.mtianyan.cn/blog/180112/59iFhGLaCD.png?imageslim)

获取传入的参数进行进一步筛选。

![mark](http://myphoto.mtianyan.cn/blog/180112/aiKJL6kCKL.png?imageslim)

>将city_id传回html，使得可以知道哪个是选中的。

![mark](http://myphoto.mtianyan.cn/blog/180112/mmChH6l2j9.png?imageslim)

因为city.id是后端传回来的值是一个int。所以我们要做类型转换。

![mark](http://myphoto.mtianyan.cn/blog/180112/GJa43hh95F.png?imageslim)

当city_id为空的时候，显示全部。

### 后台处理类别

```
  # 类别筛选
        category = request.GET.get('ct', "")
        if category:
            # 我们就在机构中作进一步筛选类别
            all_orgs = all_orgs.filter(category=category)
```

返回前台类别值以active

```
  return render(request, "org-list.html", {
            "all_orgs":orgs,
            "all_city": all_city,
            "org_nums": org_nums,
            "city_id":city_id,
            "category":category,
        })
```

![mark](http://myphoto.mtianyan.cn/blog/180112/Fgl4eHGJb8.png?imageslim)

对于类别做同样的ifequal判断

![mark](http://myphoto.mtianyan.cn/blog/180112/me43dl1f0g.png?imageslim)

如上图所示进行城市与分类的联动:

当选择全部类别的时候，就只通过当前城市id。
当选择全部城市的时候，就只通过当前目录id。
当两者都选的时候使用&连接。

刚才统计机构数目过早，应该移到后面后面已经筛选过后，

```
 # 总共有多少家机构使用count进行统计
        org_nums = all_orgs.count()
```

### 课程机构排名

```
   # 热门机构,如果不加负号会是有小到大。
        hot_orgs = all_orgs.order_by("-click_nums")[:3]
```

![mark](http://myphoto.mtianyan.cn/blog/180112/BiKdf066CL.png?imageslim)

循环时内置变量forloop.counter取当前循环到第几次

待完成:点击排名机构的连接

### 课程机构排序。

学习人数，课程数

organization/models.py
CourseOrg

```python
 # 当学生点击学习课程，找到所属机构，学习人数加1
    students = models.IntegerField(default=0, verbose_name=u"学习人数")
    # 当发布课程就加1
    course_nums =  models.IntegerField(default=0, verbose_name=u"课程数")
```

```
makemigrations organization
migrate organization
```

前端页面学习人数，添加参数sort

![mark](http://myphoto.mtianyan.cn/blog/180112/dbFlbHIBmb.png?imageslim)

```python
 # 进行排序
        sort = request.GET.get('sort', "")
        if sort:
            if sort == "students":
                all_orgs = all_orgs.order_by("-students")
            elif sort == "courses":
                all_orgs = all_orgs.order_by("-course_nums")
```

添加选择效果

![mark](http://myphoto.mtianyan.cn/blog/180112/DJeKIb9cK1.png?imageslim)

## 7-7 modelform 提交我要学习咨询1

对应表`userask`

`form`会对字段先做验证，然后保存到数据库中。

可以看到我们的forms和我们的model中有很多内容是一样的。我们如何让代码重复利用呢？

使用modelform解决这个问题。

```python
# encoding: utf-8
from django import forms

from operation.models import UserAsk

__author__ = 'mtianyan'
__date__ = '2018/1/12 0012 03:20'

# 普通版本的form
# class UserAskForm(forms.Form):
#     name = forms.CharField(required=True, min_length=2, max_length=20)
#     phone = forms.CharField(required=True, max_length=11, min_length=11)
#     course_name = forms.CharField(required=True, min_length=5, max_length=50)

# 进阶版本的modelform：它可以向model一样save
class AnotherUserForm(forms.ModelForm):
    # 继承之余还可以新增字段

    # 是由哪个model转换的
    class Meta:
        model = UserAsk
        # 我需要验证的字段
        fields = ['name','mobile','course_name']
```

### include的机制配置应用自己的url

django1.9.8 创建organization/urls.py:

```python
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/12 0012 06:20'

# encoding: utf-8
from organization.views import OrgView
from django.conf.urls import url

urlpatterns = [
    # 课程机构列表url
    url('list/&', OrgView.as_view(), name="org_list"),
```

django1.9.8 Mxonline2/urls.py:
删掉orglist,新增如下

```python
  # 课程机构app的url配置
    url(r"^org/", include('organization.urls',namespace="org")),
```


django2.0.1: 新建organization/urls.py

```python
# encoding: utf-8
from organization.views import OrgView

__author__ = 'mtianyan'
__date__ = '2018/1/12 0012 03:28'

from django.urls import path, re_path

urlpatterns = [
    # 课程机构列表url
    path('list/', OrgView.as_view(), name="org_list"),
]
```

django2.0.1: urls.py中:

删掉org_list，新增include

```
    # 课程机构app的url配置
    path("org/", include('organization.urls',namespace="org")),
```

使用命名空间防止重复


![mark](http://myphoto.mtianyan.cn/blog/180112/cH5Dmm14Cj.png?imageslim)


解决Django2.0.1报错:

```python
    'Specifying a namespace in include() without providing an app_name ' 
 django.core.exceptions.ImproperlyConfigured: Specifying a namespace in 
 include() without providing an app_name is not supported. Set the app_name 
 attribute in the included module, or pass a 2-tuple containing the list of 
 patterns and app_name instead. 
```

在自己的app下的urls中写上appname

```
# encoding: utf-8
from organization.views import OrgView

__author__ = 'mtianyan'
__date__ = '2018/1/12 0012 03:28'

from django.urls import path, re_path

app_name = "organization"

urlpatterns = [

    # 课程机构列表url
    path('list/', OrgView.as_view(), name="org_list"),

]
```

html中使用命名空间方式:

![mark](http://myphoto.mtianyan.cn/blog/180112/FkaCFJ4B7h.png?imageslim)

### 使用modelform做提交

比较合理的操作是异步的，不会对整个页面进行刷新。
如果有错误，显示错误。一种ajax的异步操作。

因此我们此时不能直接render一个页面回来。
应该是给前端返回json数据，而不是页面

`HttpResponse`类指明给用户返回哪种类型数据

```
from django.http import HttpResponse
```

配置一个modelform的view

```python
# 用户添加我要学习
class AddUserAskView(View):
    # 处理表单提交当然post
    def post(self,request):
        userask_form = UserAskForm(request.POST)
        # 判断该form是否有效
        if userask_form.is_valid():
            # 这里是modelform和form的区别
            # 它有model的属性
            # 当commit为true进行真正保存
            user_ask = userask_form.save(commit=True)
            # 这样就不需要把一个一个字段取出来然后存到model的对象中之后save

            # 如果保存成功,返回json字符串,后面content type是告诉浏览器的,
            return HttpResponse("{'status': 'success'}", content_type='application/json')
        else:
            # 如果保存失败，返回json字符串,并将form的报错信息通过msg传递到前端
            return HttpResponse("{'status': 'fail', 'msg':{0}}".format(userask_form.errors),  content_type='application/json')

```

### 配置相应的url

```
    # 添加我要学习
    path('add_ask/', AddUserAskView.as_view(), name="add_ask")
```
## 7-8 modelform 提交我要学习

### 分析ajax请求

```
<script>
    $(function(){
        $('#jsStayBtn').on('click', function(){
            $.ajax({
                cache: false,
                type: "POST",
  				url:"{% url "org:add_ask" %}",
                data:$('#jsStayForm').serialize(),
                async: true,
                success: function(data) {
                    if(data.status == 'success'){
                        $('#jsStayForm')[0].reset();
                        alert("提交成功")
                    }else if(data.status == 'fail'){
                        $('#jsCompanyTips').html(data.msg)
                    }
                },
            });
        });
    })

</script>
```

>监听这个button，用户如果点击了button。我们来向这个url进行post请求。
将我们的表单进行序列化。

form表单添加crsf_token

如果后台返回的状态值为success，那么我们将弹出提交成功。
失败，就会在错误提示框中写入。

### 手机号码正则表达式验证:

organization/forms.py

```
# 手机号的正则表达式验证
    def clean_mobile(self):
        mobile = self.cleaned_data['mobile']
        REGEX_MOBILE = "^1[358]\d{9}$|^147\d{8}$|^176\d{8}$"
        p = re.compile(REGEX_MOBILE)
        if p.match(mobile):
            return mobile
        else:
            raise forms.ValidationError(u"手机号码非法", code="mobile_invalid")
```

本小节完毕对应提交commit:

>7-7&8 使用modelform完成表单我要学习的异步提交

## 7-9 机构详情

- 机构首页
- 机构课程
- 机构介绍
- 机构讲师

登录xadmin添加基础的必要数据。添加课程与讲师。

课程中应该有一个外键指向它是哪个机构的。

courses/models.py

Django1.9.8中:

```python
from organization.models import CourseOrg

course_org = models.ForeignKey(CourseOrg, verbose_name=u"所属机构",null=True,blank=True)
```

django2.0.1下；

```python
    course_org = models.ForeignKey(CourseOrg,on_delete=models.CASCADE, verbose_name=u"所属机构",null=True,blank=True)
```

新增外键字段应该`null=true,blank=true。`

>因为历史数据中没有这个外键字段

```
makemigration course
migrate course
```

将前端给我们的org相关的四个页面拷进template

![mark](http://myphoto.mtianyan.cn/blog/180112/BeIFlkf97m.png?imageslim)

新建org_base页面

将org_home页面内容拿过去。

![mark](http://myphoto.mtianyan.cn/blog/180112/DFHg4mGkFb.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/k09CHekje2.png?imageslim)


- loadstaticfiles -> 改css文件路径->改js文件路径->改图片路径
- 改已经实现的url。->将子页面继承后需要改得地方使用block包裹。

将home页面清空

![mark](http://myphoto.mtianyan.cn/blog/180112/BBI8iLE97D.png?imageslim)

完成替换之后添加访问的view以及URl

organization/views.py:

```
class OrgHomeView(View):
    """
   机构首页
    """
    def get(self, request, org_id):
        # 根据id取到课程机构
        course_org = CourseOrg.objects.get(id= int(org_id))
        # 通过课程机构找到课程。内建的变量，找到指向这个字段的外键引用
        all_courses = course_org.course_set.all()[:4]
        all_teacher = course_org.teacher_set.all()[:2]

        return render(request, 'org-detail-homepage.html',{
           'all_courses':all_courses,
            'all_teacher':all_teacher,
        })
```

Django2.0.1下url

```
       # home页面,取纯数字
    re_path('home/(?P<org_id>\d+)/', OrgHomeView.as_view(), name="org_home"),
```

django1.9.8下url:

```
    # home页面,取纯数字
    url(r'home/(?P<org_id>\d+)/$', OrgHomeView.as_view(), name="org_home")
```

html中使用for循环遍历:

![mark](http://myphoto.mtianyan.cn/blog/180112/ECJ36kDclf.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/4j037g1DKj.png?imageslim)

>如上图可以直接通过外键字段再找到外键对象的字段

templates/org-list.html

配置里面跳转到详情页的url

![mark](http://myphoto.mtianyan.cn/blog/180112/90m2l2A0Dj.png?imageslim)

```python
        return render(request, 'org-detail-homepage.html',{
           'all_courses':all_courses,
            'all_teacher':all_teacher,
            'course_org': course_org,
        })
```

将`course_org`也return回来，就可以把网页里这部分值替换掉

templates/org_base.html

数值会随继承链向上传递。

![mark](http://myphoto.mtianyan.cn/blog/180112/0ED5bcC9Jf.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/I83bFbddC3.png?imageslim)

### 为讲师增加头像字段
organization/models.py

```
    image = models.ImageField(
        default= '',
        upload_to="teacher/%Y/%m",
        verbose_name=u"头像",
        max_length=100)
```

然后

```
makemgration organization
migrate organization
```

![mark](http://myphoto.mtianyan.cn/blog/180112/mL08LkChhe.png?imageslim)

使用for循环填充数据

![mark](http://myphoto.mtianyan.cn/blog/180112/cLg8IFB1jA.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/G2ICdgdDgh.png?imageslim)

同理可得，我们把机构课程页不同的部分拿出来即可

### 配置访问的view和url
organization/urls.py:

Django 2.0.1：

```
    # 访问课程
    re_path('course/(?P<org_id>\d+)/', OrgCourseView.as_view(), name="org_course"),
```
Django 1.9.8：

```
    # 访问课程
    url(r'^course/(?P<org_id>\d+)/$', OrgCourseView.as_view(), name="org_course"),
```

organization/views.py
```
class OrgCourseView(View):
    """
   机构课程列表页
    """
    def get(self, request, org_id):
        # 根据id取到课程机构
        course_org = CourseOrg.objects.get(id= int(org_id))
        # 通过课程机构找到课程。内建的变量，找到指向这个字段的外键引用
        all_courses = course_org.course_set.all()

        return render(request, 'org-detail-course.html',{
           'all_courses':all_courses,
            'course_org': course_org,
        })
```

base页面的left链接修改

>这里能直接用到course_org.id。是因为子页面render时都向上传递了course_org对象

![mark](http://myphoto.mtianyan.cn/blog/180112/b7heml49dh.png?imageslim)

使用for循环，填充内容。

![mark](http://myphoto.mtianyan.cn/blog/180112/5gjFji2d25.png?imageslim)

### 左侧active修改

因为现在没有值能判断当前是哪个页面。所以在orghomeview中传值回来current page
![mark](http://myphoto.mtianyan.cn/blog/180112/Kd5ijhIAgK.png?imageslim)
![mark](http://myphoto.mtianyan.cn/blog/180112/3CFjke2B3C.png?imageslim)

写两个view

```
class OrgDescView(View):
    """
   机构描述详情页
    """
    def get(self, request, org_id):
        # 向前端传值，表明现在在home页
        current_page = "desc"
        # 根据id取到课程机构
        course_org = CourseOrg.objects.get(id= int(org_id))
        # 通过课程机构找到课程。内建的变量，找到指向这个字段的外键引用
        # 向前端传值说明用户是否收藏
        has_fav = False
        # 必须是用户已登录我们才需要判断。
        if request.user.is_authenticated:
            if UserFavorite.objects.filter(user=request.user, fav_id=course_org.id, fav_type=2):
                has_fav = True
        return render(request, 'org-detail-desc.html',{
            'course_org': course_org,
            "current_page":current_page,
            "has_fav":has_fav,
        })

class OrgTeacherView(View):
    """
   机构讲师列表页
    """
    def get(self, request, org_id):
        # 向前端传值，表明现在在home页
        current_page = "teacher"
        # 根据id取到课程机构
        course_org = CourseOrg.objects.get(id= int(org_id))
        # 通过课程机构找到课程。内建的变量，找到指向这个字段的外键引用
        all_teachers = course_org.teacher_set.all()
        # 向前端传值说明用户是否收藏
        has_fav = False
        # 必须是用户已登录我们才需要判断。
        if request.user.is_authenticated:
            if UserFavorite.objects.filter(user=request.user, fav_id=course_org.id, fav_type=2):
                has_fav = True
        return render(request, 'org-detail-teachers.html',{
           'all_teachers':all_teachers,
            'course_org': course_org,
            "current_page":current_page,
            "has_fav":has_fav
        })

```

加两个url

Django2.0.1下:

```
    # 访问机构描述
    re_path('desc/(?P<org_id>\d+)/', OrgDescView.as_view(), name="org_desc"),

    # 访问机构讲师
    re_path('teacher/(?P<org_id>\d+)/', OrgTeacherView.as_view(), name="org_teacher"),
```

Django1.9.8下：

```
    # 访问机构描述
    url(r'^desc/(?P<org_id>\d+)/$', OrgDescView.as_view(), name="org_desc"),

    # 访问机构讲师
    url(r'^teacher/(?P<org_id>\d+)/$', OrgTeacherView.as_view(), name="org_teacher"),
```

修改base页面相关跳转链接，注意点：加上course_org.id

重载我们的pagepath，使得面包屑动态显示

![mark](http://myphoto.mtianyan.cn/blog/180112/2AdFE6He3D.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/4f7A1Ei2Fg.png?imageslim)

## 7-10 课程机构收藏功能

书写收藏的后台逻辑:


url配置

django2.0.1下:

```python
    # 机构收藏
    path('add_fav/', AddFavView.as_view(), name="add_fav"),
```

django1.9.8下；

```
    # 机构收藏
    url(r'^add_fav/$', AddFavView.as_view(), name="add_fav"),
```

配套的view；

```python
class AddFavView(View):
    """
    用户收藏与取消收藏功能
    """
    def post(self, request):
        # 表明你收藏的不管是课程，讲师，还是机构。他们的id
        # 默认值取0是因为空串转int报错
        id = request.POST.get('fav_id', 0)
        # 取到你收藏的类别，从前台提交的ajax请求中取
        type = request.POST.get('fav_type', 0)

        # 收藏与已收藏取消收藏
        # 判断用户是否登录:即使没登录会有一个匿名的user
        if not request.user.is_authenticated:
            # 未登录时返回json提示未登录，跳转到登录页面是在ajax中做的
            return HttpResponse('{"status":"fail", "msg":"用户未登录"}', content_type='application/json')
        exist_records = UserFavorite.objects.filter(user=request.user, fav_id=int(id), fav_type=int(type))
        if exist_records:
            # 如果记录已经存在， 则表示用户取消收藏
            exist_records.delete()
            return HttpResponse('{"status":"success", "msg":"收藏"}', content_type='application/json')
        else:
            user_fav = UserFavorite()
            # 过滤掉未取到fav_id type的默认情况
            if int(type) >0 and int(id) >0:
                user_fav.fav_id = int(id)
                user_fav.fav_type = int(type)
                user_fav.user = request.user
                user_fav.save()
                return HttpResponse('{"status":"success", "msg":"已收藏"}', content_type='application/json')
            else:
                return HttpResponse('{"status":"fail", "msg":"收藏出错"}', content_type='application/json')
```

相关处理收藏的jQuery代码写在org base Html

![mark](http://myphoto.mtianyan.cn/blog/180112/c8aa7f62L1.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180112/KelfeB7D2C.png?imageslim)

添加返回页面的收藏值。

```
 # 向前端传值说明用户是否收藏
        has_fav = False
        # 必须是用户已登录我们才需要判断。
        if request.user.is_authenticated:
            if UserFavorite.objects.filter(user=request.user, fav_id=course_org.id, fav_type=2):
                has_fav = True

 # return redener加上值
             "has_fav": has_fav
```

![mark](http://myphoto.mtianyan.cn/blog/180112/DI3GJKkJLI.png?imageslim)

前台 org_base.html中

![mark](http://myphoto.mtianyan.cn/blog/180112/3gBdC96Aij.png?imageslim)

同理添加剩下的几个页面的。

第七章完结撒花。对应commit:

>7-9&10&11&12将机构详情展示完毕，为课程机构添加了收藏功能。修复了index未登录状态下爆炸的错误


{% cq %} 三年六班，三年六班，李子明，李子明同学，你妈妈拿了两罐旺仔牛奶给你 {% endcq %}

{% note success %}  
上帝说得有课程！ 得有详情 ！点了开始学习，得有章节！章节得有视频。
课程还得能评论下，还得有相关课程。于是这章出现了。
{% endnote %}

# 课程相关功能实现

## 8-1 课程列表

拷贝课程列表页到template目录

创建课程相关的urls.py

Mxonline2/urls.py中声明包含到course的url中：

```
    # 课程app的url配置
    url(r"^course/", include('courses.urls', namespace="course")),
```

django2.0.1版本:

```
    # 课程app的url配置
    path("course/", include('courses.urls', namespace="course")),
```

书写处理列表展示相关的view

courses/views.py

```
class CourseListView(View):
    def get(self, request):
        return render(request, "course-list.html", { })
```

courses/urls.py

```
# encoding: utf-8
from courses.views import CourseListView

__author__ = 'mtianyan'
__date__ = '2018/1/13 0013 00:39'

from django.conf.urls import url

urlpatterns = [
    # 课程列表url
    url(r'^list/$', CourseListView.as_view(), name="list"),

]
```

django2.0.1版本:

```
# encoding: utf-8
__author__ = 'mtianyan'
__date__ = '2018/1/13 0013 01:57'

# encoding: utf-8
from courses.views import CourseListView
from django.urls import path
app_name = "courses"
urlpatterns = [
    # 课程列表url
    path('list/', CourseListView.as_view(), name="list"),

]

```

此时访问没有样式。我们开始对于course list html进行工作
可以观察到它和orglist一样可以有共同的头尾。所以继承base页面

xadmin中添加一些课程。

然后在view中返回课程数据

```
class CourseListView(View):
    def get(self, request):
        all_course = Course.objects.all()
        return render(request, "course-list.html", {
            "all_course":all_course,
            
        })
```

![mark](http://myphoto.mtianyan.cn/blog/180113/32hbAB04ec.png?imageslim)

保留一个div

![mark](http://myphoto.mtianyan.cn/blog/180113/L1Jm283bck.png?imageslim)

>通过外键字段取外键表中字段

### 分页功能

拷贝代码:

```
from pure_pagination import Paginator, EmptyPage, PageNotAnInteger
 # 对课程机构进行分页
        # 尝试获取前台get请求传递过来的page参数
        # 如果是不合法的配置参数默认返回第一页
        try:
            page = request.GET.get('page', 1)
        except PageNotAnInteger:
            page = 1
        # 这里指从allorg中取五个出来，每页显示5个
        p = Paginator(all_orgs, 4, request=request)
        orgs = p.page(page)
```

改动完成：

```
class CourseListView(View):
    def get(self, request):
        all_course = Course.objects.all()
        # 对课程进行分页
        # 尝试获取前台get请求传递过来的page参数
        # 如果是不合法的配置参数默认返回第一页
        try:
            page = request.GET.get('page', 1)
        except PageNotAnInteger:
            page = 1
        # 这里指从allorg中取五个出来，每页显示5个
        p = Paginator(all_course,6 , request=request)
        courses = p.page(page)
        return render(request, "course-list.html", {
            "all_course":courses,

        })
```


在html中使用时注意object_list

>此时的all_course已经不是一个queryset，而是一个purepage对象。

![mark](http://myphoto.mtianyan.cn/blog/180113/JBm95D0fK8.png?imageslim)

### 对于页码进行修改

![mark](http://myphoto.mtianyan.cn/blog/180113/L7Ibjh9g72.png?imageslim)

直接把orglist中的那段拿过来就行了。自行替换变量名称

此时已经好了。

### 排序功能

将之前的sort逻辑拷贝过来:

```
# 进行排序
        sort = request.GET.get('sort', "")
        if sort:
            if sort == "students":
                all_orgs = all_orgs.order_by("-students")
            elif sort == "courses":
                all_orgs = all_orgs.order_by("-course_nums")
```

修改完成:

```
        # 进行排序
        sort = request.GET.get('sort', "")
        if sort:
            if sort == "students":
                all_course = all_course.order_by("-students")
            elif sort == "hot":
                all_course = all_course.order_by("-click_nums")
```

应放在分页之前。让分页处理所有筛选过的数据

return render时添加

```
            "sort":sort,
```

>用来判断激活状态。

![mark](http://myphoto.mtianyan.cn/blog/180113/0DhjiABaA4.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180113/al219GFJJ1.png?imageslim)

修改a标签参数

```
    # 热门课程推荐
        hot_courses = Course.objects.all().order_by("-students")[:3]
        return render
         "hot_courses":hot_courses
```

修改html中
![mark](http://myphoto.mtianyan.cn/blog/180113/FkIJ7mCjH3.png?imageslim)

for循环填充内容

![mark](http://myphoto.mtianyan.cn/blog/180113/ji6bee4D31.png?imageslim)

这里的degree我们在数据库中填写的是字母。如何显示为中文。

- 个人猜测: template if

get_degree_display degree是字段名。专门用于choice字段显示

本小节完成对应commit：

>8-1完成课程列表页展示，分页，热门课程。

## 8-2 课程详情页1

拷贝course_detail进入template目录

可以看出这个页面也是继承base页面的。将course_list的页面框架拿过来

替换面包屑。

![mark](http://myphoto.mtianyan.cn/blog/180113/Jb07I8Ef1f.png?imageslim)

配置url访问

django2.0.1：

```
    # 课程详情页
    re_path('course/(?P<course_id>\d+)/', CourseDetailView.as_view(), name="course_detail"),
```

书写对应访问的view

```
 课程详情处理view

class CourseDetailView(View):
    def get(self, request, course_id):
        return  render(request, "course-detail.html", {

        })
```

尝试访问：

在列表展示页放入详情的url。

![mark](http://myphoto.mtianyan.cn/blog/180113/6Ca5l1lBCf.png?imageslim)

有参数类型的把参数也传进来

进行数据填充:先取出当前的课程

```
        # 此处的id为表默认为我们添加的值。
        course = Course.objects.get(id = int(course_id))

                return  render(request, "course-detail.html", {
            "course":course,
        })
```

html中取出数据:

![mark](http://myphoto.mtianyan.cn/blog/180113/mk6Gb823k6.png?imageslim)

课程的章节数如何实现？

models.py中自定义方法

```
    def get_zj_nums(self):
        # 获取课程章节数的方法
        return self.lesson_set.all().count()
```

添加课程类别字段

```
    category = models.CharField(max_length=20, default=u"", verbose_name=u"课程类别")
```

```
makemigrations
migrate
```

operation中专门有张表是做用户学习记录的。

UserCourse查询有哪些学生学习了这门课

```
    # 获取学习这门课程的用户
    def get_learn_users(self):
        # 谁的里面添加了它做外键，他都可以取出来
        return self.usercourse_set.all()[:5]
```

![mark](http://myphoto.mtianyan.cn/blog/180113/HKLll9bL4F.png?imageslim)

链式调用取出数据

添加一些用户课程进行验证

![mark](http://myphoto.mtianyan.cn/blog/180113/3kmjFehf7F.png?imageslim)

可以看到已经大功告成

课程详情的view中添加clicknums+1

```
        # 增加课程点击数
        course.click_nums += 1
        course.save()
```

![mark](http://myphoto.mtianyan.cn/blog/180113/93LBHie41d.png?imageslim)

## 8-3 课程详情页2

![mark](http://myphoto.mtianyan.cn/blog/180113/F0jLggJge6.png?imageslim)

tab_cont1 中填充我们自己的内容。

![mark](http://myphoto.mtianyan.cn/blog/180113/8fDFkB7DIm.png?imageslim)

教师数自定义函数

```
def get_teacher_nums:
	return self.teacher_set.all().count
```

不用自定义函数的方法如下

![mark](http://myphoto.mtianyan.cn/blog/180113/37jDHdha1l.png?imageslim)

### 课程是否相关

定义课程的tag ，如果tag相同，那么是相关课程。

courses/models.py:

```
    tag = models.CharField(max_length=15, verbose_name=u"课程标签", default=u"")
```

更改数据库后必然。此处略。

```
 tag = course.tag
        if tag:
        # 需要从1开始不然会推荐自己
            relate_courses = Course.objects.filter(tag=tag)[1:2]
        else:
            relate_courses = []
```

return render加上：

```
            "relate_courses":relate_courses,
```

### 收藏功能:

将block js写到页面底部。


```
<script type="text/javascript">
//收藏分享
function add_fav(current_elem, fav_id, fav_type){
    $.ajax({
        cache: false,
        type: "POST",
        url:"{% url "org:add_fav" %}",
        data:{'fav_id':fav_id, 'fav_type':fav_type},
        async: true,
        beforeSend:function(xhr, settings){
            xhr.setRequestHeader("X-CSRFToken", "{{ csrf_token }}");
        },
        success: function(data) {
            if(data.status == 'fail'){
                if(data.msg == '用户未登录'){
                    window.location.href="/login/";
                }else{
                    alert(data.msg)
                }

            }else if(data.status == 'success'){
                current_elem.text(data.msg)
            }
        },
    });
}

$('#jsLeftBtn').on('click', function(){
    add_fav($(this), {{ course.id }}, 1);
});

$('#jsRightBtn').on('click', function(){
    add_fav($(this), {{ course.course_org.id }}, 2);
});


</script>
```

刷新后又不见了的问题，从view中传递has_fav的参数。前台进行判断。

```
  # 是否收藏课程
        has_fav_course = False
        has_fav_org = False

        # 必须是用户已登录我们才需要判断。
        if request.user.is_authenticated:
            if UserFavorite.objects.filter(user=request.user, fav_id=course.id, fav_type=1):
                has_fav_course = True
            if UserFavorite.objects.filter(user=request.user, fav_id=course.course_org.id, fav_type=2):
                has_fav_org = True
```

return render

```
            "has_fav_course":has_fav_course,
            "has_fav_org":has_fav_org,
```

html中使用；

![mark](http://myphoto.mtianyan.cn/blog/180113/KJc25I0KF8.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180113/mKHhjj2d32.png?imageslim)

>8-2&3完成课程详情页展示，课程详情页机构，相关推荐课程。收藏课程，收藏机构。

## 8-4 课程章节信息

章节信息，评论信息。

course comments 和 course video放入 template

它也有head和foot继承我们的base页面

![mark](http://myphoto.mtianyan.cn/blog/180113/D4L8a0lmI0.png?imageslim)

配置相应的url:

```python
# 处理课程章节信息页面的view

class CourseInfoView(View):
    def get(self, request, course_id):
        # 此处的id为表默认为我们添加的值。
        course = Course.objects.get(id=int(course_id))
        # 是否收藏课程
        return render(request, "course-video.html", {
            "course": course,
        })

```

```
    # 课程章节信息页
    url(r'^info/(?P<course_id>\d+)/$', CourseInfoView.as_view(), name="course_info"),
```

用户点击开始学习链接修改

![mark](http://myphoto.mtianyan.cn/blog/180113/hBAAmHlm4g.png?imageslim)

为课程添加章节以及视频。

## 8-5 章节视频信息

为video表添加视频对应的url信息。

```
  url = models.CharField(max_length=200, default="http://blog.mtianyan.cn/" ,verbose_name=u"访问地址")
```

将章节信息填充进页面

通过课程可以找到章节:course.lesson_set

![mark](http://myphoto.mtianyan.cn/blog/180113/5GjjhDe40D.png?imageslim)

video的时长添加

```
 # 使用分钟做后台记录(存储最小单位)前台转换
    learn_times = models.IntegerField(default=0, verbose_name=u"学习时长(分钟数)")
```

资源下载功能:


后台自行上传点文件

```
all_resources = CourseResource.objects.filter(course=course)

          "all_resources":all_resources,
```

或者前端直接:

![mark](http://myphoto.mtianyan.cn/blog/180113/CL7fke0LGF.png?imageslim)

创建课程与讲师之间的外键关联

```
    teacher = models.ForeignKey(Teacher,verbose_name=u"讲师", null=True, blank=True)
```

前往课程，设置讲师。

**注意:不要在Unicode方法里使用外键字段很容易报错。**

增加课程需知字段和老师告诉你学什么？

```
  you_need_know = models.CharField(max_length=300, default=u"一颗勤学的心是本课程必要前提",verbose_name=u"课程须知")
    teacher_tell = models.CharField(max_length=300, default=u"按时交作业,不然叫家长",verbose_name=u"老师告诉你")
```

将这两个字段显示到页面。

对应commit:

8-4&5完成课程章节信息，课程资源，课程老师信息。

## 8-6 课程评论页面

配置课程评论的url和view

```
class CommentsView(View):
    def get(self, request, course_id):
        # 此处的id为表默认为我们添加的值。
        course = Course.objects.get(id=int(course_id))
        all_resources = CourseResource.objects.filter(course=course)
        return render(request, "course-comment.html", {
            "course": course,
            "all_resources": all_resources,
        })

```

```
# 课程章节信息页
    re_path('comments/(?P<course_id>\d+)/', CommentsView.as_view(), name="course_comments"),
```

course video中跳转到评论链接

发表评论功能

ajax操作。如果发布成功就会刷新页面。

新建view用于添加评论:

```
# ajax方式添加评论
class AddCommentsView(View):
    def post(self, request):
        if not request.user.is_authenticated:
            # 未登录时返回json提示未登录，跳转到登录页面是在ajax中做的
            return HttpResponse('{"status":"fail", "msg":"用户未登录"}', content_type='application/json')
        course_id = request.POST.get("course_id", 0)
        comments = request.POST.get("comments", "")
        if int(course_id) > 0 and comments:
            course_comments = CourseComments()
            # get只能取出一条数据，如果有多条抛出异常。没有数据也抛异常
            # filter取一个列表出来，queryset。没有数据返回空的queryset不会抛异常
            course = Course.objects.get(id = int(course_id))
            # 外键存入要存入对象
            course_comments.course = course
            course_comments.comments = comments
            course_comments.user = request.user
            course_comments.save()
            return HttpResponse('{"status":"success", "msg":"评论成功"}', content_type='application/json')
        else:
            return HttpResponse('{"status":"fail", "msg":"评论失败"}', content_type='application/json')
```

添加配套的url:

```python
    # 添加课程评论,已经把参数放到post当中了
    path('add_comment/', AddCommentsView.as_view(), name="add_comment"),
```

js代码

```
<script type="text/javascript">
    //添加评论
    $('#js-pl-submit').on('click', function(){
        var comments = $("#js-pl-textarea").val()
        if(comments == ""){
            alert("评论不能为空")
            return
        }
        $.ajax({
            cache: false,
            type: "POST",
            url:"{% url 'course:add_comment' %}",
            data:{'course_id':{{ course.id }}, 'comments':comments},
            async: true,
            beforeSend:function(xhr, settings){
                xhr.setRequestHeader("X-CSRFToken", "{{ csrf_token }}");
            },
            success: function(data) {
                if(data.status == 'fail'){
                    if(data.msg == '用户未登录'){
                        window.location.href="/login/";
                    }else{
                        alert(data.msg)
                    }

                }else if(data.status == 'success'){
                    window.location.reload();//刷新当前页面.
                }
            },
        });
    });

</script>
```

后端已经将all_comments传过来了。然后for循环输出。

本小节完毕对应commit:

```
8-6完成课程评论功能，添加评论并展示到页面。
```

## 8-7 相关课程推荐:

>学过该课程的还学过

CourseInfoView

添加

```python
# 选出学了这门课的学生关系
        user_courses = UserCourse.objects.filter(course= course)
        # 从关系中取出user_id
        user_ids = [user_course.user_id for user_course in user_courses]
        # 这些用户学了的课程,外键会自动有id，取到字段
        all_user_courses = UserCourse.objects.filter(user_id__in=user_ids)
        # 取出所有课程id
        course_ids = [all_user_course.course_id for all_user_course in all_user_courses]
        # 获取学过该课程用户学过的其他课程
        relate_courses = Course.objects.filter(id__in=course_ids).order_by("-click_nums")[:5]
        # 是否收藏课程
        return render(request, "course-video.html", {
            "course": course,
            "all_resources": all_resources,
            "relate_courses":relate_courses,
        })
```

>重点: 两个下划线代表我传进来的是一个list，你进行遍历。

comments也做同样处理

用户未登录，不要让他能点进view

如果使用的是方法型编程可以使用装饰器`loginrequired`

而我们使用的是类。所以要继承。

```python
from django.contrib.auth.mixins import LoginRequiredMixin
class CourseInfoView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'redirect_to'
```

>8-7完成相关课程推荐功能，取出相关课程去除本身。课程评论login require鉴权添加。登录页面重定向回登录前浏览页面

## 8-8 课程播放页面

将视频播放页面拷贝到template目录

使用开源库video js

![mark](http://myphoto.mtianyan.cn/blog/180113/f0j8Ffec87.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180113/kCAHJkbAdb.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180113/26FehA9AAf.png?imageslim)

添加访问的url和view；

```
    # 课程视频播放页
    url(r'^video/(?P<video_id>\d+)/$', VideoPlayView.as_view(), name="video_play"),
```

```python
# 播放视频的view
class VideoPlayView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'
    def get(self, request, video_id):
        # 此处的id为表默认为我们添加的值。
        video = Video.objects.get(id=int(video_id))
        # 找到对应的course
        course = video.lesson.course
        # 查询用户是否开始学习了该课，如果还未学习则，加入用户课程表
        user_courses = UserCourse.objects.filter(user=request.user, course=course)
        if not user_courses:
            user_course = UserCourse(user=request.user, course=course)
            user_course.save()
        # 查询课程资源
        all_resources = CourseResource.objects.filter(course=course)
        # 选出学了这门课的学生关系
        user_courses = UserCourse.objects.filter(course=course)
        # 从关系中取出user_id
        user_ids = [user_course.user_id for user_course in user_courses]
        # 这些用户学了的课程,外键会自动有id，取到字段
        all_user_courses = UserCourse.objects.filter(user_id__in=user_ids)
        # 取出所有课程id
        course_ids = [user_course.course_id for user_course in all_user_courses]
        # 获取学过该课程用户学过的其他课程
        relate_courses = Course.objects.filter(id__in=course_ids).order_by("-click_nums").exclude(id=course.id)[:4]
        # 是否收藏课程
        return render(request, "course-play.html", {
            "course": course,
            "all_resources": all_resources,
            "relate_courses": relate_courses,
            "video": video,
        })



```

title 与面包屑的修改

对应commit:

>第八章公开课模块全部完成，完结撒花。

{% cq %} 师者，所以传道受业解惑也 - 韩愈 {% endcq %}

{% note  %}  
上帝说得课程得有老师来讲！ 得有老师的详情 ！
老师应该可以收藏分享，我得看到老师是哪个机构，它讲了啥课。于是这章出现了。
{% endnote %}


授课讲师列表页。列表页右侧是讲师排行榜。列表页可以进行排序

点击课程讲师进入课程讲师的详情页: 分享 & 点击收藏 右边是讲师所属课程机构

下面是讲师的课程详情。

# 讲师相关功能实现

## 9-1 讲师列表页

teacherlist 和 teacher detail 一起放到template目录之下

继承base页面

![mark](http://myphoto.mtianyan.cn/blog/180113/ljke7AEDjj.png?imageslim)

### 书写view与配置url

```
    # 讲师列表
    path('teacher_list/', TeacherListView.as_view(), name="teacher_list"),
```

添加讲师的年龄字段

```
    age = models.IntegerField(default=18, verbose_name=u"年龄")
```

### 分页仿照orglist 注意object_list

view

```
# 课程讲师列表页
class TeacherListView(View):
        def get(self, request):
            all_teacher = Teacher.objects.all()
            # 总共有多少老师使用count进行统计
            teacher_nums = all_teacher.count()
            # 对讲师进行分页
            # 尝试获取前台get请求传递过来的page参数
            # 如果是不合法的配置参数默认返回第一页
            try:
                page = request.GET.get('page', 1)
            except PageNotAnInteger:
                page = 1
            # 这里指从allorg中取五个出来，每页显示5个
            p = Paginator(all_teacher, 4, request=request)
            teachers = p.page(page)
            return render(request, "teachers-list.html", {
            "all_teacher":teachers,
            "teacher_nums":teacher_nums
            })
```

### 排序 & 讲师排行榜

```
 sort = request.GET.get("sort", "")
            if sort:
                if sort == "hot":
                    all_teacher = all_teacher.order_by("-click_nums")
```

```
 "sort":sort
```

将sort return到前端。实现active

排行榜讲师

```
            # 排行榜讲师
            rank_teacher = Teacher.objects.all().order_by("-fav_nums")[:5]
```

![mark](http://myphoto.mtianyan.cn/blog/180114/k03L400l4c.png?imageslim)

forloop.count 取出当前是第几次循环

## 9-2 讲师详情页

![mark](http://myphoto.mtianyan.cn/blog/180114/H49BkEleaA.png?imageslim)

### 配置url和view

列表页中配置入口


```
# 教师详情页面

class TeacherDetailView(View):
    def get(self, request, teacher_id):
        teacher = Teacher.objects.get(id = int(teacher_id))
        all_course = teacher.course_set.all()
        # 排行榜讲师
        rank_teacher = Teacher.objects.all().order_by("-fav_nums")[:5]

        has_fav_teacher = False
        if UserFavorite.objects.filter(user=request.user, fav_type=3, fav_id= teacher.id):
            has_fav_teacher = True
        has_fav_org = False
        if  UserFavorite.objects.filter(user=request.user, fav_type=2, fav_id= teacher.org.id):
            has_fav_org = True
        return render(request, "teacher-detail.html", {
            "teacher":teacher,
            "all_course":all_course,
            "rank_teacher":rank_teacher,
            "has_fav_teacher":has_fav_teacher,
            "has_fav_org":has_fav_org,
        })

```

```
    # 访问机构讲师
    re_path('teacher/detail/(?P<teacher_id>\d+)/', TeacherDetailView.as_view(), name="teacher_detail"),
```

>第九章完结



{% cq %} 不以个人为中心, 但我们得有个个人中心。 {% endcq %}

{% note default %}  
做一做全局导航，做一做个人中心，做一做全局搜索。
洒洒水啦。
{% endnote %}

# 全局导航&个人中心&全局搜索

## 配置全局导航

让index页面也继承base页面

base页面的导航栏配置

![mark](http://myphoto.mtianyan.cn/blog/180114/4LGd72eA4J.png?imageslim)

但是现在我们不知道当前是哪一个页面，因为后端没有传值过来

后台的每个view中添加current nav字段。然后向上传递到base页面

为了满足前台有current view的值，我们写的每个view都得加上这个字段。

小技巧：根据request的地址中的前几位来判断在哪一个区域之下

request.path

修改url中

```
    # 访问机构讲师
    url(r'^org_teacher/(?P<org_id>\d+)/$', OrgTeacherView.as_view(), name="org_teacher"),
```

![mark](http://myphoto.mtianyan.cn/blog/180114/kGG5I71CE1.png?imageslim)

## 全局搜索功能开发

搜索跳到列表展示

courselist后加参数keywords

搜索的代码放在deco-common js中


课程的搜索功能：


```
        # 搜索功能
        search_keywords = request.GET.get('keywords','')
        if search_keywords:
            # 在name字段进行操作,做like语句的操作。i代表不区分大小写
            # or操作使用Q
            all_course = all_course.filter(Q(name__icontains=search_keywords)|Q(desc__icontains=search_keywords)|Q(detail__icontains=search_keywords))


```

```
            "search_keywords":search_keywords,
```

## 个人中心信息展示

将用户中心相关的六个页面，全部拷贝进template


新建usercenter base页面

![mark](http://myphoto.mtianyan.cn/blog/180114/3I2G5kaK1G.png?imageslim)

配置url

```
    # user app的url配置
    url(r"^users/", include('users.urls', namespace="users")),
```

```
# encoding: utf-8
from .views import UserInfoView

__author__ = 'mtianyan'
__date__ = '2018/1/14 0014 04:00'


from django.conf.urls import url

urlpatterns = [
    # 用户信息
    url(r'^info/$', UserInfoView.as_view(), name="user_info"),
]
```

```
# 用户个人信息view
class UserInfoView(LoginRequiredMixin,View):
    login_url = '/login/'
    redirect_field_name = 'next'
    def get(self, request):
        return render(request, "usercenter-info.html", {

        })

```

user app 下新建url

django自带的filter 

request.user.mobile|default_if_none:''


## 修改密码和修改头像

新建url 和 view


小技巧:

>django的xadmin和admin当中，实际上是可以对form定义为文件的时候，是可以自动对上传的文件做保存的。
使用form的一个字段定义一个文件类型。把字段取出来就是内存中的文件。
赋值到user.image 就完成图片的一个存储。

users/forms.py：

```
# 用于文件上传，修改头像
class UploadImageForm(forms.ModelForm):

    class Meta:
        model = UserProfile
        fields = ['image']
```

实例化时，传进来是post 和 文件类型的request 存放地址

![mark](http://myphoto.mtianyan.cn/blog/180114/Jabljb878I.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180114/Lb09b3457I.png?imageslim)

上传文件时通过一个form完成的。

![mark](http://myphoto.mtianyan.cn/blog/180114/1IGKhbagJC.png?imageslim)

必须指明enctype，才能把文件类型传递到后台

url 和view

```
    # 用户头像上传
    url(r'^image/upload/$', UploadImageView.as_view(), name="image_upload"),
```

```
# 用户上传图片的view:用于修改头像
class UploadImageView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'
    def post(self, request):
        # 这时候用户上传的文件就已经被保存到imageform了
        image_form = UploadImageForm(request.POST, request.FILES)
        if image_form.is_valid():
            pass
```

![mark](http://myphoto.mtianyan.cn/blog/180114/he98j111Lj.png?imageslim)

这里的name必须和form中的一样

![mark](http://myphoto.mtianyan.cn/blog/180114/J6kBci76lA.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180114/3Bm665idcK.png?imageslim)

>所有验证通过的字段放在cleaned data

```
# 用户上传图片的view:用于修改头像
class UploadImageView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'
    def post(self, request):
        # 这时候用户上传的文件就已经被保存到imageform了 ，为modelform添加instance值直接保存
        image_form = UploadImageForm(request.POST, request.FILES, instance=request.user)
        if image_form.is_valid():
            image_form.save()
            # # 取出cleaned data中的值,一个dict
            # image = image_form.cleaned_data['image']
            # request.user.image = image
            # request.user.save()
            return HttpResponse('{"status":"success"}', content_type='application/json')
        else:
            return HttpResponse('{"status":"fail"}', content_type='application/json')
```

修改密码功能:

```
# 在个人中心修改用户密码
class UpdatePwdView(View):
    def post(self, request):
        modiypwd_form = ModifyPwdForm(request.POST)
        if modiypwd_form.is_valid():
            pwd1 = request.POST.get("password1", "")
            pwd2 = request.POST.get("password2", "")
            # 如果两次密码不相等，返回错误信息
            if pwd1 != pwd2:
                return HttpResponse('{"status":"fail", "msg":"密码不一致"}', content_type='application/json')
            # 如果密码一致
            user =request.user
            # 加密成密文
            user.password = make_password(pwd2)
            # save保存到数据库
            user.save()
            return HttpResponse('{"status":"success"}', content_type='application/json')
        # 验证失败说明密码位数不够。
        else:
            return HttpResponse('{"status":"fail", "msg":"填写错误请检查"}', content_type='application/json')
```

![mark](http://myphoto.mtianyan.cn/blog/180114/CC02dfbG57.png?imageslim)

必须与我们的form中定义的一致

实现的js代码在deco-user.js

js文件中的url就一定不能用template的模板语言了

## 修改邮箱提交form表单

有两个接口需要完成。点击获取验证码时，后台需要向用户新邮箱发送验证码。
邮箱如果出错，会返回错误信息。

输入了邮箱和验证码，验证是否匹配。

### 获取验证码接口:

配置url:

```
    # 专用于发送验证码的
    url(r'^sendemail_code/$', SendEmailCodeView.as_view(), name="sendemail_code"),
```

新增邮箱验证码model类型

```
SEND_CHOICES = (
        ("register", u"注册"),
        ("forget", u"找回密码"),
        ("update_email", u"修改邮箱")
    )
           max_length=20,
```

发送邮箱验证码view

```
class SendEmailCodeView(LoginRequiredMixin, View):
    def get(self,request):
        # 取出需要发送的邮件
        email = request.GET.get("email", "")

        # 不能是已注册的邮箱
        if UserProfile.objects.filter(email=email):
            return HttpResponse('{"email":"邮箱已经存在"}', content_type='application/json')
        send_register_eamil(email, "update_email")
        return HttpResponse('{"status":"success"}', content_type='application/json')
```

发送邮箱验证码的功能放在deco-user.js中

```
    elif send_type == "update_email":
        code = random_str(4)
        email_title = "mtianyan慕课小站 修改邮箱验证码"
        email_body = loader.render_to_string(
            "email_update_email.html",  # 需要渲染的html模板
            {
                "active_code": code  # 参数
            }
        )
        msg = EmailMessage(email_title, email_body, EMAIL_FROM, [email])
        msg.content_subtype = "html"
        send_status = msg.send()
```

### 修改邮箱的view

```
# 修改邮箱的view:
class UpdateEmailView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'
    def post(self, request):
        email = request.POST.get("email", "")
        code = request.POST.get("code", "")

        existed_records = EmailVerifyRecord.objects.filter(email=email, code=code, send_type='update_email')
        if existed_records:
            user = request.user
            user.email = email
            user.save()
            return HttpResponse('{"status":"success"}', content_type='application/json')
        else:
            return HttpResponse('{"email":"验证码无效"}', content_type='application/json')
```

修改邮箱的url

```
    url(r'^update_email/$', UpdateEmailView.as_view(), name="update_email"),
```

为userInfo view增加post方法。使用modelform完成直接提交

```
    def post(self,request):
        # 不像用户咨询是一个新的。需要指明instance。不然无法修改，而是新增用户
        user_info_form = UserInfoForm(request.POST, instance=request.user)
        if user_info_form.is_valid():
            user_info_form.save()
```

user_info_form

```
# 用于个人中心修改个人信息
class UserInfoForm(forms.ModelForm):

    class Meta:
        model = UserProfile
        fields = ['nick_name','gender','birthday','address','mobile']
```

![mark](http://myphoto.mtianyan.cn/blog/180114/ADFBmE7a6B.png?imageslim)

配置url和view

```
    # 用户中心我的课程
    path('mycourse/', MyCourseView.as_view(), name="mycourse"),
```

usercenter base中添加链接

```
# 个人中心页我的课程

class MyCourseView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'

    def get(self, request):
        user_courses = UserCourse.objects.filter(user=request.user)
        return render(request, "usercenter-mycourse.html", {
            "user_courses":user_courses,
        })
```

![mark](http://myphoto.mtianyan.cn/blog/180114/8LAe6f1dl7.png?imageslim)

### 配置url和view

```
    # 我收藏的课程机构
    path('myfav/org/', MyFavOrgView.as_view(), name="myfav_org"),
```

```
class MyFavOrgView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'

    def get(self, request):
        org_list = []
        fav_orgs= UserFavorite.objects.filter(user=request.user, fav_type=2)
        # 上面的fav_orgs只是存放了id。我们还需要通过id找到机构对象
        for fav_org in fav_orgs:
            # 取出fav_id也就是机构的id。
            org_id = fav_org.fav_id
            # 获取这个机构对象
            org = CourseOrg.objects.get(id=org_id)
            org_list.append(org)
        return render(request, "usercenter-fav-org.html", {
            "org_list": org_list,
        })

```

```
# 我收藏的授课讲师

class MyFavTeacherView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'

    def get(self, request):
        teacher_list = []
        fav_teachers= UserFavorite.objects.filter(user=request.user, fav_type=3)
        # 上面的fav_orgs只是存放了id。我们还需要通过id找到机构对象
        for fav_teacher in fav_teachers:
            # 取出fav_id也就是机构的id。
            teacher_id = fav_teacher.fav_id
            # 获取这个机构对象
            teacher = Teacher.objects.get(id=teacher_id)
            teacher_list.append(teacher)
        return render(request, "usercenter-fav-teacher.html", {
            "teacher_list": teacher_list,
        })
```

url

```
    # 我收藏的课程机构
    path('myfav/org/', MyFavOrgView.as_view(), name="myfav_org"),

    # 我收藏的授课讲师
    path('myfav/teacher/', MyFavTeacherView.as_view(), name="myfav_teacher"),
```

### 配置view和url

```
# 我收藏的课程

class MyFavCourseView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'

    def get(self, request):
        course_list = []
        fav_courses = UserFavorite.objects.filter(user=request.user, fav_type=1)
        # 上面的fav_orgs只是存放了id。我们还需要通过id找到机构对象
        for fav_course in fav_courses:
            # 取出fav_id也就是机构的id。
            course_id = fav_course.fav_id
            # 获取这个机构对象
            course = Course.objects.get(id=course_id)
            course_list.append(course)
        return render(request, "usercenter-fav-course.html", {
            "course_list": course_list,
        })
```

```
    # 我收藏的课程
    path('myfav/course/', MyFavCourseView.as_view(), name="myfav_course"),
```

## 取消收藏

templates/usercenter-fav-course.html

![mark](http://myphoto.mtianyan.cn/blog/180114/i92c3ffgJD.png?imageslim)


![mark](http://myphoto.mtianyan.cn/blog/180114/LjGjh0B3cL.png?imageslim)

取消收藏的代码在base页面中。三个js。

## 我的消息页面

![mark](http://myphoto.mtianyan.cn/blog/180114/B4HKiBfla1.png?imageslim)

### 配置url和view

```
    # 我收藏的课程
    path('my_message/', MyMessageView.as_view(), name="my_message"),
```

```
# 我的消息
class MyMessageView(LoginRequiredMixin, View):
    login_url = '/login/'
    redirect_field_name = 'next'

    def get(self, request):
        all_message = UserMessage.objects.filter(user= request.user.id)
        # 对课程机构进行分页
        # 尝试获取前台get请求传递过来的page参数
        # 如果是不合法的配置参数默认返回第一页
        try:
            page = request.GET.get('page', 1)
        except PageNotAnInteger:
            page = 1
        # 这里指从allorg中取五个出来，每页显示5个
        p = Paginator(all_message, 4)
        messages = p.page(page)
        return  render(request, "usercenter-message.html", {
        "messages":messages,
        })
```

### 注册时发生欢迎消息

```
 # 写入欢迎注册消息
            user_message = UserMessage()
            user_message.user = user_profile.id
            user_message.message = "欢迎注册mtianyan慕课小站!!"
            user_message.save()
```

### 页面顶部小喇叭

所有页面都要读取一个共同的变量：未读消息的数量。我们需要向request中注入这个变量
所有页面都有request.user对象。所以我们在userprofile中自定义方法，

```
    # 获取用户未读消息的数量
    def unread_nums(self):
        from operation.models import UserMessage
        return  UserMessage.objects.filter(user=self.id).count()
```

{% cq %} 泰山不让土壤，故能成其大；河海不择细流，故能就其深。 {% endcq %}

{% note success %}  
细节决定成败，大体的网站已经做好了。
佛曰：给我把细节再搞一搞

{% endnote %}

# 首页,全局功能细节和404以及500页面配置

## 登出和点击数以及收藏数完善

### 退出登录

Python3+django2.0.1下

```
class LogoutView(View):
    def get(self, request):
        # django自带的logout
        logout(request)
        # 重定向到首页,
        return HttpResponseRedirect(reverse("index"))
```


```
    # 退出功能url
    path('logout/', LogoutView.as_view(), name="logout"),
```

### 点击数加1

CourseInfoView学习人数加1

```
        course.students += 1
        course.save()
```

![mark](http://myphoto.mtianyan.cn/blog/180115/kDd20GdFDb.png?imageslim)

TeacherDetailView：

```
        teacher.click_nums +=1
        teacher.save()
```

OrgHomeView

```
course_org.click_nums +=1
        course_org.save()
```

收藏数统计

```
            exist_records.delete()
            if int(type) == 1:
                course = Course.objects.get(id=int(id))
                course.fav_nums -=1
                if course.fav_nums < 0:
                    course.fav_nums = 0
                course.save()
            elif int(type) == 2:
                org = CourseOrg.objects.get(id=int(id))
                org.fav_nums -= 1
                if org.fav_nums < 0:
                    org.fav_nums = 0
                org.save()
            elif int(type) == 3:
                teacher = Teacher.objects.get(id=int(id))
                teacher.fav_nums -=1
                if teacher.fav_nums < 0:
                    teacher.fav_nums = 0
                teacher.save()
```

```
 user_fav.save()

                if int(type) == 1:
                    course = Course.objects.get(id=int(id))
                    course.fav_nums += 1
                    course.save()
                elif int(type) == 2:
                    org = CourseOrg.objects.get(id=int(id))
                    org.fav_nums += 1
                    org.save()
                elif int(type) == 3:
                    teacher = Teacher.objects.get(id=int(id))
                    teacher.fav_nums += 1
                    teacher.save()
```

注意负数的处理：

修改消息已读

```
        # 用户进入个人中心消息页面，清空未读消息记录
        all_unread_messages = UserMessage.objects.filter(user=request.user.id, has_read=False)
        for unread_message in all_unread_messages:
            unread_message.has_read = True
            unread_message.save()
```

改进取出未读数字

```
        return  UserMessage.objects.filter(has_read=False, user=self.id).count()
```

## 首页功能开发

轮播图

公开课

授课机构

新建view

```python
## 首页view
class IndexView(View):
    def get(self,request):
        # 取出轮播图
        all_banner = Banner.objects.all().order_by('index')[:5]
        # 正常位课程
        courses = Course.objects.filter(is_banner=False)[:6]
        # 轮播图课程取三个
        banner_courses = Course.objects.filter(is_banner=True)[:3]
        # 课程机构
        course_orgs = CourseOrg.objects.all()[:15]
        return render(request, 'index.html', {
            "all_banner":all_banner,
            "courses":courses,
            "banner_courses":banner_courses,
            "course_orgs":course_orgs,
        })
```

为课程添加字段: `isbanner`

```python
is_banner = models.BooleanField(default=False, verbose_name=u"是否轮播")
``` 

url配置:

```python
path('', IndexView.as_view(), name=  "index")
```

![mark](http://myphoto.mtianyan.cn/blog/180115/8IDjg5e8K0.png?imageslim)

使用django自带模板标签`add`添加2

为`courseOrg`添加字段`tag`

```python
tag = models.CharField(max_length=10, default= u"国内名校",verbose_name=u"机构标签")
```

![mark](http://myphoto.mtianyan.cn/blog/180115/468aAaiajk.png?imageslim)

template内建标签被五整除

## 配置全局404和500


Mxonline3/urls.py

```python
# 全局404页面配置
handler404 = 'users.views.page_not_found'
```

users/views.py

```python
# 404对应处理view

def page_not_found(request):
    from django.shortcuts import  render_to_response
    response = render_to_response("404.html", {

    })
    # 设置response的状态码
    response.status_code = 404
    return response
```

Debug = True 404是不起作用的

```
ALLOWED_HOSTS = ['*']
```

在debug为false情况下。

我们在访问media的时候配置过用serve来取
告诉它访问media的时候去哪个路径下找

debug为True

会自动前往STATICFILES——DIRS取文件的

一旦debug改为false，django就不会代管你的静态文件，

一般静态文件通过第三方http服务器代理转发。

nignx 和 Apache都会自动代理这些静态文件

方法1：我们自己url响应我们的static

```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```

# 常见web攻击及防范

## sql注入攻击与防范


sql注入的危害

![mark](http://myphoto.mtianyan.cn/blog/180115/C2H1D6mBhg.png?imageslim)

对于用户的输入进行合法性判断。

```
class LoginUnsafeView(View):
    def get(self, request):
        return render(request, "login.html", {})
    def post(self, request):
        user_name = request.POST.get("username", "")
        pass_word = request.POST.get("password", "")

        import MySQLdb
        conn = MySQLdb.connect(host='127.0.0.1', user='root', passwd='root', db='mxonline', charset='utf8')
        cursor = conn.cursor()
        sql_select = "select * from users_userprofile where email='{0}' and password='{1}'".format(user_name, pass_word)

        result = cursor.execute(sql_select)
        for row in cursor.fetchall():
            # 查询到用户
            pass
        print 'hello'

urls.py
from users.views import LoginUnsafeView

urlpatterns = [
    url('^login/', LoginUnsafeView.as_view(), name='login'),
]
```

参数中加入sql语句拼接字符串使之为真。

使用django的orm，它已经对这些做了处理

## xss攻击

xss跨站脚本攻击(Cross Site Scripting)的危害

![mark](http://myphoto.mtianyan.cn/blog/180115/8EjD3Ik9Gj.png?imageslim)

正常流程

![mark](http://myphoto.mtianyan.cn/blog/180115/4F1KK3IaaI.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180115/cB5cDiKFdJ.png?imageslim)

当传入iPhone6时，这个字符会被显示到页面中。

![mark](http://myphoto.mtianyan.cn/blog/180115/kfLLLEGa19.png?imageslim)

将这段代码改成js代码

![mark](http://myphoto.mtianyan.cn/blog/180115/d42ef1h5HC.png?imageslim)

黑客拿到你的cookie信息。然后伪装成用户。

Xss攻击防范

![mark](http://myphoto.mtianyan.cn/blog/180115/03jDakfC5A.png?imageslim)

## crsf攻击与防护

crsf跨站请求伪造(Cross-site request forgery)的危害

![mark](http://myphoto.mtianyan.cn/blog/180115/6Ikm6edG47.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180115/043H5F0K8G.png?imageslim)

用户并没有向a请求，而是访问了b。b要求用户访问a的。
原因：用户向a的每次请求都会带上session id

图片中插入。

提交form表单必须添加crsf token

攻击网站无法生成crsf token

# xadmin的进阶开发

## static目录问题。

xadmin的static文件在自己的目录下所以我们找不到

1- url下的static路由配置注释掉
2- setting中的StaticRoot注释掉

![mark](http://myphoto.mtianyan.cn/blog/180115/blD3Cgd9jG.png?imageslim)

```
from xadmin.plugins.auth import UserAdmin

class UserProfileAdmin(UserAdmin):
	pass

xadmin.site.register(UserProfile,UserProfileAdmin)

from django.contrib.auth.models import User
xadmin.site.unregister(User)
```

点进UserProfileAdmin中可以看官方是怎么实现布局的，我们可以重载

get_form_layout

```
自定义的显示方式
```

get_user_model 获取用户: User = 

django权限赋值方式：赋给用户。没一个表的增删改查。

auth_permission 组权限

## 自定义icon

model_icon = 'fa fa-group'

xadmin/static/xadmin/vendor/font-awesome

官网下载然后替换css和font

## 默认排序
adminx中

```
    ordering = ['-click_nums']
    readonly_fields =['click_nums','fav_nums']
        exclude = ['fav_nums']
```

两个字段是冲突的。

## 下拉框搜索：

```
relfield_style = 'fk-ajax'
```

当有外键指向他，会以ajax方式加载

数据量过大时很有用

## inlines添加数据。

在一个页面直接完成章节。

```
# 课程直接添加章节
class LessonInline(object):
    model = Lesson
    extra = 0

        # 课程直接添加章节
    inlines = [LessonInline]
```

没法完成在章节中再嵌套视频
但是可以有多个inline。在添加课程时添加课程资源

## 一张表分两个model来管理

```python
class BannerCourse(Course):
    class Meta:
        verbose_name = "轮播课程"
        verbose_name_plural = verbose_name
        proxy = True

```

设置proxy = true会具有model的功能，但不会生成表

```python

# Course的admin管理器
class BannerCourseAdmin(object):
    list_display = [
        'name',
        'desc',
        'detail',
        'degree',
        'learn_times',
        'students']
    search_fields = ['name', 'desc', 'detail', 'degree', 'students']
    list_filter = [
        'name',
        'desc',
        'detail',
        'degree',
        'learn_times',
        'students']
    ordering = ['-click_nums']
    readonly_fields =['click_nums']
    exclude = ['fav_nums']
    # 课程直接添加章节
    inlines = [LessonInline,CourseResourceInline]
# 将管理器与model进行注册关联
xadmin.site.register(BannerCourse, BannerCourseAdmin)
```

admin中重载queryset方法。

```
    # 过滤列表中的数据
    def queryset(self):
        qs = super(BannerCourseAdmin, self).queryset()
        qs = qs.filter(is_banner=True)
        return qs
    # 过滤列表中的数据
    def queryset(self):
        qs = super(CourseAdmin, self).queryset()
        qs = qs.filter(is_banner=False)
        return qs
```

## xamdin其他常见功能：

### 可以在列表上快速修改内容、

```
  list_editable = [ 'degree','desc',]
```

### 自定义函数作为列

```
    def get_zj_nums(self):
        return self.lesson_set.all().count()
    get_zj_nums.short_description = "章节数"
```

### 显示自定义的html代码

```
      def go_to(self):
        from django.utils.safestring import mark_safe
        # 如果不mark safe。会对其进行转义
        return  mark_safe("<a href='http://blog.mtianyan.cn'>跳转</>")
    go_to.short_description = "跳转"

```


### xadmin的工具: refresh

xadmin/plugins/refresh.py

列表页定时刷新的工具

```
    refresh_times = [3,5]
```

### 字段联动

应用场景: 新增一门课程之后，courseorg的课程数+1

```
  def save_models(self):
        # 在保存课程的时候统计课程机构的课程数
        # 字段联动
        obj = self.new_obj
        # 新增课程还没有保存，统计的课程数少一个
        obj.save()
        # 必须确定存在。
        if obj.course_org is not None:
            # obj实际是一个course对象
            course_org = obj.course_org
            course_org.course_nums = Course.objects.filter(course_org = course_org).count()
            course_org.save()

```

不用在课程里面添加章节数。

## xadmin自行探究

- local 语言包
- migration 数据表的记录
- plugins 每一个后台页面都是一个plugin 插件机制
- static文件。js css
- template xadmin自己用到的html文件
- 对django admin的封装

### 下载源码包

添加插件使得可以识别ueditor field

记得在init中注册。

![mark](http://myphoto.mtianyan.cn/blog/180115/jIJ1A5EijI.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180115/kF99c72b0K.png?imageslim)

![mark](http://myphoto.mtianyan.cn/blog/180115/lcH1c4Bb11.png?imageslim)

关闭自动转义。

## 导入excel

1. 如何注入导入excel代码到菜单
2. 如何只在课程列表显示
3. 如何接收文件对文件进行处理


![mark](http://myphoto.mtianyan.cn/blog/180115/H92HC8eJ1D.png?imageslim)

adminx 文件中的变量覆盖插件内部变量。

只需要重载`block_top_toolbar`，就会把这个放到页面里面
默认使用bootstrap

`init`确定是否启用插件，

```
    def post(self, request, *args , **kwargs):
        if 'excel' in request.FILES:
            pass
```

adminx中重写post方法。上传文件会被放在`request.FILES`中。

中间pass步骤不管做什么事情，都要最后return父类的

```
return super(CourseAdmin, self).post(request, args, kwargs)
```

# 把项目部署上线

nginx + uwsgi(Python) Tomcat(java)

端口转发。负载均衡。
静态文件交给nginx转发。静态文件代理

```
sudo apt-get install nginx
ps aux | grep nginx
ifconfig
```

```
sudo apt-get install mysql-server
提示:输入用户名密码
ps aux | grep mysql
```

```
mysql -u root -p
showdatabases
```

修改`bind address`为`0.0.0.0` 是为了让win进行连接。真正部署尽量127.0.0.1

```
sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf

sudo service mysql restart

ifconfig
```
 
然后Navicat中连接会报错

你不用localhost(127)。使用本机ip都是不行的。

`*.*`里面是可以指定某一张表。root用户名 IP地址
通过该IP地址过来的root用户，通过密码才可以访问所有表。
'%'表示所有ip可以访问。

mysql下运行

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'tp131861' WITH GRANT OPTION;

flush privileges;
```
1. 安装pip

```
wget https://bootstrap.pypa.io/get-pip.py  --no-check-certificate
sudo python get-pip.py
```

```
pip install virtualenv
pip install virtualenvwrapper

workon

vim ~/.bashrc

export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh

source ~/.bashrc

workon mxonline2

pip freeze > requirements.txt

pip install -r requirements.txt

sudo pip install virtualenvwrapper

sudo apt-get install libmysqlclient-dev

pip install -i https://pypi.douban.com/simple pillow==3.4.1

pip install uwsgi

uwsgi --http :8000 --module MxOnline.wsgi(暂时不管报错)

python manage.py runserver

数据库设置

数据传输

```
sudo ln -s /mnt/Mxonline2/uc_nginx.conf /etc/nginx/conf.d/

```

将setting中 static路径指明。然后将staticDIRS注释掉

项目根目录创建conf文件夹。然后创建uwsgi.ini.

`uwsgi -i /mnt/Mxonline2/conf/uwsgi.ini &`
