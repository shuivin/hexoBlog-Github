---
title: 强力Django+杀手级Xadmin打造在线教育平台(五)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: 507fe3bf
date: 2018-01-10 22:09:17
---

{% cq %} 总之，我们要拿来。我们要或使用，或存放，或毁灭。 - 鲁迅 {% endcq %}

{% note  %} 既然有django提供的强大admin,我们便要拿来用喽。
- 使用xadmin，通过adminx,将已有model注册进后台。快速搭建可用的后台系统。
{% endnote %}

<!--more-->

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