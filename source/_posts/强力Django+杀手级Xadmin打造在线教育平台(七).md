---
title: 强力Django+杀手级Xadmin打造在线教育平台(七)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: 5678b347
date: 2018-01-12 22:09:17
---


{% cq %} 在绝望中寻找希望，人生终将辉煌 - 新东方 {% endcq %}

{% note default %} 
作为一个正经的教育网站，我们更是拥有正规的机构合作: 比如来自火星的星星优培。
- 完成授课机构的功能实现，
{% endnote %}

<!--more-->

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
