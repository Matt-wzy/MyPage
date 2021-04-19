---
layout: post
title: 第一篇博客
date: 2021-04-15
author: Matt-wzy
tags: [essay]
comments: true
toc: true
pinned: true
theme: github-dark-orange
---


　　这应该是我配置好 [loffer](https://github.com/FromEndWorld/LOFFER "out:loffer") 之后的第一个博文，直接修改使用手册document作为我的第一篇博客了（哈哈哈哈）.

<!-- more -->

（疑惑性行为++）

下面是原来的使用手册里面自带的内容。

------------
# 这一段是我加的
网页内网易云player使用教程：Powered by Aplayer


<div>
    <meting-js server="netease" type="song" id="30284674" autoplay="false" list-max-height=1200px>
    </meting-js>
</div>

文章中添加如下代码即可加入音乐：

``` 
    <div>
    <meting-js server="netease" type="playlist" id="666375" autoplay="false" list-max-height=1200px>
    </meting-js>
    </div>
```

（songid 30284674 ）

```
<meting-js
	auto="https://y.qq.com/n/yqq/song/001RGrEX3ija5X.html">
</meting-js>
```
- server 后面的是我们要用的音乐平台，可以填写的有`netease`, `tencent`, `kugou`, `xiami`, `baidu` 。这里我用的是网易 `server=”netease”`

- type 后面可以填写 `song`, `playlist`, `album`, `search`, `artist`，分别是歌曲，歌单，专辑，搜索，歌手。这里我用的是歌单，所以 `type=”playlist”`。

- id 是我们歌单的链接号码，这个数字我们可以登录网页版的网易云，打开一个歌单，从网址就能看出 id 是多少。

server：指明是网易云音乐还是QQ音乐

type：指明是歌单还是一首歌

id：歌单的ID或者歌的ID

autopaly：自动播放

list-max-height：playlist的最大高度

[meeting.js官网](https://github.com/metowolf/MetingJS "out")

[更新网页](https://www.lefer.cn/posts/21467/ "out")

[这个网页](https://bend1031.github.io/2019/09/21/Insert-music-code-in-the-blog/ "out这个网页")告诉你怎么配置到页面左下角，[这个页面](http://yangyingming.com/article/428/ "out这个页面")告诉你怎么配置到文档内部

------------
# 这一段是原文档有的内容

　　更简单的办法是使用[Typora](https://typora.io/)，这是一个全图形化界面，全实时预览的Markdown写作软件，非常轻量，而且免费。

![img](https://raw.githubusercontent.com/FromEndWorld/LOFFER/master/images/Typora.png)

　　在发布博文前，你需要在文章的头部添加这样的内容，包括你的文章标题，发布日期，作者名，和tag等。

    ---
    layout: post
    title: LOFFER文档
    date: 2019-06-02
    Author: 来自中世界
    categories: 
    tags: [sample, document]
    comments: true
    --- 

　　完成后，保存为.md文件，文件名是date-标题，例如 2019-06-02-document.md (注意这里的标题会成为这篇博文的链接，所以请使用字母而非中文，它不影响页面上显示的标题)，然后上传到_posts文件夹，再提交修改，很快就可以在博客上看到新文章了。
