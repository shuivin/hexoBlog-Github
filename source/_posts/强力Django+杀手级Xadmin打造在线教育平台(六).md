---
title: 强力Django+杀手级Xadmin打造在线教育平台(六)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: c970abcd
date: 2018-01-11 22:09:17
---

{% cq %} 矛盾的普遍性是指矛盾存在于一切事物的发展过程之中，矛盾存在于一切事物发展过程的始终。 {% endcq %}

{% note  %} 我想只要是个系统，就少不了登录注册。这是我们需要首先处理的主要矛盾。
- 完成登录 注册 找回密码 激活 验证码集成
{% endnote %}

<!--more-->

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





