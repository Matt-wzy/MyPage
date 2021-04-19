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

## 什么是&为什么用 GitHub&Git

　　[Github](https://github.com/) ,是一个代码托管网站，简单来讲，就是给你的代码一个存放的地方。使用GitHub需要用到Git工具，这个工具是用来控制代码版本的，简单来讲，就是git可以协助你记下这次提交和上一次提交之间，代码变化了哪些部分。

　　然而这就会产生一个问题：为什么你的代码会需要存在GitHub上呢？直接在本地电脑上编辑不好么？很好，下面我就来解释一下为什么会有GitHub：

- 多人合作的时候，代码不一定只有一份&代码要在多人多台设备之间同步
- 一个大的项目通常不是一蹴而就的，需要多次逐步的编写于修改，记录更改详情有助于开发人员了解项目的构建的从无到有的流程
- 后期Debug时，合理的利用git和其版本回退功能可以有助于快速定位解决问题和解决因为Debug引入的问题。

　　总之，在我们RoboMaster队伍中视觉和电控代码都会上传到Github上并使用Git控制代码版本。