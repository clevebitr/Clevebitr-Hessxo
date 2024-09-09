---
title: 如何免费创建属于自己的博客？（step 2）
date: 2024-09-09 18:21:00
tags: Hexo
---
## 安装Hexo
在你常用的目录下新建一个文件夹，名字随意（英文）
打开vscode,打开新建的文件夹。
``` bash
npm install hexo-cli -g
```
安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
``` bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

初始化后，您的项目文件夹将如下所示：

``` bash
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```
### 文件说明:

`_config.yml`
网站的 配置 文件。 您可以在此配置大部分的参数。

`package.json`
应用程序的信息。 EJS, Stylus 和 Markdown 渲染引擎 已默认安装，您可以自由移除。 如果您想，可以稍后卸载它们。
``` json
package.json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "hexo": {
    "version": ""
  },
  "dependencies": {
    "hexo": "^7.0.0",
    "hexo-generator-archive": "^2.0.0",
    "hexo-generator-category": "^2.0.0",
    "hexo-generator-index": "^3.0.0",
    "hexo-generator-tag": "^2.0.0",
    "hexo-renderer-ejs": "^2.0.0",
    "hexo-renderer-stylus": "^3.0.0",
    "hexo-renderer-marked": "^6.0.0",
    "hexo-server": "^3.0.0",
    "hexo-theme-landscape": "^1.0.0"
  }
}
```
`scaffolds`
模版 文件夹。 当您新建文章时，Hexo 会根据 scaffold 来创建文件。

`source`
资源文件夹。 是存放用户资源的地方。 除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。 Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。

`themes`
主题 文件夹。 Hexo 会根据主题来生成静态页面。
### 配置
可根据官方配置文档设置。
{% btn regular ::Hexo配置文档::https://hexo.io/zh-cn/docs/configuration ::fa-brands fa-hexo %}

主要配置
``` 
`title`	网站标题
`subtitle`	网站副标题
`description`	网站描述
`keywords`	网站的关键词。 支持多个关键词。
`author`	您的名字
`language`	网站使用的语言。 使用 2 个字母的 ISO-639-1 代码，或 它的变体。 默认为 en。
`timezone`	网站时区。 Hexo 默认使用您电脑的时区。 请参考 时区列表 进行设置，如 America/New_York, Japan, 和 UTC 。 一般的，对于中国大陆地区可以使用 Asia/Shanghai。
```

### 指令
{% note warning fa-warning %}
建议都看一遍
{% endnote %}

{% btn regular ::Hexo指令文档::https://hexo.io/zh-cn/docs/commands ::fa-brands fa-hexo %}

## 上传到github

当你运行过
``` bash
hexo server
```
后，就可以试试看把博客中的文件推送到新建的远程仓库了

在目录下运行
``` bash
git init
```
初始化git

打开VScode中的`源代码管理选项卡`,就可以看到当前存储库的信息了。
选择当前存储库，点击右边的`...`展开选项，在弹出的菜单中选择`远程`->`添加远程存储库`,选择`从github上添加仓库`，选择新建的仓库。
或者在当前目录执行
``` bash
git remote add origin https://自己的仓库url地址
```
将当前仓库关联到github。

接下来就可以上传文件到github了。

## 使用vercel托管静态网站
打开 vercel官网。
{% btn regular ::vercel::https://vercel.com/ ::fa-brands fa-hexo %}

点击`start deploying`创建一个项目，导入git仓库选择`github`
登录github后，选择之前创建的存储库.
点击Deploy，等待部署完成即可。

部署完成后，就可以访问你的博客了。
当你以后更新文章时，只需要在本地编辑完成后上传到github,vercel就会自动编译项目并部署。

## 绑定你的域名
现在vercel.app 域名已经被各大搜索引擎屏蔽，无法被收录。
vercel.app 根域名已经被中国大陆防火长城屏蔽，中国国内无法访问，如果你的读者面向国内，不建议使用

可以绑定你购买的域名，用于国内访问。

{% btn regular ::Cloudflare::https://dash.cloudflare.com ::fa-brands fa-cloudflare %}

登录Cloudflare,绑定你购买的域名。
将你购买的域名托管至CloudFlare上。（通常在域名提供商上修改DNS等）

现在转回到Vercel

点击编译好的项目，点击右上角的`Domains`绑定你的域名。
在输入框中输入你托管至Cloudeflare的域名。根据提示到cloudflare修改DNS.

互联网上很多教程，本文不再概述。