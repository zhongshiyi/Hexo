---
title: GitHub + Hexo 搭建个人博客详细教程
top: true
cover: true
toc: true
mathjax: false
typora-root-url: ../../source/
date: 2019-12-29 13:23:17
author:
img:
coverImg:
password:
summary:
tags:
 - GitHub
 - Hexo
 - 博客
categories:
 - 软件安装与配置
---

# GitHub + Hexo 搭建个人博客详细教程

## 我的博客

本博客基于[Hexo](https://hexo.io/zh-cn/docs/)，所以我们首先需要了解一下我们搭建博客需要用到的框架。大家可以进入[Hexo](https://hexo.io/zh-cn/docs/)官网进行详细查看，因为 `Hexo` 的创建者是台湾人，对中文的支持很友好，可以选择中文进行查看。

最后，如果项目和教程对你有所帮助或者你看见了还算比较喜欢，欢迎给我的 [github项目仓库](https://github.com/zhongshiyi/Hexo.git) `star`，谢谢您！

## GitHub 创建个人仓库

登录到 GitHub, 点击 New repository 创建新仓库，仓库名为：**用户名** + .github.io 这个用户名就是你的 GitHub 账户的用户名，这是固定写法，千万不要搞错。比如我的仓库名为：

![](/images/GitHub-Hexo-detailed-blog-tutorial/z1.png)

## 安装 Git

为了把本地的网页文件上传到 GitHub 上面去，我们需要用到分布式版本控制工具--[Git](https://git-scm.com/download/win)

若安装失败，请看其他Git安装教程。安装成功后，鼠标右键打开 `Git Bash Here`
![](/images/GitHub-Hexo-detailed-blog-tutorial/02.png)

## 连接 GitHub 与本地

打开 `Git Base Here` 并依次输入：

```shell
git config --global user.name "你的github用户名"
git config --global user.email "你的邮箱"
```

然后生成密钥 SSH key:

```shell
ssh-keygen -t rsa -C "你的邮箱" 
```

打开 GitHub，点击头像下面的 `settings` ，再点击`SSH and GPG keys`，新建一个SSH，名字随便。
![](/images/GitHub-Hexo-detailed-blog-tutorial/03.png)



找到生成的`.ssh` 的文件夹中的 `id_rsa.pub` 密钥，打开，将内容全部复制到上图的 `key` 中，并点击 `Add SSH key` 。

![](/images/GitHub-Hexo-detailed-blog-tutorial/04.png)



输入`ssh git@github,com`,如果如下图显示出现你的用户名，那就成功了。

![](/images/GitHub-Hexo-detailed-blog-tutorial/05.png)

## 安装Node.js

Hexo 基于 [Node.js](https://nodejs.org/en/download/)，选择对于你的电脑合适的 Node.js 进行下载。安装后，检测 Node.js 是否安装成功，可在 `Git Base` 中输入 `node -v`,显示如图，则表明成功。
![](/images/GitHub-Hexo-detailed-blog-tutorial/06.png)

## 安装Hexo

在合适的地方新建一个文件夹，用来存放自己的博客文件。

在该目录下右键打开 `Git Base Here`，打开git的控制台窗口。

输入 `npm install -g hexo-cli` 安装 Hexo。

安装完毕之后，输入 `hexo -v` 验证是否安装成功。

然后我们就要初始化我们的博客网页啦，输入 `hexo init` 初始化文件夹，接着输入 `npm install` 安装必备的组件。

然后我们的本地网站配置就弄好了，接着输入 `hexo g` ，生成静态网页，再输入 `hexo s` ，把网站部署到本地。
![](/images/GitHub-Hexo-detailed-blog-tutorial/07.png)

用浏览器打开 http://localhost:4000 ,就可以看到我们的博客啦。
![](/images/GitHub-Hexo-detailed-blog-tutorial/08.png)

按下 `Ctrl + C` 关闭本地服务器。

## 推送网站

刚才我们只能在本地预览，接下来我们就要发布网站，让我们的网站可以被其他所有人访问。首先我们要找到 **站点配置文件** ，就是在 Hexo 安装目录下的 `_config.yml` 文件。
![](/images/GitHub-Hexo-detailed-blog-tutorial/09.png)

打开它，找到 `deploy` 并修改为：

```yaml
deploy:
  type: git
  repository: git@github.com:zhongshiyi/zhongshiyi.github.io.git
  branch: master
```



repository 改成你自己的仓库地址，即创建的 `你的用户名.github.io` 仓库的地址，并保存。
![](/images/GitHub-Hexo-detailed-blog-tutorial/10.png)

然后我们依次在 `Git Base Here` 中输入：

```bash
hexo clean
hexo g
hexo d
```

或则输入 `hexo g -d`，若出现 `Deploy done: git` 则部署成功,如图
![](/images/GitHub-Hexo-detailed-blog-tutorial/11.png)

用浏览器输入我们的博客地址： `用户名 + github.io` ，如我的博客 zhongshiyi.github.io

然后你就会发现你的博客已经上线了，能够在网络上被访问了。

## 设置个人域名

现在你的个人网站的地址是：`yourname.github.io` ，如果觉得这个网址逼格不太够，这就需要你设置个人域名了。但是需要花钱。

> 
>
> 不过，这一步不是必要的，如果小伙伴不想现在就买域名，那就可以直接观看下一篇博客
>
> 

[GitHub Actions 自动部署 Hexo 博客教程](https://zsyle.top/2020/01/06/github-actions-auto-build-hexo-blog-tutorial/)

首先你得买一个专属域名，百度云，阿里云都能买。

这篇以阿里云为例，阿里云官方购买：

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110155656010.png)

### 阿里云 DNS 解析

然后实名认证后进入阿里云控制台，点云解析进去，找到你刚买的域名，点进去添加一条解析记录，如下图所示：

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110160536472.png)

然后打开你的`github`博客项目，点击`settings`，拉到下面`Custom domain`处，填上你自己的域名，保存：

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110163540354.png)

这时候你的项目根目录应该会出现一个名为`CNAME`的文件了。如果没有的话，打开你本地博客`/source`目录，我的是`D:\Blog\source`，新建`CNAME`文件，注意没有后缀。然后在里面写上你的域名，保存。最后运行`hexo g`、`hexo d`上传到`github`。

过不了多久，再打开你的浏览器，输入你自己的专属域名，就可以看到搭建的网站啦！

### Cloudflare DNS 解析

一名朋友告诉我，阿里云的解析速度不理想，于是他推荐了我一个 Cloudflare 网站用来 DNS 解析，这里我也给大家推荐一下吧。

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110161423343.png)

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110161631510.png)

**现在我们去阿里云的域名控制面板修改 DNS**

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110162512112.png)

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110162703384.png)

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110162837116.png)

**到这里，阿里云域名面板的设置到这里结束，下面我们回到 Cloudflare 面板，找到你的域名，点 DNS。**

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110163101183.png)

**下面添加记录基本和阿里云一样，添加一条像这样的记录：**

![](/images/GitHub-Hexo-detailed-blog-tutorial/image-20200110163350282.png)

**这里就解析配置完毕了。**

**下一篇博客介绍如何利用 GitHub Actions 工作流自动部署博客**

参考文章：

1、 [Github+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)

2、 [超详细 Hexo+Github 博客搭建小白教程](https://godweiyang.com/2018/04/13/hexo-blog/#toc-heading-2)