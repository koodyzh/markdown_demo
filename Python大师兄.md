## Python大神自创完整版，系统性学习Python

![从0到就业](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yMDA2MjQwOC1kY2Q2YTNkZTgxZGFkYzI4LmpwZw?x-oss-process=image/format,png)

给初学者的几个建议：

- Make English as your working language.

- Practice makes perfect.

- All experience comes from mistakes.

- Don’t be one of the leeches.

- Either stand out or kicked out.

[Python 大师兄](https://blog.csdn.net/ITHHH777/article/details/104267002)

## 教你如何编写第一个简单的爬虫

1. 第1步 获取页面

```python
#!/usr/bin/python
# coding: utf-8

import requests #引入包requests
link = "http://www.santostang.com/" #定义link为目标网页地址
# 定义请求头的浏览器代理，伪装成浏览器
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'} 

r = requests.get(link, headers= headers) #请求网页
print (r.text)  #r.text是获取的网页内容代码

```

2. 第2步 提取需要的数据

```python
#!/usr/bin/python
# coding: utf-8

import requests
from bs4 import BeautifulSoup     #从bs4这个库中导入BeautifulSoup

link = "http://www.santostang.com/"
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'} 
r = requests.get(link, headers= headers)

soup = BeautifulSoup(r.text, "html.parser") #使用BeautifulSoup解析

#找到第一篇文章标题，定位到class是"post-title"的h1元素，提取a，提取a里面的字符串，strip()去除左右空格
title = soup.find("h1", class_="post-title").a.text.strip()
print (title)

```

3. 第3步 存储数据

```
import requests
from bs4 import BeautifulSoup   #从bs4这个库中导入BeautifulSoup

link = "http://www.santostang.com/"
headers = {'User-Agent' : 'Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.6) Gecko/20091201 Firefox/3.5.6'} 
r = requests.get(link, headers= headers)

soup = BeautifulSoup(r.text, "html.parser") #使用BeautifulSoup解析
title = soup.find("h1", class_="post-title").a.text.strip()
print (title)

# 打开一个空白的txt，然后使用f.write写入刚刚的字符串title
with open('title_test.txt', "a+") as f:
    f.write(title)

```

[简单的爬虫编程实例](https://blog.csdn.net/weixin_37649168/article/details/104265388)

想要学更多爬虫相关的内容，可以查寻《Python网络爬虫从入门到实践（第2版）》

![Python 网络爬虫](https://img-blog.csdnimg.cn/20200211165212664.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zNzY0OTE2OA==,size_16,color_FFFFFF,t_70#pic_center)
