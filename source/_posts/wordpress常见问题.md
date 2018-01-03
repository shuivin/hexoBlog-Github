---
title: wordpress常见问题
date: 2016-04-09 23:40:15
tags: 
- WordPress

copyright: true
---
{% cq %} 
在使用wordpress过程中遇到的一些问题及解决方案。
{% endcq %}
{% note primary %} 包括ftp传输服务器错误，Warning: scandir() has been disabled for security reasons in，后台ftp麻烦的手续关闭。
 {% endnote %}
<!--more-->
## 后台ftp传输连接服务器失败。

>解决方案：
按照lnmp教程中安装pureftp设置好自己的ftp用户名
## Warning: scandir() has been disabled for security reasons in
该方案同样可以解决wordpress后台一直重复提示更新翻译

>解决方案：
编辑网站目录`/usr/local/php/etc/php.ini`目录下`php.ini`
`disable_functions =scandir,passthru,exec,system,chroot,chgrp,chown,shell_exec,proc_open,proc_get_status,ini_alter,ini_alter,ini_restore,dl,pfsockopen,openlog,syslog,readlink,symlink,popepassthru,stream_socket_server,fsocket,fsockopen`
去掉其中`scandir`保存后
通过putty下执行/etc/init.d/php-fpm restart重启服务,解决。

## 后台ftp麻烦的手续关闭。

>解决方案：
putty下执行`chown -R www  /home/wwwroot/www.mtianyan.cn`(后面地址视个人wordpress安装目录而定)
 