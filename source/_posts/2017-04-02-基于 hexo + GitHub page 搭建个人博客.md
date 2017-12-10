---
title: 基于 hexo + github page 搭建个人博客
date: 2017年4月2日
tags: hexo blog
toc: true
---


本文介绍了如何利用 hexo + github page 的形式搭建个人博客，步骤详细，一步成功。

<!--more-->

## 准备工具

- 操作系统: Mac OS 10.12, Sierra.
- Node.js: 用来生成静态页面.
- Git: 将本地的 Hexo 内容部署到 github.
- Hexo: 一个快速、简洁且高效的博客框架.


### 安装 Node.js

点击[下载][1]安装

如何[升级][2] Node 和 npm ？

升级 Node
``` bash
安装命令行指令 n
$ npm install -g n

安装最新版本
$ n stable
安装某一版本(v6.2.0)：
$ n v6.2.0
```

升级 npm
``` bash
$ npm -g install npm@next
```

### 安装 Git

点击[下载][3]安装

### 安装 Hexo

具体安装步骤可以参考[官方文档][4]，总结为：

``` bash
$ npm install -g hexo-cli
```

 在运行上面命令之前，需确保 Mac 上已经安装有 Xcode，并且已经安装其配套的 `Command Line Tools` 命令行工具，否则可能在编译时会遇到问题。

### 测试安装

```bash
$ hexo -v

若显示如下说明安装成功
hexo-cli: 1.0.2
os: Darwin 16.5.0 darwin x64
http_parser: 2.7.0
node: 6.10.1
v8: 5.1.281.95
uv: 1.9.1
zlib: 1.2.8
ares: 1.10.1-DEV
icu: 58.2
modules: 48
openssl: 1.0.2k
```

## 创建个人博客

在本地创建目录，这将是我们博客系统在本地硬盘的存放空间。

```bash
$ mkdir ~/Document/myblog
```

进入目录，进行初始化：

```bash
$ cd ~/Document/myblog
$ hexo init   # 这样就生成了一个默认的博客系统
```

编译生成静态文件：

```bash
$ hexo generate
```

本地预览效果

```bash
$ hexo serve
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
# 在浏览器中打开链接，即可查看效果
```

发布到 Github Page

- 在自己的 Github 上创建一个 repository，注意名字必须是`Shiwei-Wu/Shiwei-Wu.github.io`；

- 配置hexo 配置文件(\_config.yml)，在最后面添加刚刚新建的 repository，例如：

```YAML
deploy:
    type: git
    repository: https://github.com/Shiwei-Wu/Shiwei-Wu.github.io.git
    branch: master
```

- 最后使用 `hexo deploy` 命令提交并发布到外网[^1]

```bash
$ hexo deploy
```

发布后，别人怎么访问你的博客呢？很简单，浏览器访问`<your_account_name>.github.io `即可

--------------------------------------------------------------------------------

以上，就搭建好了个人博客框架；之后要进行更新，总共要经历以下几个步骤：

```bash
$ hexo new "post name"                     # 新建文章
$ hexo new page "page name"                # 新建页面
$ hexo clean                               # 清除 cache
$ hexo generate                            # 生成静态页面至 public 目录
$ hexo server                              # 开启预览访问端口，可以跳过
$ hexo deploy                              # 更新到 Github
```

[^1]:	在 hexo 3.0 版本后，deploy git 被分开，需要安装，安装命令如下：npm install hexo-deploy-git —save

[1]:	https://nodejs.org/en/
[2]:    https://segmentfault.com/a/1190000009025883
[3]:	https://git-scm.com/download/
[4]:	https://hexo.io/zh-cn/docs/index.html