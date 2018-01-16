---
title: 强力Django+杀手级Xadmin打造在线教育平台(八)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: 9f2a0c4b
date: 2018-01-13 22:09:17
---

{% cq %} 三年六班，三年六班，李子明，李子明同学，你妈妈拿了两罐旺仔牛奶给你 {% endcq %}

{% note success %}  
上帝说得有课程！ 得有详情 ！点了开始学习，得有章节！章节得有视频。
课程还得能评论下，还得有相关课程。于是这章出现了。
{% endnote %}

<!--more-->

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