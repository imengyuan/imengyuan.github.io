---
title: LyriCloud——网易云音乐专辑歌词爬虫+词云
date: 2017-12-07 16:38:00
tags:
- crawler
categories:
- python

---
Python3.x 简单网络爬虫，网易云音乐整张专辑歌词爬虫+专辑封面风格词云的生成。
<!--more-->
 
### 歌词爬取
python3.x 网络爬虫，requests + BeautifulSoup实现。requests实现基本http操作进行爬取，BeautifulSoup解析网页结构，提取有效信息。
提取出的歌词为json格式，用json模块转成字典，就得到需要的歌词了。最新歌词爬虫代码在这里：[代码和README](https://github.com/ViciaYuan/LyriCloud)

目前是version 2，实现了从专辑的album_id即可得到专辑所有歌的歌词，后续考虑引入数据库储存歌词。
<br>
### 词云生成
生成词云的网站很多，这个链接有一些推荐[我想用代码做一张这样的图片](https://zhuanlan.zhihu.com/p/24533452)。我用的是[wordart.com](https://wordart.com/)，超级好用！目前只支持英文，想使用中文等可以查看上面链接里的推荐。

#### 功能完善，基本满足了一个强迫症的要求
* WORDS: 直接粘贴或输入网址，可以去除数字和常用单词（估计是一些虚词）
+ SHAPES: 输入自己想要的图片模板，比如专辑封面
- FONTS: 40多种英文字体
* LAYOUT: 单词横纵斜组合布局
+ STYLE: 字体颜色+背景颜色，可以自己输如16进制颜色码（eg. #1DC8DC）

网站操作很友好，建议直接上手试试~
![](https://viciayuan.github.io/images/1712/wordart.png)

#### 彩蛋——在线取色器
由于需求不仅在于爬虫做词云，而在于做成专辑风格的词云。
可以使用在线取色器网站（[推荐这个](http://www.jiniannet.com/Page/allcolor)），提取对应图片所有颜色的16进制颜色码，可以直接用在WordArt网站设置背景和字体颜色。在上面提到的SHAPES选项使用专辑封面的图片，STYLE使用这里提取的颜色码，最后生成的就是专辑风格的歌词词云啦。

![](https://viciayuan.github.io/images/1712/color.png)<br>
### 结果展示
其实我最感兴趣的部分结果分析，真想过度解读一番。解读一下歌词中出现最多单词与专辑风格、作者感情流露的关系。（假装是为了分析而作图，不是为了作图而作图）

还是先放图吧。最喜欢的两张图Ed Sheeran的除号和Taylor最新专辑Reputation，最喜欢只因做出来效果太好了。
![](https://viciayuan.github.io/images/1712/wordart.jpg)

1989背景太杂，换了图代替，RED也换了一张与专辑封面风格一致的字母图代替，[查看其他LyriCloud图片](https://github.com/ViciaYuan/LyriCloud/tree/master/cloud_img)。
最常出现的单词可能与某一首歌反复的一句话有关，比如Taylor的暗黑系"oh look what you made me do"无限循环。除了这种强行加戏的情况，观察稍多的，也有new,up, wish, know, love, good, trust, dance, better这些美好的词出现。
<br>
很感谢大神同学的commits，感觉一个人写不知道啥时候碰到问题就放弃了...最近一周依旧被植物社的事烦得要死，周三收到加拿大暑研offer，也没激动太久，心怀感激，继续前进，talk is cheap, show me the commits. Thank you for giving me purpose.
不急不懒，静水流深，每天都有新的激励。

<script>
<%- toc(page.content, {
        class: 'post-toc',
        list_number: true
    }) %>
</script>

<div id="container"></div>
<link rel="stylesheet" href="https://imsun.github.io/gitment/style/default.css">
<script src="https://imsun.github.io/gitment/dist/gitment.browser.js"></script>
<script>

var gitment = new Gitment({
  //sid: '页面 ID', // 可选。默认为 location.href
  owner: 'ViciaYuan',
  repo: 'viciayuan.github.io',
  oauth: {
    client_id: '0edc885787509e0eadc7',
    client_secret: '935379f53bf779fb6445d4341c9076418938c761',
  },
})
gitment.render('container')
</script>
