---
layout: post
title: Pages 建站说明
date: 2021-04-18
author: Matt-wzy
tags: [essay,document]
comments: true
toc: true
#theme: github-dark-orange
---

我觉得你看完本篇博客将会知道本站是怎么来的以及我编写博文的时候是如何操作的。

<!-- more -->

<div>
    <meting-js server="netease" type="song" id="492390949" autoplay="false" list-max-height=1200px>
    </meting-js>
</div>




## 从零开始，搭建博客

### 　快进到拥有一个空的仓库

　　此类创建GitHub账户、新建一个repo的教程数不胜数，不想赘述。

　　[以防你真的不会](https://sspai.com/post/54608)，这个链接点进去之后看到 `找到 GitHub Pages 选项`即可

### 　寻找合适的模板

> 　　不会吧？不会有人搭建博客之前就已经会写而且写好一个完完整整的静态网站框架了吧？

　　实际上大部分人都没有自己的一套网站模板，如果有请跳过寻找模板直接上传。这里随便给个[模板网站](http://jekyllthemes.org/themes) ，找到一个你喜欢的之后下载或者去其主页看看~~或许有使用说明~~。

　　本站用的是[此模板](https://github.com/FromEndWorld/LOFFER) ，这个模板有个好处就是全中文说明，及其友好，简单看看readme和里面的链接基本上就啥都会配置了。~~（不会你issue找我，我教）~~

### 　上传，配置

　　对你新建的空仓库 `git clone` , 把下下来的zip解压， 更改一点点内容 , `git push` ，git设置啥的我就不教了，有需要issue私聊。

（上面那个也可以直接用克隆样板库的方式完成，随意就好）

　　打开GitHub pages的方法也比较简单，settings-pages-打个勾勾就好啦~

[![PnUQ1b.png](https://piccdn.freejishu.com/images/2021/04/18/PnUQ1b.png)](https://pic.freejishu.com/image/PnUQ1b)

　　配置到这一步，你就可以打开看到模板网站啦~~~~

## 增删内容，更改框架

### 　基本

#### 　　更改_config.ymal文件

　　这个是建站必改的配置文件了，这个文件里面包含了有关网页正常运转的很多配置，你看代码便会明白它是怎么运作的，不过就目前而言，我们只需要知道这个文件需要被改动而且我们有详细的改动说明已经写在文件里面的注释里了。

　　第一个要改的便是网站的名字和描述，这个没啥好说的，主要是homepage里面展示出来的那样

[![PnUp8R.png](https://piccdn.freejishu.com/images/2021/04/18/PnUp8R.png)](https://pic.freejishu.com/image/PnUp8R)[![PnU2O5.png](https://piccdn.freejishu.com/images/2021/04/18/PnU2O5.png)](https://pic.freejishu.com/image/PnU2O5)

　　再有就是repo的名字，照着说明改成你仓库的名字的就行[![PnU3fy.png](https://piccdn.freejishu.com/images/2021/04/18/PnU3fy.png)](https://pic.freejishu.com/image/PnU3fy)

 　　至此 _config.yal 已经基本改完，起码你的网站刷新完后应该看起来正常（指和模板一摸一样）。

　　如果想要自定义404页面工作正常的话，记得在404.md顶上改一下改成这个样子[![PnU6m8.png](https://piccdn.freejishu.com/images/2021/04/18/PnU6m8.png)](https://pic.freejishu.com/image/PnU6m8)

```html
---
permalink: /404.html
layout: page
title: 404 - Page not found
---
```

　　至此，基础的配置已经结束了，你还可以在此配置文件里面更改您的页脚注等等，根据个人喜爱自行发挥即可。

#### 　　添加博文、编辑内容

　　其实readme里面指向的链接中已经[说的很清楚了](https://fromendworld.github.io/LOFFER/document/#第三步-发布博文) ，以防你还是看不明白我来给你说一下。

　　[![PnUFpB.png](https://piccdn.freejishu.com/images/2021/04/18/PnUFpB.png)](https://pic.freejishu.com/image/PnUFpB)

　　你的目录至少看起来应该和这个样子很像，想开始写一个博文，你只需要打开_posts文件夹，然后在里面新建一个md为后缀的文件，文件名应该类似于日期-名字，这里我没有试过中文名是否可用，反正我用的是英文名因为这个名字可是要上URL的。

　　然后按照指示，你需要在新的文件里面插入如下的开头：

```html
---
layout: post
title: Pages 建站说明
date: 2021-04-18
author: Matt-wzy
tags: [essay,document]
comments: true
toc: true
---
```

　　其中，`layout: post` 不用改，`toc: true` 是指打开目录显示（桌面版浏览器生效），剩下的自己猜猜就猜出来了。~~主要是懒不想一个个找然后发出来~~

### 　进阶

#### 　　增加google analytics

#### 　　增加Aplayer

#### 　　增加一言







Still building ... 

[<img src="{{ site.baseurl }}/images/404.jpg" alt="Constructocat by https://github.com/jasoncostello" style="width: 400px;"/>{: .center-image}]({{ site.baseurl }}/)