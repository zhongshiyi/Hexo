---
title: Github+Hexo搭建个人博客详细教程
date: 2019-12-29 13:23:17
categories:
 - 软件安装与配置
top: true
cover: true
mathjax: false
tags:
 - Github
 - Hexo
 - 博客
---

# Github + Hexo 搭建个人博客详细教程

## 我的博客

本博客基于[Hexo](https://hexo.io/zh-cn/docs/)，所以我们首先需要了解一下我们搭建博客需要用到的框架。大家可以进入[Hexo](https://hexo.io/zh-cn/docs/)官网进行详细查看，因为 `Hexo` 的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。

最后，如果项目和教程对你有所帮助或者你看见了还算比较喜欢，欢迎给我的[github项目仓库](https://github.com/zhongshiyi/Hexo.git) `star`，谢谢您！

## Github创建个人仓库

登录到github,点击New repository创建新仓库，仓库名为：**用户名** + .github.io 这个用户名就是你的github账户的用户名，这是固定写法，千万不要搞错。比如我的仓库名为：

![](z1.png)

## 安装Git

为了把本地的网页文件上传到github上面去，我们需要用到分布式版本控制工具--[Git](https://git-scm.com/download/win)

若安装失败，请看其他Git安装教程。安装成功后，鼠标右键打开 `Git Bash Here`
![](02.png)

## 链接Github与本地

打开 `Git Base Here` 并依次输入：

```
git config --global user.name "你的github用户名"
git config --global user.email "你的邮箱"
```

然后生成密钥SSH key:

```
ssh-keygen -t rsa -C "你的邮箱" 
```

打开github，点击头像下面的 `settings` ，再点击`SSH and GPG keys`，新建一个SSH，名字随便。
![](03.png)

找到生成的`.ssh` 的文件夹中的`id_rsa.pub` 密钥，打开，将内容全部复制到上图的 `key` 中，并点击 `Add SSH key` 。
![](04.png)

输入`ssh git@github,com`,如果如下图显示出现你的用户名，那就成功了。
![](05.png)

## 安装Node.js

Hexo基于[Node.js](https://nodejs.org/en/download/)，选择对于你的电脑合适的Node.js进行下载。安装后，检测Node.js是否安装成功，可在 `Git Base` 中输入 `node -v`,显示如图，则表明成功。
![](06.png)

## 安装Hexo

在合适的地方新建一个文件夹，用来存放自己的博客文件。

在该目录下右键打开`Git Base Here`，打开git的控制台窗口。

输入`npm install -g hexo-cli` 安装Hexo。

安装完毕之后，输入 `hexo -v` 验证是否安装成功。

然后我们就要初始化我们的博客网页啦，输入 `hexo init` 初始化文件夹，接着输入 `npm install` 安装必备的组件。

然后我们的本地网站配置就弄好了，接着输入 `hexo g` ，生成静态网页，再输入 `hexo s` ，把网站部署到本地。
![](07.png)

用浏览器打开 http://localhost:4000 ,就可以看到我们的博客啦。
![](08.png)

按下 `Ctrl + C` 关闭本地服务器。

## 推送网站

刚才我们只能在本地预览，接下来我们就要发布网站，让我们的网站可以被其他所有人访问。首先我们要找到 **站点配置文件** ，就是在Hexo安装目录下的 `_config.yml` 文件。
![](09.png)

打开它，找到 `deploy` 并修改为：

```
deploy:
  type: git
  repository: git@github.com:zhongshiyi/zhongshiyi.github.io.git
  branch: master
```

repository 改成你自己的仓库地址，即创建的 `你的用户名.github.io` 仓库的地址，并保存。
![](10.png)

然后我们依次在 `Git Base Here` 中输入：

```
hexo clean
hexo g
hexo d
```

或则输入 `hexo g -d`，若出现 `Deploy done: git` 则部署成功,如图
![](11.png)

用浏览器输入我们的博客地址： `用户名+github.io` ，如我的博客 zhongshiyi.github.io

然后你就会发现你的博客已经上线了，能够在网络上被访问了。

参考文章：

1、 [Github+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)

2、 [超详细 Hexo+Github 博客搭建小白教程](https://godweiyang.com/2018/04/13/hexo-blog/#toc-heading-2)