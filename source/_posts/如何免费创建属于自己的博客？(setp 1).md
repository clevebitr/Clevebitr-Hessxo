---
title: 如何免费创建属于自己的博客？（setp 1）
date: 2024-09-08 22:56:24
tags: Hexo
---
## 本教程手把手教你如何创建属于你自己的博客！
### 准备：
1. 一台电脑（windows10及以上）
2. 一个邮箱（注册账号使用）
3. 一个github账号
4. 一个Cloudflare账号

## 1.安装软件
要使用Hexo傻瓜式部署一个博客，首先，需要安装一些它依赖的软件。
1. vscode
2. nodejs
3. git

### Vscode的安装
{% note info fa-info %} 
"Visual Studio Code（简称“VS Code”）是Microsoft在2015年4月30日Build开发者大会上正式宣布一个运行于 Mac OS X、Windows和 Linux 之上的，针对于编写现代Web和云应用的跨平台源代码编辑器，可在桌面上运行，并且可用于Windows，macOS和Linux。它具有对JavaScript，TypeScript和Node.js的内置支持，并具有丰富的其他语言（例如C++，C＃，Java，Python，PHP，Go）和运行时（例如.NET和Unity）扩展的生态系统。 "
主要的是，它开源
{% endnote %}
{% btn regular ::官网::https://vscode.github.net.cn/ ::fa-solid fa-download %}
如果你是windows电脑，安装windows版本，mac就安装macos版本。

### Nodejs安装
可以在nodejs中文网安装nodejs
{% note info fa-info %} 
Node.js 建立在 Google Chrome V8 JavaScript 引擎之上，主要用于创建网络服务器 - 但不仅限于此。
Node.js 是一个开源和跨平台的 JavaScript 运行时环境。 它是几乎任何类型项目的流行工具！
{% endnote %}
{% btn regular ::在 Nodejs 中文网 下载::https://nodejs.cn/download/ ::fa-solid fa-download %}
长期支持版和最新版都可以，选择适合你系统的版本（Windows,MacOS,Liunx下载源代码自行编译）

### Git安装
{% note info fa-info %} 
Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。
Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。
Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。
{% endnote %}
根据操作系统选择下载  

{% btn regular ::Git for Windows 下载::https://git-scm.com/download/win ::fa-solid fa-download %}

{% btn regular ::Git for MacOS 下载::https://git-scm.com/download/mac ::fa-solid fa-download %}

{% btn regular ::Git for Liunx 下载::https://git-scm.com/download/linux ::fa-solid fa-download %}

保持默认，一直点击下一步就可以。

## 2.注册账号

### 注册Github账号

{% note info fa-info %} 
关于 GitHub
GitHub 是一种基于云的平台，可在其中存储、共享并与他人一起编写代码。

通过将代码存储在 GitHub 上的“存储库”中，你将可以：

“展示或共享” 你的工作。
持续“跟踪和管理” 对代码的更改。
让其他人“审查” 你的代码，并提出改进建议。
在共享的项目中开展“协作”，无需担心这些更改会在准备好集成更改之前影响协作者的工作。
协作式工作是 GitHub 最基本的功能之一，该功能由开源软件 Git 实现，而 GitHub 是以该软件为基础进行构建的。
{% endnote %}

{% btn regular ::Github::https://github.com/ ::fa-brands fa-github %}

进入github

点击右上角的`Sing up`注册账号  
- `Enter your email*` -> 输入你的邮箱  
- `Create a password*` ->创建你的密码  
- `Enter a username*` -> 输入你的用户名（英文）  
- `Email preferences` -> 验证邮箱  
完成人机验证并验证邮箱，账号就注册成功了。
注册成功后，下一步将你的git链接到github上，就可以将代码存放在github上了。

### 创建Cloudflare账号
{% note info fa-info %} 
Cloudflare 的使命是帮助构建更好的互联网。 

Cloudflare 是世界最大的网络之一。今天，企业、非营利组织、博客作者和任何有互联网存在的人都因为 Cloudflare 而拥有更快、更安全的网站和应用。 

{% btn regular ::关于 Cloudflare::https://www.cloudflare-cn.com/learning/what-is-cloudflare/ ::fa-brands fa-cloudflare %}
{% endnote %}


{% btn regular ::注册 Cloudflare::https://dash.cloudflare.com/sign-up ::fa-brands fa-cloudflare %}

填入邮箱和密码

## 3.Git 与 Github

### 创建存储库
打开github,登录账户。

点击右上角的加号
点击 `new repository` 创建新的存储库。
填入存储库名称（英文） -> `Repository name*`
点击创建。

### 配置git

设置名称与邮箱

``` git
git config --global user.name "注册名"
git config --global user.email "注册邮箱"
```

生成密钥
``` bash
ssh-keygen -t rsa -C "自己的邮箱"
```

SSH文件存放在C:/User/用户/.ssh下，id_rsa为私钥，id_rsa.pub为公钥。

### 配置ssh

打开id_rsa.pub文件，全选，复制全文

打开github
github->账户->setting

选择SSH and GPGkeys，New SSH key

自定义一个title，然后粘贴从公钥文件中拷贝的key

### 测试SSH

``` bash
ssh -T git@github.com

```
按照提示输入yes，回车，提示successfully之类的就说明SSH连接正常，github上的钥匙也会变成绿色

至此，本地git客户端和远程github建立了联系。