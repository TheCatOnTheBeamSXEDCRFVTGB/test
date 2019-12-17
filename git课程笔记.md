# git课程笔记

[TOC]

---



<img src="C:\Users\GYQC\AppData\Roaming\Typora\typora-user-images\1576566753248.png" alt="1576566753248" style="zoom:67%;" />



<img src="C:\Users\GYQC\AppData\Roaming\Typora\typora-user-images\1576566788428.png" alt="1576566788428" style="zoom:67%;" />



## git 基本介绍

仓库又名版本库，英文名repository，我们可以简单理解成是一一个目录，用于存放代码的，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除等操作Git都能跟踪到。

①在安装好后首次使用需要先进行全局配置

```cmd
$ git config--global user.name"用户名"
$ git config--global user.emaill"邮箱地址”
```



②创建仓库
当我们需要让Git 去管理某个新项目/已存在项目的时候，就需要创建仓库了。注意，创建仓库时使用的目录不一-定要求是空目录，选择-一个非空目录也是可以的，但是不建议在现有项目上来学习Git，否则造成的一切后果概不负责！
注意：为了避免在学习或使用过程中出现各种奇葩问题，请不要使用包含中文的目录名（父目录亦是如此）。



③Git常用指令操作
查看当前状态：git status
添加到缓存区：gitadd 文件名

> 说明：git add指令，可以添加一个文件，也可以同时添加多个文件。
> 语法1：git add文件名
> 语法2：git add文件名1文件名2文件名3...
> 语法3：git add .   [添加当前目录到缓存区中]

提交至版本库：git commit-m“注释内容”



## 时光穿梭机

版本回退分为两步骤进行操作：步骤：
①查看版本，确定需要回到的时刻点指令：

```cmd
git log 
git log --pretty=oneline
```

②回退操作
指令：

```cmd
git reset--hard 版本号
```

> 注意：回到过去之后，要想再回到之前最新的版本的时候，则需要使用指令去查看历史操作，以得到最新的commit id。指令：git reflog，

> 小结：
> a.要想回到过去，必须先得到commit id，然后通过git reset-hard进行回退；
> b.要想回到未来，需要使用git reflog进行历史操作查看，得到最新的commit id；
> c.在写回退指令的时候commit id可以不用写全，git 自动识别，但是也不能写太少，至少需要写前4位字符；



## 远程仓库使用

a.使用clone指令克隆线上仓库到本地
语法：

```cmd
git clone 线上仓库地址
```

b.在仓库上做对应的操作（提交暂存区、提交本地仓库、提交线上仓库、拉取线上仓库）
提交到线上仓库的指令：

```cmd
git push
```

> git push 错误提示：
>
> remote: Permission to bjitcast/shop. git denied to chn20190910
> fatal: unable to access ' https://github.com/bjitcast/shop.git/': The requested URL returned error: 403
>
> 403 错误代表没有权限
>
> 原因：
> 在首次往线上仓库提交内容的时候出现了403 的致命错误，原因是不是任何人都可以往线上仓库提交内容，必须需鉴权。
>
> 处理：
> 需要修改“.git/config"文件内容：
>
> #将
> [remote"origin"]
> url =https://github.com/用户名/仓库名.git
> 修改为：
> [remote"origin"]
> url = https://用户名：密码@github.com/用户名/仓库名.git
>
> ```
> [core]
> 	repositoryformatversion = 0
> 	filemode = false
> 	bare = false
> 	logallrefupdates = true
> 	symlinks = false
> 	ignorecase = true
> [remote "origin"]
> 	url = https://github.com/TheCatOnTheBeamSXEDCRFVTGB/test.git
> 	fetch = +refs/heads/*:refs/remotes/origin/*
> [branch "master"]
> 	remote = origin
> 	merge = refs/heads/master
> ```



















