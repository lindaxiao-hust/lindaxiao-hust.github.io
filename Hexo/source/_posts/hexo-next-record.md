---
title: next配置中的问题
date: 4/6/2016 3:10:37 PM 
categories: next
tags: [next]
description: 
---

### 将本地hexo站点部署到github pages

#### 在_config.yml文件中配置部署信息
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:your-github-name/your-github-name.github.io.git
  branch: master
```
#### 安装hexo-deployer-git插件
```
$ npm install hexo-deployer-git --save
```
就在这一步，我遇到了无比坑爹的事情，具体的错误忘记记录下来了，大致就是执行npm命令的时候一直报错，Google到一个类似的问题[npm-deployer-git cannot be installed](http://stackoverflow.com/questions/34037897/npm-deployer-git-cannot-be-installed)，错误如下
```
npm WARN optional Skipping failed optional dependency /chokidar/fsevents:
npm WARN notsup Not compatible with your operating system or architecture: fsevents@1.0.5
```
<!-- more -->
Google未果，因为是刚刚接触nodeJS和npm也不知道问题在哪儿，明明没有问题嘛哈哈↓
```
node -v #no problem
npm -v #no problem
path #include nodejs & npm
```
解决办法：请自行卸载重装nodeJS，切记安装[官网stable版](https://nodejs.org/en/download/)！我这儿出现问题的是"node-v5.9.1-x64"，换成"node-v4.4.2-x64"就没问题了Orz。。所以说做人啊，最重要的是开心，来老哥给你重装一个。。一个不想轻易重装的美少男在这块耗了很久很久很久。。

#### 愉快的部署到github pages
```
$ hexo d -g
```
### 在next中使用多说
在next中使用多说真的很方便啊，只需小手轻轻一动
```
# Duoshuo ShortName
duoshuo_shortname: your-duoshuo-站点名
```
但是！！！千千万万要记住在使用多说前一定要在_config.yml文件中添加你的URL信息！！！（我是一朵被拍死在沙滩上的小浪花
```
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com #切记修改成你自己的站点地址！
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
```
加入多说成功发布后，就好玩嘛，各种test，然后就发现使用多说转发后附上的网址一直都是类似 http://yoursite.com/2016/04/06/hexo-next-record/ 这样（跳转网址简直不堪入目不能忍），后来发现是URL忘改了，就随手改了下，结果。。网址死活都是yoursite.com！！！
以后请不要再跟我提起yoursite.com！！！各种Google都未果啊啊啊！！！主题配置文件也没有问题啊啊啊！！！多说后台也没有设置site的地荒啊啊啊！！！
这块又耗了很久很久很久。。想不开的我，不不不想不通的我，终于在多说讨论区水了一贴：[为什么转发的链接一直都是yoursite.com](http://dev.duoshuo.com/threads/5704ac9af8a3a8cd16299468)，结果在等答案的时候顺手右上角“添加新站点”（作为一个伪处女座，不到万不得已我是不会建一堆乱七八糟的站点的，骄傲），重新绑定next再发布，居然就好了啊好了啊好了啊哗擦！！！
具有自动记忆功能的你说真棒！不过现在想想会不会是浏览器缓存的问题。。