---
title: Hexo博客系统多终端同步数据
date: 2017-05-21 14:15:32
tags: 博客 多终端同步 Hexo 
---

由于更换了pc 原来的博客环境失效，幸好提前将原始文件传到了github上，在搭建好本地环境后做一次同步就可恢复了。
在初次搭建好博客系统后就有一次因为系统重装丢失了搭建好的博客系统，当时系统还没备份，后来将新的博客系统搭建好后全部同步到了github
这样在换电脑或重装系统就不会丢失以前的资料了。现将大体流程做个记录备份。

### 一、搭建本git环境

下载自己喜欢的git版本安装就可以，安装完可以和自己的github账户关联，添加ssh密钥。此处不做祥述。

### 二、使用github+hexo+nodejs 搭建自己的博客系统
使用github+hexo+node.js 搭建博客系统的方法就不再这里多讲了，不清楚可以[google](https://www.google.com/ncr)、[百度](http://www.baidu.com)一下或[查看此处](https://easthj.github.io/2017/03/03/using-hexo-and-github-to-build-yourslef-blog/)

### 三、博客系统的原始文件上传

>**1.进入博客系统的原始文件夹的根目录打开GitBash 或其他命令行工具执行以下命令**

    git init #初始化本地git仓库
    git remote add origin <你的远程仓库地址>    #可以在你的github仓库上复制地址,连接远程仓库
   ![复制github仓库地址](/images/201705/14953539921.png)
    
    git add . #添加目录下所有文件 
    git commit -m "更新说明" #提交并添加更新说明 
    git push -u origin master #推送更新到远程仓库
    
>**2.将博客系统数据同步到另一台电脑**
 
 在要同步数据的电脑上使用github+hexo+node.js 搭建好相应的环境安装git、hexo、nodejs并建好博客系统需要的文件夹
 配置好环境后，打开命令行，进入到博客系统文件夹执行以下命令：
    git init 
    git remote add origin <server> 
    git fetch --all 
    git reset --hard origin/master
    
在执行完上面操作后原先的博客数据就应该同步到新电脑

>**3.在新电脑上写博客发布**

在发布完性博客后，也要将本地数据同步到github存档，使用以下命令

    git add . 
    #可以用git master 查看更改内容 
    git commit -m "更新信息" 
    git push -u origin master 
    #以后每次提交可以直接git push
    
>**4.多终端管理同一个博客**

如果是多个终端管理同一个博客要记得在每次新建博客时要先获取服务器上的数据，使用git pull 获取服务器数据，在发布完博客后要将本地数据上传到服务器

 以上就是hexo 博客系统多终端同步的一种方法，更多方法可以自己在网上获取。 


