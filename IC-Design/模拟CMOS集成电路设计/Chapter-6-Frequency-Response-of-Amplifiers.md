---
title: Chapter 6 Frequency Response of Amplifiers
date:  20200228 17:23:15
categories: 模拟CMOS集成电路设计
tags: 
 - 读书笔记
mathjax: true
---

## 章节介绍

我们前面面是在考虑较低频率的情况下，忽略器件及负载电容。但其实速度还是会与各种寄生参数互斥的，比如增益，功率损耗，噪声。因此我们有必要知道每种电路的频率响应限制。

本章我们学习一阶以及差分放大器的频域行为表述，我们学习共源级、共门级，源跟随（source flower）。然后是串联（cascode）以及差分放大器。最后，我们考虑差分对中，有源电流镜对频率响应的影响。

**关于不同stage的连接方法：** common-source and common-gate stages and source followers分别是怎样的电路？如下图：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.4&#32;common-source&#32;stage.png" width = "60%" height = "60%" alt="common-source" align=center />
</div>

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.48&#32;common-gate&#32;stage.png" width = "60%" height = "60%" alt="common-gate" align=center />
</div>

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.34&#32;source&#32;follower.png" width = "60%" height = "60%" alt="source followers" align=center />
</div>

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.59&#32;cascode&#32;stage&#32;.png" width = "60%" height = "60%" alt="cascode stage" align=center />
</div>

## General Considerations

## The End
