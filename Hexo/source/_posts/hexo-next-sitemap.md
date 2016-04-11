---
title: next添加sitemap
date: 4/6/2016 8:45:13 PM 
categories: next
tags: [next]
description: 
---

#### 执行命令安装sitemap
```
npm install hexo-generator-sitemap --save
```
#### 在Hexo站点配置文件_config.yml中加入sitemap插件
```
# Extensions
plugins: hexo-generator-sitemap
```
#### 执行命令生成sitemap文件
```
hexo clean
hexo g
```
以上操作顺利无误的话，我们可以在Hexo站点的**public**文件夹中找到**sitemap.xml**文件，可以通过 http://yoursite.com/sitemap.xml 的方式访问进行查看，如果无法生成sitemap.xml，可能是因为执行安装命令的时候没有加`--save`，详见：[Hexo搭建GitHub博客（三）- NexT主题配置使用](http://zhiho.github.io/2015/09/29/hexo-next/) #sitemap插件（这篇文章内容很详细

<!-- more -->

#### 提交sitemap到Google
这块在[官方文档](http://theme-next.iissnan.com/third-party-services.html#google-webmaster-tools)里面有提到（官方文档其实很容易上手，跟着官方走还是很容易的，有些地方可能不够详细，但是网上关于next的配置博客也不少，如[｜Hexo优化｜如何向google提交sitemap（详细）](http://fionat.github.io/blog/2013/10/23/sitemap/)），这里给出傻瓜式详细步骤：
1. 进入[Google Webmaster Central](https://www.google.com/webmasters/verification/home?hl=en)
2. 点击骚红色的"ADD A PROPERTY"
3. 在弹出来的小框中加入你的站点地址 http://yoursite.com ，然后点击"Continue"
4. Tab栏选择"Alternate methods"，选中HTML tag可以看见
```
<meta name="google-site-verification" content="xxxxxxxxxxxxxxxxxx" /> #复制content的值
```
5. 打开next主题的配置文件_config.yml，找到google_site_verification字段（找不到就新建）：
```
# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
google_site_verification: xxxxxxxxxxxxxxxxxx #4中content的值
```
6. 执行命令重新发布站点
```
hexo d -g
```
7. 回到4中的Google Webmaster Central页面，点击骚红色的"VERIFY"，done！

#### 提交sitemap到百度
[Hexo搭建GitHub博客（三）- NexT主题配置使用](http://zhiho.github.io/2015/09/29/hexo-next/) #baidusitemap安装配置 中也已经提到了，“普通的Sitemap格式不符合百度的要求”，所以我们需要对度娘特殊处理：
##### 执行命令安装百度sitemap
```
npm install hexo-generator-baidu-sitemap --save
```
##### 站点配置文件中加入百度sitemap插件
```
# Extensions
plugins: hexo-generator-baidu-sitemap
```
##### 执行命令生成百度sitemap文件
```
hexo clean
hexo g
```
与Google一样，以上操作顺利无误的话，我们可以在Hexo站点的**public**文件夹中找到**baidusitemap.xml**文件
##### 提交sitemap到百度
这部分与Google的处理方式类似：
1. 进入[百度链接提交通道](http://www.sousuoyinqingtijiao.com/baidu/tijiao/)，点击[验证网站所有权](http://zhanzhang.baidu.com/site/siteadd)（或者直接进入）
2. 输入你的站点地址http://yoursite.com ，然后点击“下一步”
3. 选中“HTML标签验证”可以看见
```
<meta name="baidu-site-verification" content="xxxxxxxx" />
```
4. 与Google不同的是，我们并不能通过在_config.yml中新建baidu_site_verification字段的方式进行验证（我试过好像不行），所以我们直接在Hexo站点的**public**文件夹中找到**index.html**文件，并在其中加上3中的验证标签
5. 执行命令重新发布站点
```
hexo d -g
```
6. 回到3中的百度验证网站页面，点击“完成验证”，done！