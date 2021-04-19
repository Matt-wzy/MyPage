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
你在我站最底下看到的那个GitHub图标[![PnUyJ3.th.png](https://piccdn.freejishu.com/images/2021/04/18/PnUyJ3.th.png)](https://pic.freejishu.com/image/PnUyJ3)，点进去，就能看到本站的全部代码和博文。[![PnUD1H.png](https://piccdn.freejishu.com/images/2021/04/18/PnUD1H.png)](https://pic.freejishu.com/image/PnUD1H) (啊好羞耻祝贺那个单词竟然拼错了谁能告诉我怎么改commit的标注么)





## 从零开始，搭建博客

###  快进到拥有一个空的仓库

　　此类创建GitHub账户、新建一个repo的教程数不胜数，不想赘述。

　　[以防你真的不会](https://sspai.com/post/54608 "out")，这个链接点进去之后看到 `找到 GitHub Pages 选项`即可

###   寻找合适的模板

> 　　不会吧？不会有人搭建博客之前就已经会写而且写好一个完完整整的静态网站框架了吧？

　　实际上大部分人都没有自己的一套网站模板，如果有请跳过寻找模板直接上传。这里随便给个[模板网站](http://jekyllthemes.org/themes "out") ，找到一个你喜欢的之后下载或者去其主页看看~~或许有使用说明~~。

　　本站用的是[此模板](https://github.com/FromEndWorld/LOFFER "out") ，这个模板有个好处就是全中文说明，及其友好，简单看看readme和里面的链接基本上就啥都会配置了。~~（不会你issue找我，我教）~~

###   上传，配置

　　对你新建的空仓库 `git clone` , 把下下来的zip解压， 更改一点点内容 , `git push` ，git设置啥的我就不教了，有需要issue私聊。

（上面那个也可以直接用克隆样板库的方式完成，随意就好）

　　打开GitHub pages的方法也比较简单，settings-pages-打个勾勾就好啦~

[![PnUQ1b.png](https://piccdn.freejishu.com/images/2021/04/18/PnUQ1b.png)](https://pic.freejishu.com/image/PnUQ1b)

　　配置到这一步，你就可以打开看到模板网站啦~~~~

## 增删内容，更改框架

###  基本

　　谁不想啥都不动然后立刻开箱使用~~

####   更改 _config.yml 文件

　　这个是建站必改的配置文件了，这个文件里面包含了有关网页正常运转的很多配置，你看代码便会明白它是怎么运作的，不过就目前而言，我们只需要知道这个文件需要被改动而且我们有详细的改动说明已经写在文件里面的注释里了。

　　第一个要改的便是网站的名字和描述，这个没啥好说的，主要是homepage里面展示出来的那样

[![PnUp8R.png](https://piccdn.freejishu.com/images/2021/04/18/PnUp8R.png)](https://pic.freejishu.com/image/PnUp8R)[![PnU2O5.png](https://piccdn.freejishu.com/images/2021/04/18/PnU2O5.png)](https://pic.freejishu.com/image/PnU2O5)

　　再有就是repo的名字，照着说明改成你仓库的名字的就行[![PnU3fy.png](https://piccdn.freejishu.com/images/2021/04/18/PnU3fy.png)](https://pic.freejishu.com/image/PnU3fy)

 　　至此 _config.yml 已经基本改完，起码你的网站刷新完后应该看起来正常（指和模板一摸一样）。

　　如果想要自定义404页面工作正常的话，记得在404.md顶上改一下改成这个样子[![PnU6m8.png](https://piccdn.freejishu.com/images/2021/04/18/PnU6m8.png)](https://pic.freejishu.com/image/PnU6m8)

```html
---
permalink: /404.html
layout: page
title: 404 - Page not found
---
```

　　至此，基础的配置已经结束了，你还可以在此配置文件里面更改您的页脚注等等，根据个人喜爱自行发挥即可。

　　看到这里，你自然会担心如果自己配置的时候改错了会怎么样：不用担心，如果你配置的时候产生了严重的语法错误（比如说该加的空格忘了加），GitHub的Jekyll工具会报错，然后给你发一封邮件说明你的repo对应的网页构建失败，这时候你简单看一看是不是哪里的空格一不小心给删了，补上去重新提交就可。

####  添加博文、编辑内容

　　其实readme里面指向的链接中已经[说的很清楚了](https://fromendworld.github.io/LOFFER/document/#第三步-发布博文 "out") ，以防你还是看不明白我来给你说一下。

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

##### 图床

　　你会发现使用md文件编写博客的时候无法像编写word文档一样直接粘贴如图片，如果在typora这样的编辑器里面直接粘贴会出现文件名+本地文件地址，这样子的话别人是绝对无法看到你想展示的图片的，一个合适的解决办法就是将图片上传的图床并使用图床地址。而现在互联网上图床有特别多，我个人对于那些要求图片大小小于0.5M的主流图床并不感兴趣，相反的，我选择[freejishu搭建的图床](https://pic.freejishu.com/ "out") 他本人用爱发电搭建起了一个图床系统，虽然不知道能用多久，但是用一天爽一天哈哈哈（（（（谁叫他的图床没有使用限制哈哈哈当然我也不会传什么不符合主流价值观的图片上去的。

###   进阶

　　如果你不止满足于开箱即用，那么你可以对模板进行一定的修改。

####    增加google analytics

　　此网站的模板自带google analytics支持，但是不知道怎么的，我怎么配置都不生效，于是被迫自己改了改。

　　首先，你需要一个**账号，然后……算了快进到你拿到G代码

[![PnUOeO.png](https://piccdn.freejishu.com/images/2021/04/18/PnUOeO.png)](https://pic.freejishu.com/image/PnUOeO)

　　然后下面有代码添加说明，按照说明加到head里面即可。

　　什么？你不知道怎么加进去？~~啊哈那是因为我没说~~ 这个网页的布局不是说一个html就是一个页面的，而是一层套一层，层层嵌套，具体我不是有关专业从业人员也说不明白为什么，但是你只要知道在代码里看到如下的内容就说明这个页面引用了另一个页面内的全部代码。[![PnUSK0.png](https://piccdn.freejishu.com/images/2021/04/18/PnUSK0.png)](https://pic.freejishu.com/image/PnUSK0) 这里说的是用了head.html里面的全部代码。

　　现在你就知道了，你只需要找到head.html里面对应的地方加入谷歌给你的分析代码即可。

　　找到/_include/analytics.html，删掉原有的部分，然后加入谷歌给你的那一块代码，然后再去head.html里面把插入代码的语句适当往前提，比如说我的就改成了这样[![PnUvzY.png](https://piccdn.freejishu.com/images/2021/04/18/PnUvzY.png)](https://pic.freejishu.com/image/PnUvzY)

　　然后你守着谷歌的实时分析数据就可以啦~记得提交完之后等一两分钟多刷新刷新你的网页。

####    增加Aplayer

　　使用说明[在这](https://matt-wzy.github.io/MyPage/firstComment/#这一段是我加的) ，而如何将其添加到网站里面回头再讲，本质是加js

　　一个合格的博客文章，怎能没有BGM的加持呢？对于加BGM，其实很早以前就有大神提出了解决方案，Aplayer做音乐播放器，mettingjs做网络音乐id解析器，两者结合即可达到输入音乐id即出音乐的作用，如下所示：

<div>
    <meting-js server="netease" type="song" id="569212210" autoplay="false" list-max-height=1200px>
    </meting-js>
</div>
　　将这样[棒棒的播放器](https://github.com/metowolf/MetingJS "out")加入你的网页只需要分为三步：

- 第一步：head加入对应代码

  ```html
  <!-- require APlayer -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.css">
  <script src="https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.js"></script>
  <!-- require MetingJS -->
  <script src="https://cdn.jsdelivr.net/npm/meting@2/dist/Meting.min.js"></script>
  ```

  

- 第二部：文章内容（在 * - * - * .md文件中）直接写html代码

  ```
  <div>
      <meting-js
          server="netease"
          type="playlist"
          id="60198">
      </meting-js>
  </div>
  ```

  

- 第三步：提交并聆听~




## Option

|option               |default      |description|
|:--------------------|:------------:|:----------|
|id              |**require**   |song id / playlist id / album id / search keyword|
|server          |**require**   |music platform: `netease`, `tencent`, `kugou`, `xiami`, `baidu`|
|type            |**require**   |`song`, `playlist`, `album`, `search`, `artist`|
|auto            |options       |music link, support: `netease`, `tencent`, `xiami`|
|fixed           |`false`       |enable fixed mode|
|mini            |`false`       |enable mini mode|
|autoplay        |`false`       |audio autoplay|
|theme           |`#2980b9`     |main color|
|loop            |`all`         |player loop play, values: 'all', 'one', 'none'|
|order           |`list`        |player play order, values: 'list', 'random'|
|preload         |`auto`        |values: 'none', 'metadata', 'auto'|
|volume          |`0.7`         |default volume, notice that player will remember user setting, default volume will not work after user set volume themselves|
|mutex           |`true`        |prevent to play multiple player at the same time, pause other players when this player start play|
|lrc-type         |`0`           |lyric type|
|list-folded      |`false`       |indicate whether list should folded at first|
|list-max-height   |`340px`       |list max height|
|storage-name     |`metingjs`    |localStorage key that store player setting|

Documentation for APlayer can be found at <https://aplayer.js.org/#/home?id=options>

####    增加一言

　　[一言](https://developer.hitokoto.cn/sentence/demo/#网页 "out")

　　作为一个完善的网页怎能没有美丽的修饰？一言可以说是被很多网站所采用的所增加他们网站美观度的一个小工具，没有很复杂，就网上选取的一句话，或调皮，或惊喜，或感触，总之，你会期待每次刷新所呈现出来的新鲜句子，你会觉得他们永远不会重复，并且时刻充满新鲜于惊喜。

　　虽然一言api提供了选择范围的接口，~~但是我懒~~但是我觉得没有必要筛选，随意刷新出来自己所没能在日常生活中看到的句子，难道不是一件值得庆祝的事情么？

　　具体的构建方法也很简单，将此代码放入head中

```html
  <!-- toko -->
  <script>
    fetch('https://v1.hitokoto.cn')
      .then(response => response.json())
      .then(data => {
        const hitokoto = document.getElementById('hitokoto')
        hitokoto.href = 'https://hitokoto.cn/?uuid=' + data.uuid
        hitokoto.innerText = data.hitokoto
      })
      .catch(console.error)

  </script>
```

　　然后将此段代码插入合适的位置（如页脚）

```html
      <!-- toko -->
      <p id="hitokoto">:D 获取中...</p>
```

　　实际实战中发现如果网页会动态调整其layout的话，用一个p标签可能会导致总是有一个显示方式一直显示获取中，解决办法就是在不同的排版方式中都加入p标签并改id，然后头文件改成这样：

```html
  <!-- toko -->
  <script>
    fetch('https://v1.hitokoto.cn')
      .then(response => response.json())
      .then(data => {
        const hitokoto = document.getElementById('hitokoto')
        const hitokoto2 = document.getElementById('hitokoto2')
        hitokoto.href = 'https://hitokoto.cn/?uuid=' + data.uuid
        hitokoto.innerText = data.hitokoto
        hitokoto2.href = 'https://hitokoto.cn/?uuid=' + data.uuid
        hitokoto2.innerText = data.hitokoto
      })
      .catch(console.error)

  </script>
```

This page is still building&updating ... 

[<img src="{{ site.baseurl }}/images/404.jpg" alt="Constructocat by https://github.com/jasoncostello" style="width: 400px;"/>{: .center-image}]({{ site.baseurl }}/)