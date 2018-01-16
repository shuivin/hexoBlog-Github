---
title: 强力Django+杀手级Xadmin打造在线教育平台(十一)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: a5f911ea
date: 2018-01-16 22:09:17
---

{% cq %} 泰山不让土壤，故能成其大；河海不择细流，故能就其深。 {% endcq %}

{% note success %}  
细节决定成败，大体的网站已经做好了。
佛曰：给我把细节再搞一搞

{% endnote %}

<!--more-->
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
