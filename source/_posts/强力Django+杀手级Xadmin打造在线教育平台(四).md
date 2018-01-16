---
title: 强力Django+杀手级Xadmin打造在线教育平台(四)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: 56d4b4c2
date: 2018-01-09 22:09:17
---

{% cq %}  数据基础决定上层建筑 {% endcq %}

{% note warning %} 设计数据库是整个项目的第一项工作:
- 完成django的app设计 & 完成app中的models设计

Django1.9.8对应github: https://github.com/mtianyan/Mxonline2
Django2.0.1对应github: https://github.com/mtianyan/Mxonline3
{% endnote %}

<!--more-->

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

