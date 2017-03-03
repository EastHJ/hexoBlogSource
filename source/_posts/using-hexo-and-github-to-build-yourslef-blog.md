---
title: 利用hexo和github搭建个人博客平台
date: 2017-03-03 22:35:08
tags: hexo
---
## 利用hexo和github搭建个人博客平台

  学习新的知识最好的老师就是兴趣，如果兴趣不大那就想想Money，找对自己有用的能让自己升值加薪的学！只要努力你总会得到些东西！
  我平时喜欢瞎折腾，最近喜欢上了编程，想把自己学的东西找个地方存起来，慢慢的构建自己的知识树。现在有很多工具都可已达到这个效果，但是通过自己的折腾建立起来的平台，自己会更有成就感，不是么！
就像这句话:

#### 活着就是折腾!

  GitHub是一个利用Git进行版本控制、专门用于存放软件代码与内容的共享虚拟主机服务。它由GitHub公司（曾称Logical Awesome）的开发者Chris Wanstrath、PJ Hyett和Tom Preston-Werner使用Ruby on Rails编写而成。
  GitHub同时提供付费账户和免费账户。这两种账户都可以创建公开的代码仓库，但是付费账户也可以创建私有的代码仓库。根据在2009年的Git用户调查，GitHub是最流行的Git访问站点。除了允许个人和组织创建和访问代码库以外，它也提供了一些方便社会化软件开发的功能，包括允许用户追踪其他用户、组织、软件库的动态，对软件代码的改动和bug提出评论等。GitHub也提供了图表功能，用于显示开发者们怎样在代码库上工作以及软件的开发活跃程度。

  Github上虽然绝大多数是程序员，但它作为一个协作社区，也在慢慢渗透到更多的具有协作性质的领域。想获得更多的信息，自己去google 或百度吧！本篇博客的主要目的还是作为我自己折腾的一个记录！
  下面进入正题吧。

#### 1. 创建Github 域名和空间

#####1.1注册

  首先你需要注册一个Github账号，已有的可以下一步了，创建仓库，注意username，这会影响到你的域名，你的域名将会是 username.github.io ，所以认真的取个名字吧。
      ![create github account](/images/createaccount.JPG)
  注册过程需要验证你的邮箱,再有不懂的问度娘吧。

##### 1.2 创建仓库

  然后需要创建一个仓库(repository) 来存储我们的网站，点击首页任意位置出现的 New repository按钮创建仓库,
![new repo](/images/newrepo.jpg)
就是上面这货！
Respository name中的username.github.io 的username 一定与前面的Owner 一致，记住你的username下面会用到。

![create new repo](/images/newrepo2.JPG)
  第一步就已经完成了，下面是安装。

####  2. 安装

  Hexo 可以说是目前最流行的博客框架了，基于Nodejs，更多信息可以google、百度，下面需要安装的工具包括 Git，Nodejs，Hexo。（不明白Internet）

##### 安装Git

  搜索相应的安装程序下载来安装 git for windows

##### 安装Nodejs

  去官网Nodejs根据自己的系统选择合适的版本下载安装

##### 安装Hexo

  以上所有都安装完成之后再安装Hexo,鼠标右键打开 Git Bash 输入下面的命令！

    $ npm install hexo-cli -g

  所有必须工具已经安装完成，下面我们就可以生成博客，上传至我们的Github 仓库了。

#### 3. 编写，发布

  接下来我们需要用Hexo初始化一个博客，然后更改一些自定义的配置，或者加上自己喜欢的主题，写上第一篇文章，然后发布到自己的个人Github网站(username.github.io)。

##### 创建博客

  将下面的username替换成你自己的username(username.github.io也可以是其他的，但是其它的名称需要再多了解点Git知识，进行设置，想了解自己脑补去吧)，执行成功后，会创建出一个名为 username.github.io 的文件夹。

    $ hexo init username.github.io

##### 更改配置

**主题安装**

  为了使博客不太难看，我们需要安装一个主题，切换至刚刚生成的Hexo 目录，安装主题

    $ cd username.github.io
    $ git clone https://github.com/iissnan/hexo-theme-next themes/next

  这里随便选了一个主题，在这里Hexo也有更多主题供你选择。
  基础配置：打开文件位置username.github.io/_config.yml修改几个键值对，下面把几个必须设置的列出来按需求修改，记得保存， 还有注意配置的键值之间一定要有空格。更多设置…

>title: youBlogName //你博客的名字<br>
author: username //你的名字<br>
language: zh-Hans //语言 中文<br>
theme: next //刚刚安装的主题名称<br>
deploy:<br>
type: git //使用Git 发布<br>
repo: https://github.com/username/username.github.io.git // 刚创建的Github仓库<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;或者使用ssh 格式 ：git@github.com:username/username.github.io.git

** 主题配置：**

  主题配置文件在username.github.io/themes/next/_config.yml中修改，这里略过。设置详情

##### 写文章

  所有基础框架都已经创建完成，接下来可以开始写你的第一篇博客了
  在username.github.io/source/_posts下创建你的第一个博客吧，例如，创建一个名为FirstNight.md的文件，用Markdown大肆发挥吧，注意保存。
如：

>title: First Night
>
>我有一头小毛驴，可是我从来都不骑。

####测试

    $ hexo s

  测试服务启动，你可以在浏览器中输入https://localhost:4000 访问了。

>安装hexo-deployer-git自动部署发布工具

    $ npm install hexo-deployer-git –save

#### 发布

  测试没问题后，我们就生成静态网页文件发布至我们的Github pages 中。

    $ hexo clean && hexo g && hexo d

  如果这是你的第一次，终端会让你输入Github的邮箱和密码，正确输入后，就会把你的博客上传至Github了。以后在每次把博客写完后，执行一下这个命令就可以直接发布了。在浏览器中输入 http://username.github.io 就能够访问了。

  时间有限，这里只说到了简单的博客创建流程，github 还后更丰富的资源有时间可以自己探索

