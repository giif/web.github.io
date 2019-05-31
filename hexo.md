---
title: hexo
date: 2019-05-18 02:33:27
tags:
---
搭建步骤
环境准备

安装 Node.js（我们要用它来安装博客框架、渲染主题等）。
安装 Git（我们要用它来下载主题、提交、部署文章等）。

安装 Hexo
以上两个必备程序安装完成后，只需要用 git-bash 执行如下命令即可安装 Hexo。
$ npm install -g hexo-cli

建站
安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹 <folder> 中新建所需要的文件。
$ hexo init <folder>
$ cd <folder>
$ npm install

新建完成后，指定文件夹 <folder> 的目录如下：
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes




文件/文件夹
作用




_config.yml
网站的配置文件


package.json
应用程序的信息


scaffolds

模版文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件


source

资源文件夹是存放用户资源的地方。除 _posts 文件夹之外，开头命名为 _ (下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去


themes

主题文件夹。Hexo 会根据主题来生成静态页面



创建主题
使用如下命令下载主题：
$ cd themes/
$ git init 
$ git clone https://github.com/iissnan/hexo-theme-next.git

你也可以下载多个主题，然后修改 _config.yml（注意是网站的配置文件而非主题的配置文件） 内的 theme 设定，即可切换主题。一个主题通常有以下结构：
.
├── _config.yml
├── languages
├── layout
├── scripts
└── source




文件/文件夹
作用




_config.yml
主题的配置文件


languages
语言文件夹，请参见国际化 (i18n)



layout
布局文件夹。用于存放主题的模板文件，决定了网站内容的呈现方式，您可参考模板以获得更多信息


scripts
脚本文件夹。在启动时，Hexo 会载入此文件夹内的 JavaScript 文件，参见插件获取更多信息


source
资源文件夹，除了模板以外的 Asset，例如 CSS、JavaScript 文件等，都应该放在这个文件夹中。文件或文件夹开头名称为 _（下划线线）或隐藏的文件会被忽略



主题配置
每个主题的配置文件 _config.yml 内容可能都不太一样，但是大致都包括了菜单栏、侧边栏、站点图标、头像等常用项，如下是 NexT 主题的部分配置细节展示，其它主题可以去主题官网详细了解。

在站点根目录打开命令行，执行hexo s，如下图所示状态
image.png

在浏览器中访问http://localhost:4000/即可预览网站全貌，在命令行 Ctrl+C 即可停止预览。
Step 1: 新建文章
在hexo所在目录下，打开terminal，在命令行输入：
hexo new a
a是文章标题，也可以加上双引号,如“a”。
通过这行命令，我们新建出来了一个page，而且是一个post page，page还有其他种，稍后我们会提到。
正确的结果：我们会在_posts里看见多了一个a.md文件。
因此我们也知道了，默认情况下，hexo为我们创建的是markdown文件。刷新页面（http://localhost:4000/）我们能看见新添一个名字叫a的文章，没有任何内容。
而这个_posts文件夹，算是一个比较特殊的文件夹，因为它装着所有你发布出去的文章。
打开a.md文件，我们会看到
---
title: 1
date: 2017-09-15 19:00:41
tags:
---
在这里随便写点什么

然后刷新页面,就会看到你写的内容。与此同时，hexo也会自动为这个post生成一个页面，当我们点击标题，就会进入那个页面。





a.png

Step 2:  草稿箱
上一步我们新建出来的，叫做post page。除了post page，我们还可以新建draft page，也就是草稿。很多时候我们需要先写成草稿，而暂时不发布出去。draft page就可以满足我们的要求，我们的网站上是看不到草稿文件的。
在terminal输入
hexo new draft b
我们会在source下看见一个新的文件夹，_drafts，这个里面会装我们所有的草稿文件。
那写好了的草稿，如何可以在不发布的情况下，预览一下文章在网站上的样子呢？
hexo server --draft
当然，你要先shut down原来开着那个server，才可以开启新的server。如此一来，我们就可以预览草稿文件啦
Step 3: 发布草稿
当你准备好了要发布草稿时:
hexo publish b
你会发现_drafts里的b.md不见了，跑到了
_posts,也就说明你的草稿发布成功了。
Step 4: normal page
�前还不知道该如何用中文称呼这类页面。我们可以把post和draft统称为blog pages，在这之外的一种就是normal pages， 类似一个网站上的“关于”，“了解我们”之类的页面。
这类page要如何新建呢？
hexo new 
