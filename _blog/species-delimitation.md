---
title: Species delimitation review 物种界定综述（一）
date: 2017-12-03 19:51:14
tags: 
- speciation
- species delimitation
- molecular evolution
categories:
- species concepts
---
深入了解物种概念，物种界定综述笔记分享。
<!-- more -->
这学期的分子生态学课程，没有考试，要求选一篇文献进行翻译。于是愉快地选择了感兴趣的“DNA条形码和物种界定”方向的综述。选综述一时爽，翻译......边读边学习了很多分子进化的东西，试着做一个分享。

对物种的概念感兴趣的同学欢迎直接下载原论文来读，本文提供的只是一些背景补充、概要和总结。还有很多不全面、不深入或者有错误的地方，欢迎指正。


<!--要把引言的一些东西加进来。-->
#### 物种界定的七层面纱

在过去几十年，DNA序列在探讨近源物种的关系、确定物种年代、界定物种有很多应用。这通常是基于一些适合科以上分类阶元的进化假设，但在物种层面可能无效。在过去，物种层面上这种无效的假说被每个物种只用很少的样品、序列分析仅来自一个基因组/基因座所掩盖。

最近，群体遗传学在物种等级上被应用于谱系地理学、DNA条形码技术，导致了研究者们对这种错误假设被用在物种及以上等级的担忧。这两个领域都发现了一些能模糊系统发育信号的过程。DNA条形码技术除了引发争议，也复兴了关于物种概念、物种界限和物种发现的讨论。

这里补充一个概念叫分类学复杂群体(taxonomically complex groups,TCG)，大致意思是分类困难的复杂群体，比如存在混合群hybrid swarm的群体（至于混合群又是啥，看我后面背景知识补充吧...）。在TCG中，尤其是形态学、倍性（是几倍体）、谱系地理模式、种群动态和繁殖之间的相互作用，对基于少数基因/样本数的一些假说去捕捉，或许过于复杂。如果物种有一个清楚的信号用于界定，那是再好不过，但是这种信号在物种层面很少能被找到，甚至比分类学复杂群体更简单的群体，这种情况也没找到。

然后文章主要鉴定了七种在没有正确认识时，能够模糊物种界限和关系的过程（即七层面纱），包括：

1. Intergenomic transfers 基因组间转移
2. Hybridization 杂交
3. Incomplete lineage sorting 不完整谱系分选
4. Genome organisation 基因组结构
5. Demography 种群动态
6. Selection 自然选择
7. Phylogeographic structure 谱系地理学结构

这几个过程有的比较熟悉，比如杂交、种群动态、基因组结构和自然选择，虽没有深入研究，各种课程多有涉及。也有不太熟悉的，比如基因组间转移（质体、线粒体的DNA转移到核基因组）、不完整谱系分选（涉及溯祖理论、谱系分选的随机性）和谱系地理学结构（研究谱系的地理格局变化）。不管是熟悉还是不熟悉的过程，读罢文章又多了许多新的理解。


#### 错误猜测的影响
这七个过程对有效种群大小有直接影响，有效种群大小Ne是个很重要的参数，群体遗传学的研究多据此展开。没有将上述七个过程考虑到，而用了一些错误猜测，得出不准确的结论会存在于以下方面：

1. 用序列数据鉴定标本
1. 物种界定(delimitation)
1. 物种聚类(cluster)的系统发育关系
1. 物种确定年代(dating)


#### 给物种界定研究的建议
作者认为这些问题可以被识别并且在某种程度上减少他们的影响。下面四个方法可以揭露遗传数据的问题，避免误导的信号。

1. 每一个物种应该用多个个体来表示，覆盖不同的倍型（如果有的话）以及物种的地理和生态学范围；
1. 对每一个样品，数据应尽可能来自更多的基因组和基因座；
1. 所有基因座被当做单独的数据，因为级联（concatenation）更可能导致物种树错误；
1. 在任何研究近源物种或姐妹物种时，都应使用溯祖(coalescence)的框架。


#### 背景理论 /知识补充
这里先补充一些重要的理论或概念，方便理解上面的一些内容，也为下一篇介绍七个过程的文章补一些背景。（此处先挖坑再填坑）
<!--补充一些常用的，和部分来自appendix的-->

![](https://viciayuan.github.io/images/171203/coalescence.png)
溯祖

有效种群大小Ne
种群大小N
多物种溯祖模型
不完全谱系分选
谱系地理学
单系分支物种
基因座
倍性
TCG
选择扫荡
...

<!--看这里需不需要提一下结论，主要上面提的内容太少了-->
#### 小结
如果你真的读到了这里并且对于物种概念和物种界定感兴趣的话，建议下载原论文阅读。 并且欢迎参考我的下一篇笔记，了解导致物种界定困难的七个过程。

论文地址：[Species delimitation and relationships: The dance of the seven veils](http://www.plantevolution.org/jc/Naciri2015.pdf)
下一篇笔记：[Species delimilation review 物种界定综述（二）](https://viciayuan.github.io/2017/12/14/species-delimitation-7-veils/#more)

<!--Comment Area Here-->
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