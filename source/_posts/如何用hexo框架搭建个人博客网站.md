---
title: 如何用hexo框架搭建个人博客网站
date: 2023-10-24 22:57:13
tags: [网站搭建]
index_img: /img/Hexo_index.jpg
category: 前端
comment: true
---

# Hexo使用前提
在安装hexo之前，请确保你下载了以下应用程序:
* Node.js
* Git

根据Hexo官网所述，Node.js 版本需不低于 10.13，且建议使用 Node.js 12.0 及以上版本。

至于Node.js和Git的安装，就不再此篇文章阐述了，我会在之后的文章中给出。

# 安装

Hexo的安装我们将要用到npm包管理器，然后输入以下命令

```bash
$ npm install -g hexo-cli
```

![输入后](../img/A.png)
 
然后可以进行下一步：**建站**。

# 建站 

安装完Hxo之后，执行以下命令即可生成所需要的文件。
 
```bash
$ hexo init <folder> 
$ cd <folder>
$ npm install
```
  
其中<folder>中folder用你给你博客文件夹取的名字替换。

完成后显示如下信息：

![](../img/B.png)

新建文件夹完成后目录文件如下：

```
. 
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

# 生成静态网页

执行完以上操作之后，你需要在博客的目录中输入以下指令完成静态网页的生成：

```bash
$ hexo g
```

grnerate 生成静态网页

![generate](../img/C.png)

然后使用localhost预览效果：

```bash
$ hexo s
```

![](../img/D.png)

双击 'http://localhost:4000/' 末尾的斜杆选中地址，右键open打开，效果如下：
![网站效果](../img/E.png)

记得使用完之后按下ctrl+C来关闭。

完成了这几步，那么恭喜你，你已经可以开始部署网站了。

# 网站的部署

首先，如果你下载了WebStorm，在其中打开刚刚创建的文件夹，然后创建Git仓库：

![](../img/F.png)

在你连接了远程仓库的情况下点击提交，勾选所有未进行版本管理的文件，输入提交信息后点击提交并推送，然后显示有警告需要经行代码分析，直接提交就是。

到这一步其实差不多就已经完成了，然后你可以用4everland来部署网站，别问为什么不用vercel，问就是加载太慢，以下是两者对比：

* 4everland：加载快，免费，但是部署有点慢，他是支持自动部署的。
* vercel：加载奇慢，有时候甚至完全打不开(毕竟节点在国外)，但是部署速度还算快，也能制动部署。
* 其他的还有cloudflare，这个好像速度也还行，但是我好像不怎么会用，所以感觉使用起来不如4everland。

那么以下我就只展示如何使用4everland来部署你的博客网站。

## 注册/登录/连接

首先进入4everland官网完成基本的注册登录，此处略去这些操作，在你登陆后，连接你的Github账号

![](../img/G.png)

## 部署

单击new project
![](../img/H.png)

在**Import Git Respository**下选择你博客文件的仓库，然后在**Build Configuration**下的Framework Preset选择Hexo，Build Command填写hexo generate，最后直接点击Deploy等待部署完成即可，部署完成后他会给出网址，点进去就能看到你的博客网站了。

## 域名修改

如果你有自己的域名，你可以在左侧**Hosting**下找到Project，单击后显示你的博客项目，点击设置，找到顶部的Domains，输入你的域名即可。

输入完后，你需要在域名解析中添加cname记录，将记录值填写为他给你的Value，name为你的域名的前半部分输入完后，你需要在域名解析中添加CNAME记录，将记录值填写为他给你的Value，name为你的域名的前半部分（例如，如果你的域名是"www.example.com"，那么填写的值应为'www'）。

# 第二种部署方式(服务器部署+定时更新)