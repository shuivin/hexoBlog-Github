---
title: Scrapy分布式爬虫打造搜索引擎- (五)爬虫与反爬虫的战争
date: 2017-07-02 13:36:48
tags: 
- 爬虫
- scrapy
top: 14
categories: Scrapy分布式爬虫打造搜索引擎
copyright: true
---
{% cq %}  五、爬虫与反爬虫{% endcq %}
{% note warning %} 介绍反爬虫的基本知识，随机更换useagent，fake UseAgent代理池，西刺代理创建ip代理池，云打码实现验证码的识别等。 {% endnote %}

<!--more-->

### 1. 基础知识
如何使我们的爬虫不被禁止掉

爬虫：
>自动获取数据的程序，关键是批量的获取

反爬虫：
>使用技术手段防止爬虫程序的方法

误伤：
>反爬虫技术将普通用户识别为爬虫，效果再好也不能用

学校，网吧，出口的公网ip只有一个，所以禁止ip不能用。

ip动态分配。a爬封b

成本：
>反爬虫人力和机器成本

拦截：
>拦截率越高，误伤率越高

反爬虫的目的：

![反爬虫的目的](http://upload-images.jianshu.io/upload_images/1779926-d48e923ecb3d20ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

爬虫与反爬虫的对抗过程：

![爬虫与反爬虫斗争](http://upload-images.jianshu.io/upload_images/1779926-77314219c9f1757e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用检查可以查看到价格，而查看网页源代码无法查看到价格字段。
scrapy下载到的网页时网页源代码。
js（ajax）填充的动态数据无法通过网页获取到。

### 2. scrapy架构及源码介绍

![scrapy组件分析图](http://upload-images.jianshu.io/upload_images/1779926-8381473a93549bc0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![scrapy官方架构图](http://upload-images.jianshu.io/upload_images/1779926-8f93d40d66c9fe04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1. 我们编写的spider，然后yield一个request发送给engine
2. engine拿到什么都不做然后给scheduler
3. engine会生成一个request给engine
4. engine拿到之后通过downloadermiddleware 给downloader
5. downloader再发送response回来给engine。
6. engine拿到之后，response给spider。
7. spider进行处理，解析出item & request，
8. item->给itempipeline；如果是request，跳转步骤二

path：articlespider3\Lib\site-packages\scrapy\core

- engine.py：
- scheduler.py
- downloader

- item
- pipeline
- spider

**engine.py：重要函数schedule**

1. enqueue_request：把request放scheduler
2. `_next_request_from_scheduler`:从调度器拿。

```python
    def schedule(self, request, spider):
        self.signals.send_catch_log(signal=signals.request_scheduled,
                request=request, spider=spider)
        if not self.slot.scheduler.enqueue_request(request):
            self.signals.send_catch_log(signal=signals.request_dropped,
                                        request=request, spider=spider)
```

articlespider3\Lib\site-packages\scrapy\core\downloader\handlers
>支持文件，ftp，http下载(https).

后期定制middleware：

- spidermiddlewire
- downloadmiddlewire

django和scrapy结构类似


### 3. scrapy的两个重要类：request和response
类似于django httprequest

```python
yield Request(url=parse.urljoin(response.url, post_url))
```
request参数：

```python
class Request(object_ref):

    def __init__(self, url, callback=None, method='GET', headers=None, body=None,
                 cookies=None, meta=None, encoding='utf-8', priority=0,
                 dont_filter=False, errback=None):
```

cookies：
Lib\site-packages\scrapy\downloadermiddlewares\cookies.py

```python
cookiejarkey = request.meta.get("cookiejar")
```

- priority: 优先级，影响调度顺序
- dont_filter：我的同样的request不会被过滤
- errback：错误时的回调函数

https://doc.scrapy.org/en/1.2/topics/request-response.html?highlight=response

**errback example：**

```python
class ErrbackSpider(scrapy.Spider):
    name = "errback_example"
    start_urls = [
        "http://www.httpbin.org/",              # HTTP 200 expected
        "http://www.httpbin.org/status/404",    # Not found error
        "http://www.httpbin.org/status/500",    # server issue
        "http://www.httpbin.org:12345/",        # non-responding host, timeout expected
        "http://www.httphttpbinbin.org/",       # DNS error expected
    ]

    def start_requests(self):
        for u in self.start_urls:
            yield scrapy.Request(u, callback=self.parse_httpbin,
                                    errback=self.errback_httpbin,
                                    dont_filter=True)

    def parse_httpbin(self, response):
        self.logger.info('Got successful response from {}'.format(response.url))
        # do something useful here...

    def errback_httpbin(self, failure):
        # log all failures
        self.logger.error(repr(failure))

        # in case you want to do something special for some errors,
        # you may need the failure's type:

        if failure.check(HttpError):
            # these exceptions come from HttpError spider middleware
            # you can get the non-200 response
            response = failure.value.response
            self.logger.error('HttpError on %s', response.url)

        elif failure.check(DNSLookupError):
            # this is the original request
            request = failure.request
            self.logger.error('DNSLookupError on %s', request.url)

        elif failure.check(TimeoutError, TCPTimedOutError):
            request = failure.request
            self.logger.error('TimeoutError on %s', request.url)
```

**response类**

```python
 def __init__(self, url, status=200, headers=None, body=b'', flags=None, request=None):
        self.headers = Headers(headers or {})
```

**response的参数：**
request：yield出来的request，会放在response，让我们知道它是从哪里来的

### 4. 自行编写随机更换useagent

1. setting中设置

```python
user_agent_list = [
    'Mozilla/5.0 (Windows NT 6.1; WOW64; rv:51.0) Gecko/20100101 Firefox/51.0',
    'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.104 Safari/537.36',
]
```

然后在代码中使用。

```python
	from settings import user_agent_list
    import random
    random_index =random.randint(0,len(user_agent_list))
    random_agent = user_agent_list[random_index]

    'User-Agent': random_agent
```

```python
                import random
                random_index = random.randint(0, len(user_agent_list))
                random_agent = user_agent_list[random_index]
                self.headers["User-Agent"] = random_agent
                yield scrapy.Request(request_url, headers=self.headers, callback=self.parse_question)
```

但是问题：每个request之前都得这样做。

### 5. middlewire配置及编写fake UseAgent代理池
取消DOWNLOADER_MIDDLEWARES的注释状态

```python
DOWNLOADER_MIDDLEWARES = {
   'ArticleSpider.middlewares.MyCustomDownloaderMiddleware': 543,
}
```
articlespider3\Lib\site-packages\scrapy\downloadermiddlewares\useragent.py

```python
class UserAgentMiddleware(object):
    """This middleware allows spiders to override the user_agent"""

    def __init__(self, user_agent='Scrapy'):
        self.user_agent = user_agent

    @classmethod
    def from_crawler(cls, crawler):
        o = cls(crawler.settings['USER_AGENT'])
        crawler.signals.connect(o.spider_opened, signal=signals.spider_opened)
        return o

    def spider_opened(self, spider):
        self.user_agent = getattr(spider, 'user_agent', self.user_agent)

    def process_request(self, request, spider):
        if self.user_agent:
            request.headers.setdefault(b'User-Agent', self.user_agent)
```

重要方法process_request

**配置默认useagent为none**

```python
DOWNLOADER_MIDDLEWARES = {
   'ArticleSpider.middlewares.MyCustomDownloaderMiddleware': 543,
    'scrapy.downloadermiddlewares.useragent.UserAgentMiddleware': None
}
```

**使用fakeuseragent**
`pip install fake-useragent`

setting.py设置随机模式`RANDOM_UA_TYPE = "random"`

```python
from fake_useragent import UserAgent

class RandomUserAgentMiddlware(object):
    #随机更换user-agent
    def __init__(self, crawler):
        super(RandomUserAgentMiddlware, self).__init__()
        self.ua = UserAgent()
        self.ua_type = crawler.settings.get("RANDOM_UA_TYPE", "random")

    @classmethod
    def from_crawler(cls, crawler):
        return cls(crawler)

    def process_request(self, request, spider):
        def get_ua():
            return getattr(self.ua, self.ua_type)

        request.headers.setdefault('User-Agent', get_ua())
```

### 6. 使用西刺代理创建ip代理池保存到数据库*

ip动态变化：重启路由器等

ip代理的原理：

不直接发送自己真实ip，而使用中间代理商（代理服务器），那么服务器不知道我们的ip也就不会把我们禁掉
setting.py设置

```python
class RandomProxyMiddleware(object):
    #动态设置ip代理
    def process_request(self, request, spider):
        request.meta["proxy"] = "http://111.198.219.151:8118"
```

**使用西刺代理创建代理池保存到数据库**

```python
# _*_ coding: utf-8 _*_
__author__ = 'mtianyan'
__date__ = '2017/5/24 16:27'
import requests
from scrapy.selector import Selector
import MySQLdb

conn = MySQLdb.connect(host="127.0.0.1", user="root", passwd="ty158917", db="article_spider", charset="utf8")
cursor = conn.cursor()


def crawl_ips():
    #爬取西刺的免费ip代理
    headers = {"User-Agent":"Mozilla/5.0 (Windows NT 6.1; WOW64; rv:52.0) Gecko/20100101 Firefox/52.0"}
    for i in range(1568):
        re = requests.get("http://www.xicidaili.com/nn/{0}".format(i), headers=headers)

        selector = Selector(text=re.text)
        all_trs = selector.css("#ip_list tr")


        ip_list = []
        for tr in all_trs[1:]:
            speed_str = tr.css(".bar::attr(title)").extract()[0]
            if speed_str:
                speed = float(speed_str.split("秒")[0])
            all_texts = tr.css("td::text").extract()

            ip = all_texts[0]
            port = all_texts[1]
            proxy_type = all_texts[5]

            ip_list.append((ip, port, proxy_type, speed))

        for ip_info in ip_list:
            cursor.execute(
                "insert proxy_ip(ip, port, speed, proxy_type) VALUES('{0}', '{1}', {2}, 'HTTP')".format(
                    ip_info[0], ip_info[1], ip_info[3]
                )
            )

            conn.commit()


class GetIP(object):
    def delete_ip(self, ip):
        #从数据库中删除无效的ip
        delete_sql = """
            delete from proxy_ip where ip='{0}'
        """.format(ip)
        cursor.execute(delete_sql)
        conn.commit()
        return True

    def judge_ip(self, ip, port):
        #判断ip是否可用
        http_url = "http://www.baidu.com"
        proxy_url = "http://{0}:{1}".format(ip, port)
        try:
            proxy_dict = {
                "http":proxy_url,
            }
            response = requests.get(http_url, proxies=proxy_dict)
        except Exception as e:
            print ("invalid ip and port")
            self.delete_ip(ip)
            return False
        else:
            code = response.status_code
            if code >= 200 and code < 300:
                print ("effective ip")
                return True
            else:
                print  ("invalid ip and port")
                self.delete_ip(ip)
                return False


    def get_random_ip(self):
        #从数据库中随机获取一个可用的ip
        random_sql = """
              SELECT ip, port FROM proxy_ip
            ORDER BY RAND()
            LIMIT 1
            """
        result = cursor.execute(random_sql)
        for ip_info in cursor.fetchall():
            ip = ip_info[0]
            port = ip_info[1]

            judge_re = self.judge_ip(ip, port)
            if judge_re:
                return "http://{0}:{1}".format(ip, port)
            else:
                return self.get_random_ip()



# print (crawl_ips())
if __name__ == "__main__":
    get_ip = GetIP()
    get_ip.get_random_ip()
```
**使用scrapy_proxies创建ip代理池**

`pip install scrapy_proxies`

收费，但是简单
https://github.com/scrapy-plugins/scrapy-crawlera

tor隐藏。vpn
http://www.theonionrouter.com/

### 7. 通过云打码实现验证码的识别

http://www.yundama.com/

```python
# _*_ coding: utf-8 _*_
__author__ = 'mtianyan'
__date__ = '2017/6/24 16:48'

import json
import requests

class YDMHttp(object):
    apiurl = 'http://api.yundama.com/api.php'
    username = ''
    password = ''
    appid = ''
    appkey = ''

    def __init__(self, username, password, appid, appkey):
        self.username = username
        self.password = password
        self.appid = str(appid)
        self.appkey = appkey

    def balance(self):
        data = {'method': 'balance', 'username': self.username, 'password': self.password, 'appid': self.appid, 'appkey': self.appkey}
        response_data = requests.post(self.apiurl, data=data)
        ret_data = json.loads(response_data.text)
        if ret_data["ret"] == 0:
            print ("获取剩余积分", ret_data["balance"])
            return ret_data["balance"]
        else:
            return None

    def login(self):
        data = {'method': 'login', 'username': self.username, 'password': self.password, 'appid': self.appid, 'appkey': self.appkey}
        response_data = requests.post(self.apiurl, data=data)
        ret_data = json.loads(response_data.text)
        if ret_data["ret"] == 0:
            print ("登录成功", ret_data["uid"])
            return ret_data["uid"]
        else:
            return None

    def decode(self, filename, codetype, timeout):
        data = {'method': 'upload', 'username': self.username, 'password': self.password, 'appid': self.appid, 'appkey': self.appkey, 'codetype': str(codetype), 'timeout': str(timeout)}
        files = {'file': open(filename, 'rb')}
        response_data = requests.post(self.apiurl, files=files, data=data)
        ret_data = json.loads(response_data.text)
        if ret_data["ret"] == 0:
            print ("识别成功", ret_data["text"])
            return ret_data["text"]
        else:
            return None

def ydm(file_path):
    username = ''
    # 密码
    password = ''
    # 软件ＩＤ，开发者分成必要参数。登录开发者后台【我的软件】获得！
    appid = 
    # 软件密钥，开发者分成必要参数。登录开发者后台【我的软件】获得！
    appkey = ''
    # 图片文件
    filename = 'image/1.jpg'
    # 验证码类型，# 例：1004表示4位字母数字，不同类型收费不同。请准确填写，否则影响识别率。在此查询所有类型 http://www.yundama.com/price.html
    codetype = 5000
    # 超时时间，秒
    timeout = 60
    # 检查

    yundama = YDMHttp(username, password, appid, appkey)
    if (username == 'username'):
        print('请设置好相关参数再测试')
    else:
        # 开始识别，图片路径，验证码类型ID，超时时间（秒），识别结果
        return yundama.decode(file_path, codetype, timeout);

if __name__ == "__main__":
    # 用户名
    username = ''
    # 密码
    password = ''
    # 软件ＩＤ，开发者分成必要参数。登录开发者后台【我的软件】获得！
    appid = 
    # 软件密钥，开发者分成必要参数。登录开发者后台【我的软件】获得！
    appkey = ''
    # 图片文件
    filename = 'image/captcha.jpg'
    # 验证码类型，# 例：1004表示4位字母数字，不同类型收费不同。请准确填写，否则影响识别率。在此查询所有类型 http://www.yundama.com/price.html
    codetype = 5000
    # 超时时间，秒
    timeout = 60
    # 检查
    if (username == 'username'):
        print ('请设置好相关参数再测试')
    else:
        # 初始化
        yundama = YDMHttp(username, password, appid, appkey)

        # 登陆云打码
        uid = yundama.login();
        print('uid: %s' % uid)

        # 登陆云打码
        uid = yundama.login();
        print ('uid: %s' % uid)

        # 查询余额
        balance = yundama.balance();
        print ('balance: %s' % balance)

        # 开始识别，图片路径，验证码类型ID，超时时间（秒），识别结果
        text = yundama.decode(filename, codetype, timeout);


```

### 8. cookie的禁用。& 设置下载速度

http://scrapy-chs.readthedocs.io/zh_CN/latest/topics/autothrottle.html

setting.py:

```python
# Disable cookies (enabled by default)
COOKIES_ENABLED = False
```

设置下载速度：

```python
# The initial download delay
#AUTOTHROTTLE_START_DELAY = 5
```

给不同的spider设置自己的setting值

```python
    custom_settings = {
        "COOKIES_ENABLED": True
    }
```


