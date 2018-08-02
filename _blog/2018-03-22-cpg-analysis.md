---
title: 叶绿体基因组的组装、注释、修正和提交
date: 2018-03-22 23:48:17
tags:
- bioinfo
categories:
- bioinfo
---
一个入门生物信息学的绝佳实践。
<!-- more -->

之所以属这个项目是绝佳实践是因为：

1. 涉及基因组组装、注释的基本操作，可以顺便了解一下相关算法
2. 叶绿体基因组一般比较小（100-200kb），测序的原始数据也不大，可以用少量体会高通量测序的流程
3. 周期也比较短，可以比较快地体会整套流程
4. 最后可将结果提交到NCBI GENBANK，小白也可以贡献一点数据

<br>

## 背景知识与说明

[Readme on Github](https://github.com/imengyuan/Bioinfo-pipelines/tree/master/cpg-analysis)

<br>


## 分析流程和脚本

[旧脚本的详细解释](https://github.com/imengyuan/Bioinfo-pipelines/blob/master/cpg-analysis/get-chloroplast-genome.md)


[新脚本有每步输入和输出](https://github.com/imengyuan/Bioinfo-pipelines/blob/master/cpg-analysis/get-chloroplast-genome-new.md)

<br>

## geneious的使用 
[use-geneious](https://github.com/imengyuan/Bioinfo-pipelines/blob/master/cpg-analysis/use-geneious.md)

geneious是一个多功能的生物信息学分析软件，文件的可视化很棒，可以直接在序列上修改。但它也是要钱的，实验室买了license，但在自己电脑上用就只有14天的免费试用期，用完了试用期就只有...
~~找破解版~~ 可以试下在虚拟机上装，还支持反复装，强烈推荐！

<br>

## PCR和一代测序
[use-PCR](https://github.com/imengyuan/Bioinfo-pipelines/blob/master/cpg-analysis/use-PCR.md)

PCR手动补洞这个步骤其实是可选的，但..这个小项目对小白还有个好处在于除了有用软件跑流程，还包括了做分子实验。emmm还是很贴心的。












