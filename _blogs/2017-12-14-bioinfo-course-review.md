---
title: 生物信息学软件推荐/课程总结
date: 2017-12-21 13:55:00
tags: 
- bioinfo
categories:
- bioinfo
---
常用生物信息学网站/软件总结，以及总结一下这学期bioinfo课学了啥。
<!-- more -->

写在前面：这是一篇课程笔记，对这学期的生物信息学课程主要内容做了大致的总结。由于是给本科三年级计算生物学专业学生开设，这门课内容可能会比较基础，写笔记在这里也是希望对同在入门的同学有所帮助。详略程度很受我自己的影响，不清楚的地方可以自行深入了解orz..也欢迎补充、指正、交流。

总的来说这学期的生物信息学课内容详略得当、作业合理，可能以后更多和具体项目结合会更好。这篇文章会简单总结一下生物信息学一些大方向的概要笔记、和一些常用网站/软件资源。可以先收藏老师的这个汇总网站再看下面的总结↓↓↓

[LabShare 生物信息学在线软件集锦](http://www.labshare.cn/biosoft/index.html)

在查资料过程偶遇北大Applied Bioinfomatics Course的课程网站,很多学习资源和总结，可以看看 [网站链接](http://abc.cbi.pku.edu.cn/index.php)
<br>
<!--2-->
# 数据库资源 

几个常用生物数据库，前三个是最基础常用的。
1. 核酸序列数据库[GenBank](https://www.ncbi.nlm.nih.gov/genbank/)
2. 蛋白序列数据库[UniProt](http://www.uniprot.org/) 
3. 生物大分子三维结构数据库[PDB](http://www.pdb.org) 
<!--12万的数据，不是特别多，折叠模式一两千，很有限-->
4. 蛋白质结构数据库[SCOP](http://scop.mrc-lmb.cam.ac.uk/scop/search.cgi)
5. 基因芯片数据库[GEO](https://www.ncbi.nlm.nih.gov/geo/) 
6. 肿瘤基因图谱数据库[TCGA](https://cancergenome.nih.gov/)

__GenBank__
- GenBank与欧洲[EMBL](https://www.ebi.ac.uk/ena)、 日本[DDBJ](http://www.ddbj.nig.ac.jp/)建立了交换数据的合作关系
- 分类：高通量基因组序列（HTG）、表达序列标记（EST）、序列标记位点（STS）、基因组概览序列（GSS）
- 内容：将一条序列相关的各种信息，按一定的结构，以文本文件(text file)的形式组织在一起，构成一个GenBank record (entry)

__Universal Protein Knowledgebase(UniProt)__
- Swiss-Prot， TrEMBL 和 PIR 三大数据库组合
- UniProtKB/Swiss-Prot：检查过的、手工注释的条目;UniProtKB/TrEMBL:未校验的、自动注释的条目

__Protein Data Bank(PDB)__
- 搜索方式：PDB id、文本、针对特定领域的数据库

<!--3 4 5,6-->
<br>
# 序列比对 

从序列的相似性推测同源性，进而得到关于结构、功能和进化的关系。这里要注意同源性是生物学上关系的描述，而相似性是针对数据本身差异的描述，相似并不一定说明同源。

那么是选取蛋白质的序列还是DNA的序列作比对呢？一般从进化意义上分析,蛋白比对比核苷酸更可取，蛋白序列比核苷酸序列可以追溯更久的历史，其次，分析蛋白质的序列忽略了密码子简并性，得到结果更反映进化关系。


比对序列之前，首先要评估不同氨基酸的相似性。常用评估相似性方法：PAM矩阵和BLOSUM矩阵
<!--基于统计的数据，反推概率-->
- PAM矩阵(Point Accepted Mutation)：由最初一个数据库得到的氨基酸两两突变频率表
- BLOSUM矩阵：蛋白质序列高度保守部分比对得到，是现在很多软件的首选

使用区别
- PAM-n的n越小，表氨基酸变异可能性小，小n适合更相似的序列之间使用
- BLOSUM-n的n越小，表氨基酸相似可能性小，小n适合不太相似的序列之间使用

<!--概率矩阵乘法,外推远缘概率值PAM1>>PAM250 啥意思-->
关于序列比对算法，都采用了动态规划的思想
- 全局：Needleman-Wunsch算法，序列头尾空位都要罚分
- 局部：Smith-Waterman算法，只关注局部

（这学期有个选做作业就是实现Needleman-Wunsch算法）

## Blast (Basic Local Alignment Search Tool)
Blast是寻找序列局部相似性的算法，另有一个很老的算法叫FASTA，针对全局的序列比对。Blast在双序列比对中有很广的应用，[NCBI Blast](https://blast.ncbi.nlm.nih.gov/Blast.cgi)和[Uniprot Blast](http://www.uniprot.org/blast/)都提供了在线的使用。除此之外，双序列比对算法也有基于隐马尔科夫模型的[HMMER](https://www.ebi.ac.uk/Tools/hmmer/search/phmmer)和[HHblits](https://toolkit.tuebingen.mpg.de/hhblits)，速度更快。

前面提到序列之间的相似性只能推测其同源性，Blast的统计学显著性由E-value评估，E值越小，结果越有意义。有一些经验规则，如E值小于 0.01的序列可以认定为同源序列。

<!--Blast针对局部，FASTA全局-->
Blast搜索结果的应对策略
- 结果过多：合适的数据库、限定种属、各结构域单独搜索、调整评分矩阵、调整E值阈值
- 结果过少：不同的数据库、取消种属限制、使用n小的BLOSUM矩阵或n大的PAM矩阵、提高E值、PSI-BLAST或HMMs(隐马模型)等更敏感的办法

PSI-BLAST (Position-Specific Iterated Blast) 用于发现相似性低但可能存在生物学联系的相关蛋白。原理是：每次进行多序列比对后建立一个位置特异性矩阵(PSSM), 然后利用这个矩阵在数据库进行搜索，评估结果的统计学显著性，再根据搜索结果更新PSSM，不断循环，最终得出结果。

除了PSI-Blast，另一种缩写很像但完全不一样的PHI-BLAST (Pattern-Hit Initiated Blast) 算法可以按一定的序列模式进行搜索，Pattern的语法规则[pattern syntax](https://www.ncbi.nlm.nih.gov/blast/html/PHIsyntax.html)，序列特征参考[PRINTS](http://www.bioinf.man.ac.uk/dbbrowser/PRINTS/),[PROSITE](https://prosite.expasy.org/).

## 多序列比对(multi-sequence alignment)

多序列比对用于找出 __一组序列__ 中的保守片段，以便进行结构、功能、进化方面的分析。与双序列比对不同，多序列比对照顾不到每两个序列比对结果，只能尽量使相似的地方出现在相同位置；并且结果无对错之分，我们只能评价这个结果是否合理。
<!--这里弄一张表格 ppt6 -->
多序列比对的方法
- 手工比对（先Needleman-Wunsch动态规划两两比对，再肉眼观察对齐一些关键性残基）
- 同步法（扩展二维动态规划矩阵到多维，将所有序列同时比对，计算量大，适合少量短序列）
- 步进法（先Needleman算法两两比对，选出一对最相近序列作为基准，将和两条基准序列最相近的第三条序列加进去一起对齐，如果有空位则遵循“once a gap, always a ap”原则，陆续加入其他序列直到全部完成）

步进法的代表为[ClustalW](http://www.clustal.org/)，现在已发展为Clustal Omega。除了ClustalW，也有其他具有不同特点的软件，如MUSCLE, MAFFT,Cobalt,PRALINE, ProbCons, T-Coffee, Expresso, M-coffee等，这是[omictools](https://omictools.com/multiple-sequence-alignment-category)网站列出的相关软件，[wiki](https://en.wikipedia.org/wiki/List_of_sequence_alignment_software)上也列出的双序列和多序列比对算法及其特点，可以大致看看。
<!--先两两比对，得到初始consensus序列，其他再和这个比较-->

多序列比对在序列相似程度较低的时候准确性会明显下降。确定结果是否准确可以看：蛋白质保守的残基、motif、二级结构偏好和一些区域恒定的插入删除模式。

多序列比对结果的形象显示工具——[Squence Logo](http://weblogo.berkeley.edu/logo.cgi)
<br>
# 进化树构建

研究生物进化的一个重要途径就是对于生物大分子的比较，根据分子进化速率恒定（中性理论）、不同物种同源大分子的进化速率大致相同（分子钟理论）等，可通过不同物种同源大分子的比较，确定物种间亲缘关系、分支时间、构建系统进化树。

这一部分推荐文章开头提到应用生物信息课程的一个[分子系统发育分析课件](http://abc.cbi.pku.edu.cn/talk/phylogeny-yang-q.pdf)

## 分子进化树的构建

方法有：
- 距离法（UPGMA, Minimal Evolution, Neighbor-Joining）
- 最大简约法 （Maximum parsimony，MP）
- 最大似然法 （Maximum likelihood，ML）
- 贝叶斯推断 （Bayesian）

建立分子进化树之后一定要进行可靠性检验，常用方法为bootstrap法，一般认为Bootstrap值>70时，进化树可信。对比较序列上的替换位点作多次随机取样，根据每次取样的数
据可以得到新的树形图，相同的组合出现在某一个节点上的次数占总取样次数的百分比就是该节点的bootstrap值。另外的进化树可信度检验方法还有Delete-half-jackknifing, Permuting species within characters

常用绘制进化树的软件：
- [PHYLIP](http://evolution.genetics.washington.edu/phylip.html) (Phylogenetic Inference Package)
- [Mega](http://www.megasoftware.net/mega4/) (Molecular Evolutionary Genetics Analysis)
- [PAUP](http://paup.sc.fsu.edu/about.html) (Phylogenetic Analysis Using Parsimony)
- [PAML](http://web.mit.edu/6.891/www/lab/paml.html) (Phylogenetic Analysis by Maximum Likelihood) 


## 分子进化的局限

分子进化和物种进化也是有区别的，使用分子进化推测物种进化会存在一些问题。
- 单个分子代表整个物种的片面性问题
- 基因横向迁移(Lateral Gene Transfer)的问题
- 基因重复(gene duplication)使难以区分直系或旁系同源的问题
- 方法本身没有考虑多次突变、回复突变的问题

用一个特征分子代表一个物种的方法受到了质疑，且生命出现早期基因横向迁移的现象也使进化树成网状而不是单纯的二叉树。也有人提出基于共有基因含量的进化树构建（nature genetics,1999）。两个基因组之间的共同基因的数量与它们的进化距离相关，以此来推断两个物种间的相似性。

<!--基本思想
具体步骤
算法很多
都要做可信度检验（默认）判断可靠不可靠
bootstrap选样是否有可靠性，70%为可靠
常用软件
Mega
PHILIP-->
<br>
<!--10-->
# 蛋白质三维结构分析与预测 

通常使用均方根偏差RMSD(root mean square deviation)作为两种或更多种蛋白质结构之间相似性的定量度量。RMSD通常是骨架原子之间平均距离的量度，单位是埃，RMSD越低，模型与目标结构相比越好。RMSD小于2埃时表示结构很相似，大于6.5埃表示拓扑结构不同。
<!--插入一个公式？-->

结构比对的网站：1.RCSB PDB[Sequence & Structure Alignment](https://www.rcsb.org/pdb/secondary.do?p=v2/secondary/analyze.jsp#Sequence), 2.[StructureAlign by Dr. Cao](http://cao.labshare.cn/Tools/structurealign.php)
蛋白质三维结构预测一直是个有重要意义并受到很多关注的领域，并有专门且持续的比赛[CASP](https://en.wikipedia.org/wiki/CASP)

蛋白质三维结构预测的主要办法有基于模板的结构预测（同源建模、折叠识别）,不依赖模板的结构预测（从头计算）。按常用顺序依次是同源建模、折叠识别、从头计算，实在找不到模板了才会从头计算。

<!--
结构比对
蛋白质三维结构预测的主要办法
基于模板的结构预测：同源建模和折叠识别,不依赖模板的结构预测：从头计算
能量（结构是否合理）
搜索算法（旋转角的数据）
找不到模板再重头计算（重要！！）
-->

## 同源建模 Homology modeling

八个步骤 比对->建模->修正 （这段大家感受一下思想和流程...总结得可能不准确）

1. Template recognition and initial alignment
PDB里Blast寻找匹配程度最高的，作为模板
2. Alignment correction
修正功能性的残基、删除位点等，使用多序列比对
3. Backbone generation
使用模板产生主干的模型，按上面判断删除位点、保留保守残基
4. Loop modeling
条带连接部分的loop选择后匹配
5. Sidechain modeling 
侧链角度的匹配
6. Model optimization 
分子动力学模拟使结构能量最低，全局优化
7. Model validation 
检验phi角等来确认模型是否合理，网站[ProCheck](http://www.biochem.ucl.ac.uk/~roman/procheck/procheck.html), [WhatIf server](http://swift.cmbi.kun.nl/WIWWWI//)
8. Iteration
从错误的步骤重新开始，不断循环直至得到目标结构

推荐软件
- [Modeller](https://salilab.org/modeller/)
- [SWISS MODEL](https://swissmodel.expasy.org/)


## 折叠识别 Fold Recognition/Threading
<!--maybe a graph-->
基于蛋白折叠模式来预测，例子是这个

[I-TASSER](https://zhanglab.ccmb.med.umich.edu/I-TASSER/) (Iterative Threading ASSEmbly Refinement)

## 从头计算 Ab initio/de novo prediction

已知结构的片段建库，与蛋白序列对应，组装这些亚结构的单元，可以预测新的结构。例子是这个

[QUARK](https://zhanglab.ccmb.med.umich.edu/QUARK/):Ab initio structure prediction method

<!--片段装配-->

<br>
<!--11-->
# 分子对接与虚拟筛选 

分子对接即预测受体和配体分子形成的复合物结构，分为两类：蛋白和蛋白、蛋白和小分子。两者结合特征不同，蛋白和小分子结合面很小，有结合口袋binding pocket，结合准确性高，这里主要讨论蛋白与小分子结合。

找出空穴，定出表面
- [Q-SiteFinder](http://www.modelling.leeds.ac.uk/qsitefinder)
- [SiteHound](http://scbx.mssm.edu/sitehound/sitehound-web/Input.html)

代表性对接软件
有很多 Flex X, LigandFit, Glide, Gold, AutoDock, Dock, ICM-Dock, Fred(open eye) etc. Autodock Vina的[网站](http://vina.scripps.edu/)

分子对接计算的需要注意的地方也需从小分子、蛋白质和对接三方面来考虑。

## 药物设计与发现
分子对接对于药物靶点的发现十分重要，现代药物开发多从疾病入手，用疾病模型去寻找可能的药物靶点。高通量药物筛选（High throughput screen,HTS）技术便是生物信息应用到这一领域的技术。曾在生命科学联合中心暑期班通过清华药学院一位老师讲他们实验室做的相关成果，有时间再来这里补充一下。

## 虚拟筛选
指的是从大量的化合物中经过筛选，找出与靶标分子结合的最佳分子，得到一个合理大小的化合物库，然后仅对这些适合成药的化合物购买、合成或分离得到，然后再进行实际的生物测试。


<br>
# 蛋白质设计
蛋白质设计是蛋白质三维结构预测的逆问题，即已知结构，找到能折叠成这个结构的氨基酸序列。蛋白质设计的一些例子有：蛋白间相互作用的设计、酶催化反应的设计、HIV疫苗等。（此处略去很多老师给的例子...）

可以看看这个建模和分析蛋白结构的软件[Rosetta software suite](https://www.rosettacommons.org/software)
蛋白质设计存在的困难在于打分函数、搜索算法和应用这三方面。
<!--
存在的问题，困难和解决
-->

<br>
# 生物芯片分析 

基因芯片的数据分析有以下几类：
1. 差异表达分析
使用标准的统计学方法检验 (t-test)，发现统计显著性差异表达的基因
1. 基因共表达分析 
在N个不同的条件下 (时间序列的芯片数据)，考察基因X和Y的表达是否相似
1. 表达数据的聚类
将表达谱相似的基因聚类在一起
1. 与GO数据库关联分析
<!--注释库-->
1. 基因调控网络

几个没细看的数据库：[Gene Expression Omnibus-NCBI](https://www.ncbi.nlm.nih.gov/geo/);[ArrayExpress-EMBL](https://www.ebi.ac.uk/arrayexpress/);[用不了的的Stanford Microarray Database](http://smd.princeton.edu/)
<br>
# 基因结构分析 

一些常用软件（emmm因为懒所以这里就不附上超链接了）
1. 识别基因  GENSCAN;GENOMESCAN
1. CpG岛  CpGPlot
1. 启动子/转录起始位点  PromoterScan
1. 转录终止信号  POLYAH
1. 密码子偏好分析  CodonW
1. mRNA剪切位点  NETGENE2；Spidey
1. 选择性剪切  ASTD

<!-- 识别基因
GpG岛
-->

<br>
如果发现我后面写的都很简略...一部分原因是后面的结构相关没有特别感兴趣，所以没有认真听，当然除了前面写的最详细的序列比对进化分析，后面的也很重要。希望这篇笔记能有所帮助，欢迎大家指正和补充orz

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
