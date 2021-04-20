---
layout: post
title:  GitHub & Git 使用说明
date: 2021-04-19
author: Matt-wzy
tags: [document]
comments: true
toc: true
#theme: github-dark-orshen
---

<!-- DocNo1 -->

<div>
    <meting-js server="netease" type="playlist" id="6720015398" autoplay="false" list-max-height=1200px>
    </meting-js>
</div>

<!-- more -->

## 什么是&为什么用 GitHub&Git

　　[Github](https://github.com/ "out") ,是一个代码托管网站，简单来讲，就是给你的代码一个存放的地方。使用GitHub需要用到Git工具，这个工具是用来控制代码版本的，简单来讲，就是git可以协助你记下这次提交和上一次提交之间，代码变化了哪些部分。

　　然而这就会产生一个问题：为什么你的代码会需要存在GitHub上呢？直接在本地电脑上编辑不好么？很好，下面我就来解释一下为什么会有GitHub：

- 多人合作的时候，代码不一定只有一份&代码要在多人多台设备之间同步
- 一个大的项目通常不是一蹴而就的，需要多次逐步的编写于修改，记录更改详情有助于开发人员了解项目的构建的从无到有的流程
- 后期Debug时，合理的利用git和其版本回退功能可以有助于快速定位解决问题和解决因为Debug引入的问题。

　　总之，在我们RoboMaster队伍中视觉和电控代码都会上传到Github上并使用Git控制代码版本，方便多人协作和控制版本。

## 怎么用Github&Git

### Git使用

#### 安装

　　Git本质就是一个软件，而使用软件的第0步是安装软件，[git的下载链接](https://git-scm.com/download/win "out") ,如果下载速度缓慢，可以试试[这个链接](https://474b.com/f/19128606-490774539-30c811 "out") （为什么用诚通？~~别问，问就是和百度云过不去~~）

　　如果没有截图提示的话就一路下一步![PnUbSQ.png](https://piccdn.freejishu.com/images/2021/04/20/PnUbSQ.png) 这里选择你需要用git的代码编辑工具，默认是nano或者vim，但是如果你装了VSCode而且比较喜欢用它，那么你就可以像我一样换成VSCode。剩下的部分一路下一步或者按照自己的喜好来选就可以。

　　![PnUkfK.png](https://piccdn.freejishu.com/images/2021/04/20/PnUkfK.png) 随意找一个有文件的地方右键能看到Git Bash Here就说明你已经安装好git了，之后提到`运行git代码`默认说的就是找到对应文件夹右键选择Git Bash Here。

#### 初始化

　　先随便找一个地方打开git bash，运行如下代码，`Your Name`部分改成你的网名或者今后使用Git、GitHub的昵称，`email@example.com`部分写成你的邮箱。（注：$是系统自动生成的命令提示符，别复制）

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

比方说我的话就应该这样配置：

![PnU4m4.png](https://piccdn.freejishu.com/images/2021/04/20/PnU4m4.png)

　　好了，现在电脑里就已经有一个Git工具了，快来新建一个文件夹试试吧！

#### 建立本地仓库

> 注意，剩下的部分借用廖雪峰的教程并对其有大幅度的精简，如果看完觉得还想深入了解请自行搜索git使用教程或者访问廖雪峰的git教程网站 <https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304> 

！ 请注意，为了尽可能地减少错误，我们下面的操作均应避免使用中文名和在C盘内部操作。

　　随便找一个目录新建文件夹并随便起一个**英文名** ，比如我在E盘建立了一个新的文件夹`E:\GitTest`作为本次训练使用git命令的目录在此处Git Bash，轻敲

```
git init
```

　　你现在就成功地建立起了一个git仓库（它目前仅存在于你的本地电脑上）![PnUa2z.png](https://piccdn.freejishu.com/images/2021/04/20/PnUa2z.png) 现在我们就可以开始尝试使用git工具所涉及到的命令了。

#### 将文件放入仓库

　　现在我们编写一个`readme.txt`文件，内容如下：

```
Git is a version control system.
Git is free software.
```

　　一定要放到`learngit`目录下（子目录也行），因为这是一个Git仓库，放到其他地方Git再厉害也找不到这个文件。

　　把一个文件放到Git仓库只需要两步。

- 第一步，用命令`git add`告诉Git，把文件添加到仓库：

```
$ git add readme.txt
```

　　执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

- 第二步，用命令`git commit`告诉Git，把文件提交到仓库：

```
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

　　简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，比方说我们在这里新建了readme文件，commit内容就说写了一个readme文件，清晰明了,这样你就能从历史记录里方便地找到改动记录。

　　嫌麻烦不想输入`-m "xxx"`行不行？确实有办法可以这么干，但是强烈不建议你这么干，因为输入说明对自己对别人阅读都很重要。实在不想输入说明的童鞋请自行Google，我不告诉你这个参数。

`git commit`命令执行成功后会告诉你，`1 file changed`：1个文件被改动（我们新添加的readme.txt文件）；`2 insertions`：插入了两行内容（readme.txt有两行内容）。

#### 小结

　　以后常用的命令：

　　初始化一个Git仓库，使用`git init`命令。

　　添加文件到Git仓库，分两步：

1. 使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m <message>`，完成。

　　当然，借助VSCode等工具之后，你或许点几下鼠标即可达成同样的效果，但是那些都是在你了解git命令含义的基础上的进阶操作，而且很多地方没法安装或者很难安装VSCode这样的工具（比方说网络差的情况下），所以起码你要会检索着使用git工具的命令行形态。

　　哦对了，如果你想更进一步了解git的使用的话，不仅可以看[廖雪峰的教程](https://www.liaoxuefeng.com/wiki/896043488029600/896067074338496 "out")，还可以看看[这个网站](https://learngitbranching.js.org/?locale=zh_CN "out")（请用电脑访问）。

-----------



　　到现在为止，你已经可以使用git的基本功能做到版本控制了，但是目前你还不能使用git和GitHub联动，也不能将代码上传到GitHub上看完下面的部分你就知道如何使用git和GitHub联动以及使用git命令上传、下载代码。

### Hello, GitHub

[Github](https://github.com/ "out") ，代码托管网站。

如果你还没有注册账号的话，其实不急，就算没有账户你仍然可以查看一些开源库的代码。

<https://github.com/Matt-wzy/R-M_Robot> （我们的视觉项目~~因为不想调设置，被迫~~开源）

![PnUeeU.png](https://piccdn.freejishu.com/images/2021/04/20/PnUeeU.png)

　　以前我们用到的时候都会点击download zip，以后则会更多地使用`git@github.com:Matt-wzy/R-M_Robot.git`。

　　好了，为了练习git命令和GitHub在线仓库的联动，你起码要有一个GitHub账户了。

#### 注册GitHub账户

　　~~什么？这还要我教？~~ 我随便搜了一下，看到[一个结果](https://cloud.tencent.com/developer/article/1487508 "out")，我也没仔细看，反正你能注册了就行

#### 搞一个仓库

　　你看到外面的GitHub教程大多都是从零创建一个仓库，但其实没有必要，除非你们要从零开始重写整个视觉代码，否则从拿过我们的仓库开始就行~~（实际上是懒得又截图又打字写教程了）~~

　　具体方法如下：

　　为了练习`推送` `修改`命令,首先你需要有仓库的使用权限，这需要建立仓库的管理员设置，在此之前，你可以fork本项目，这样整个仓库的一个备份都到了你的账号底下![PnUhKI.png](https://piccdn.freejishu.com/images/2021/04/20/PnUhKI.png) 　　然后选好一个文件夹 **不要用中文目录** 下载（Git Bash命令）

```
git clone git@github.com:你的GitHub用户名/R-M_Robot.git
```

　　wala~ 你现在已经拿到了和我们视觉组3月27号一模一样的整个项目代码，如果你想可以大致阅览一下，不过我们此篇教程重点在于使用git&GitHub，所以暂不介绍目录结构和代码功能。

　　现在你会发现你下载下来的项目里面有一个隐藏文件夹名字为.git，对的，如此clone下的项目，git已经为你做好初始化了，你也不需要填什么仓库地址搞那些麻烦的东西