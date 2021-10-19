---
layout: post
title: 基于 ReRAM 的神经网络加速器综述（二）——早期的加速器
date:   2021-08-03 09:52:00 +0800
categories: 
    - "基于 ReRAM 的 DNN 加速器"
description: some word here
keywords: ReRAM, DNN, Review
---


上一章链接：
[基于 ReRAM 的神经网络加速器综述（一）——介绍]({{"/2021/03/24/3_ReRAM_DNN_Review_1/" | absolute_url}})

上一章我们讲了 ReRAM 做矩阵乘法的基本原理以及高精度的向量-矩阵乘的电路。
接下来我们将介绍早期的基于这个原理的神经网络加速器的设计。

## PRIME

PRIME [^PRIME] 加速器是 2016 年 ISCA 上的文章。
那个时候 ReRAM 还是个新事物，大家对它的期望还很高，因此思路还是存和算的结合。

从整体架构上来看，如下图所示。
ReRAM 存储器被分为三个部分，分别用作 memory ， buffer 和 FF 。
其中， FF 就是用来做向量-矩阵乘的部分，同时它也可以用作存储。
那个时候 ReRAM 的寿命问题还没有那么多人讨论，还可以用作需要频繁擦写的存储器。

<img src="/img/ReRAM_DNN_accelerator/4_figure_prime_overview.jpg" alt="TE" width="400" align="bottom" />

下图是 FF bank 的一个架构图，它设计了完整的周边电路来支持神经网络的计算。


<img src="/img/ReRAM_DNN_accelerator/4_figure_prime_architecture.jpg" alt="TE" width="800" align="bottom" />




[^PRIME]: P. Chi et al., "PRIME: A Novel Processing-in-memory Architecture for Neural Network Computation in ReRAM-based Main Memory," presented at the 2016 ACM/IEEE 43rd Annual International Symposium on Computer Architecture (ISCA), 2016, 27.
