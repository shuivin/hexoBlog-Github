---
title: 强力Django+杀手级Xadmin打造在线教育平台(十二)
tags:
  - Python
  - Django
  - 在线教育平台
categories: Django+Xadmin打造在线教育平台
copyright: true
abbrlink: ac88a88
date: 2018-01-16 22:09:17
---

{% cq %} 君子以思患而豫防之 {% endcq %}

{% note success %}  
安全问题还是要搞一搞的: sql注入，xss攻击，crsf攻击。
{% endnote %}

<!--more-->
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