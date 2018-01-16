---
title: 强力Django+杀手级Xadmin打造在线教育平台(三)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: ac975bcd
date: 2018-01-08 22:09:17
---

{% cq %}  小项目不扫何以扫天下 {% endcq %}

{% note success %}  
使用Django+Xadmin打造在线教育平台
- 第三章：通过留言板功能回顾django基础知识
通过做一个小留言板，学习django基础知识
教程仓库地址1: https://github.com/mtianyan/DjangoGetStarted

{% endnote %}

<!--more-->


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














