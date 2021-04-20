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

　　Git本质就是一个软件，而使用软件的第0步是安装软件，[git的下载链接](https://git-scm.com/download/win "out") ,如果下载速度缓慢，可以试试[这个链接](https://474b.com/f/19128606-490774539-30c811 "out") （为什么用诚通？~~别问，问就是和百度云过不去~~）

　　如果没有截图提示的话就一路下一步![PnUbSQ.png](https://piccdn.freejishu.com/images/2021/04/20/PnUbSQ.png) 这里选择你需要用git的代码编辑工具，默认是nano或者vim，但是如果你装了VSCode而且比较喜欢用它，那么你就可以像我一样换成VSCode。剩下的部分一路下一步或者按照自己的喜好来选就可以。

　　![PnUkfK.png](https://piccdn.freejishu.com/images/2021/04/20/PnUkfK.png) 随意找一个有文件的地方右键能看到Git Bash Here就说明你已经安装好git了，之后提到`运行git代码`默认说的就是找到对应文件夹右键选择Git Bash Here。
　　先随便找一个地方打开git bash，运行如下代码，`Your Name`部分改成你的网名或者今后使用Git、GitHub的昵称，`email@example.com`部分写成你的邮箱。（注：$是系统自动生成的命令提示符，别复制）

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

比方说我的话就应该这样配置：

![PnU4m4.png](https://piccdn.freejishu.com/images/2021/04/20/PnU4m4.png)

　　好了，现在电脑里就已经有一个Git工具了，快来新建一个文件夹试试吧！

> 注意，剩下的部分借用廖雪峰的教程并对其有大幅度的精简，如果看完觉得还想深入了解请自行搜索git使用教程或者访问廖雪峰的git教程网站 <https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304> 





　　到现在为止，你已经可以使用git的基本功能做到版本控制了，但是目前你还不能使用git和GitHub联动，也不能将代码上传到GitHub上看完下面的部分你就知道如何使用git和GitHub联动以及使用git命令上传、下载代码。