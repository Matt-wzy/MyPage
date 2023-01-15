---
layout: post
title: 本网站模板复制办法
date: 2023-01-15
author: Matt-wzy
tags: [document]
comments: true
toc: true
---

好耶，终于写个教程教你们怎么用我这个github pages模板喽~

<!-- more -->

<div>
    <meting-js server="netease" type="song" id="30284674" autoplay="false" list-max-height=1200px>
    </meting-js>
</div>

首先，本网站所使用模板来自[GitHub - FromEndWorld/LOFFER: 博客主题 A Jekyll theme with Chinese UI and document](https://github.com/FromEndWorld/loffer) ，本人在其基础上稍加修改，本教程旨在让希望使用我修改后内容作为模板建站的同学更快了解本网站所使用建站模板，大部分内容来自于上述连接中的教程。

这是一个可以直接发布在GitHub page的Jekyll博客，你不需要编写代码或使用命令行即可配置属于你的网站。

为什么使用本模板（部分优点指Matt-Wang修改后的模板）建站？

- 静态网站，但无需编写HTML，CSS。只需要编写`.md`文件内容，且不需要使用Hexo等框架在本地编译，直接commit并push等待github为您编译好网站后即可看到效果。也就是说，本模板对比其他静态github pages模板有着不需要本地编译的优点。

- 多项功能快速响应，尽本人最大可能维护至可用水平。原仓库LOFFER为2019年创立，经过作者与其他人员积极贡献到本文撰写时最新一次更新在2021年，虽然那时原仓库已经相当完善，但是现在来看还有包括但不限于无暗色模式等现代化交互问题，目前有三个Open issues作者未能回复 。我在使用过程中发现没有Aplayer、暗色模式等问题时快速响应自己的要求，在自己能力范围之内搜索出可用结果并反复试验进行适配，最终得到本网站。

- 虽然目前还有无法自由开关目录列表问题无法解决，但不得不说本博客模板已经是一个成熟且好看的模板。

- 拥有评论系统架构，在本页末尾你能发现（可能需要加载很长时间），基于github仓库issue，不需要额外购买服务器即可获得类似评论系统的功能，便宜大碗。

- 支持LaTex渲染



# 快速上手

1. 点击fork或者下载后创建新仓库提交commit

2. 删除`_posts`文件夹内所有内容

3. 更改`_config.yml`文件中对应的内容，其中每一部分都有详细中文注释第92行的`google_analytics`可能失效了，想要修改需要去`_includes/analytics.html`第10行改成自己的代码，如果不需要或者暂时不想配置，可以删除第4行到第11行的内容

4. 在你的仓库的github页面，点击`Settings` 左侧找到`code and automation`中的 `Panges` ，点击后找到`Branch`，里面如果没被配置则默认为`None`，点一下切换成`master`分支，点击`Save` ，等待github为你的页面构建结束，即可在 `https://github用户名.github.io/仓库名/`中找到你的网站。当然你可以根据需要自行配置自己的域名。

5. 至此你的博客框架已经搭建好，现在你就可以新建一个全新的博文了！我们到`_posts`文件夹下创建一个文件，文件名是`date-标题`，例如 `2019-06-02-document.md` (注意这里的标题会成为这篇博文的链接，所以请使用字母而非中文，它不影响页面上显示的标题)

在发布博文前，你需要在文章的头部添加这样的内容，包括你的文章标题，发布日期，作者名，和tag等。

```
---
layout: post
title: 第一个博文！
date: 2023-01-16
Author: Matt-Wang
categories: 
tags: [sample, document]
comments: true
--- 


```

其中，`layout: post` 不用改，`toc: true` 是指打开目录显示（桌面版浏览器生效）

6. `commit` `push`，并稍等两分钟，你就可以在你的博客页面看到自己的博文啦！

7. 如果博文中需要加图片，需要放到图床中，也可以放到仓库里。

# 特色功能

需要手动配置参数的后面没有*, 有 * 的表示不需要配置参数开箱即用。

## Aplayer

> 老早就想说了，老得意了我

网页内网易云player使用教程：Powered by Aplayer

文章中添加如下代码即可加入音乐：

```html
    <div>

    <meting-js server="netease" type="playlist" id="666375" autoplay="false" list-max-height=1200px>

    </meting-js>

    </div>
```

（songid 30284674 ）

```html
<meting-js

    auto="https://y.qq.com/n/yqq/song/001RGrEX3ija5X.html">

</meting-js>
```

- server 后面的是我们要用的音乐平台，可以填写的有`netease`, `tencent`, `kugou`, `xiami`, `baidu` 。这里我用的是网易 `server=”netease”`

- type 后面可以填写 `song`, `playlist`, `album`, `search`, `artist`，分别是歌曲，歌单，专辑，搜索，歌手。这里我用的是歌单，所以 `type=”playlist”`。

- id 是我们歌单的链接号码，这个数字我们可以登录网页版的网易云，打开一个歌单，从网址就能看出 id 是多少。

autopaly：自动播放    list-max-height：playlist的最大高度

Documentation for APlayer can be found at [APlayer](https://aplayer.js.org/#/home?id=options “out”)

## 外部连接跳转

博客中经常需要有连接到外部的内容，比如说上面的Aplayer就是个很好的例子，你如果点击会发现其会使用一个新的页面打开连接，而如果你直接使用md标准的连接写法的话，会发现它是页面内打开的，也就是说万一你的用户点击之后关掉了打开的网页，他也就需要重新去历史记录找到你的页面才能打开重新看，而配置外部跳转与页内跳转只需要一个`"out"`标志，具体为：

`[APlayer](https://aplayer.js.org/#/home?id=options "out")` 新页面打开[例子](https://aplayer.js.org/#/home?id=options "out")

`[APlayer](https://aplayer.js.org/#/home?id=options)` 本页面打开[例子](https://aplayer.js.org/#/home?id=options)

## 暗色模式*

此功能不需要你配置任何内容，但是由于目前实现方式的限制，页面在加载时为了防止夜间晃眼默认使用暗色模式加载，等完全加载成功后js脚本便会自动判断用户系统当前是否处于暗色模式并对应响应，且网页打开后会一直监听用户系统暗色模式是否切换从而自动切换，同时用户也可以手动点击右下角按钮（虽然目前做的很烂）来切换亮暗色模式。

## 评论区

此区域施工中……若烂尾可参考[原仓库教程](https://fromendworld.github.io/LOFFER/document/#可选添加评论区)

## Markdown语法

请参考[原仓库文档](https://fromendworld.github.io/LOFFER/chinese-markdown-cheatsheet/)或者自行检索

## LaTex

请参考[原仓库文档](https://fromendworld.github.io/LOFFER/math-test/) 

LaTeX渲染已经在全站头部文件引入，可以直接使用，公式块上下使用`$$`标明，内联公式则用`$`.

最好不要让公式出现在文章摘要里。

## 文章摘要

Jekyll的默认文章摘要是第一段，但原仓库提供了手动分割线，默认为`<!-- more -->`，并且加入了首页摘要的字符数限制。

Block math test

```
$$
\begin{align*}
y = y(x,t) &= A e^{i\theta} \\
&= A (\cos \theta + i \sin \theta) \\
&= A (\cos(kx - \omega t) + i \sin(kx - \omega t)) \\
&= A\cos(kx - \omega t) + i A\sin(kx - \omega t)  \\
&= A\cos \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big) + i A\sin \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big)  \\
&= A\cos \frac{2\pi}{\lambda} (x - v t) + i A\sin \frac{2\pi}{\lambda} (x - v t)
\end{align*}
$$
```

$$
\begin{align*}
y = y(x,t) &= A e^{i\theta} \\
&= A (\cos \theta + i \sin \theta) \\
&= A (\cos(kx - \omega t) + i \sin(kx - \omega t)) \\
&= A\cos(kx - \omega t) + i A\sin(kx - \omega t)  \\
&= A\cos \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big) + i A\sin \Big(\frac{2\pi}{\lambda}x - \frac{2\pi v}{\lambda} t \Big)  \\
&= A\cos \frac{2\pi}{\lambda} (x - v t) + i A\sin \frac{2\pi}{\lambda} (x - v t)
\end{align*}
$$





```
$\lim_{x \to \infty} \exp(-x) = 0$
```


Inline math test , $\lim_{x \to \infty} \exp(-x) = 0$


