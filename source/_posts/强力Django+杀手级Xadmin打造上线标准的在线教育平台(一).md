---
title: 强力Django+杀手级Xadmin打造在线教育平台(一)
tags:
  - Python
  - Django
  - 在线教育平台
categories: python从入门到精通
copyright: true
abbrlink: e4b77eed
date: 2018-01-07 03:08:18
---

{% cq %}  请开始你的表演是做一个项目的第一步{% endcq %}

{% note  %}  
使用Django+Xadmin打造在线教育平台
- 第一章：项目介绍和课程介绍

教程仓库地址1:https://github.com/mtianyan/DjangoGetStarted
{% endnote %}

<!--more-->
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

