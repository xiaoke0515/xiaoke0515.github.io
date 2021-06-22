---
layout: post
title: 基于 ReRAM 的神经网络加速器综述（一）——介绍
date:   2021-03-24 22:02:00 +0800
categories: 
    - "基于 ReRAM 的 DNN 加速器"
description: some word here
keywords: ReRAM, DNN, Review
---

筹划了一段时间，终于开始写这个综述了。也算是对研究生阶段研究的东西做个总结吧。
这个综述将聚焦于基于 ReRAM 的存算一体的 DNN 加速器设计。

## 存算一体（ PIM ）

存算一体（ Process-in-Memory, PIM ； 也有称为 Compute-in-Memory 或 In-Memory-Computing 的，但都是一个东西）是一个比较“古老”的概念了。
在这里我们就简单定性地介绍一下这个 PIM [^pim]。

在介绍 PIM 之前要提一下冯$\cdot$诺依曼架构，也就是现在普遍应用的架构，的一个特点。
这个特点就是存储和计算单元是分离的。
也就是说在计算时要先将数据从存储器中读取到计算单元中，再由计算单元执行计算。
这样就会产生数据读写和搬移的功耗。
目前的大部分的 workload 都是计算密集（ CPU Bound ）的，即计算量远大于存储的读写量，因此体现不出这个数据搬移带来的开销的影响。
但是，随着深度神经网络（ Deep-Neural-Network ， DNN ）的崛起，情况开始变得不同了。
DNN 中存在大量的矩阵运算，而矩阵运算是存储密集的（ Memory Bound ），因此数据搬移的的开销就成为了一个问题。

PIM ，顾名思义，就是直接在存储器内执行计算。
这样就省去了数据搬移的开销。
目前我了解的 PIM 有如下几种路径：

1. 近存计算

    近存计算就是在存储器旁边直接放置计算电路。
    这样数据就不用搬到计算单元中计算，就直接在存储器旁边计算。
    这种方式实现非常简单，直接在 FPGA 上实现就可以，也没什么人去研究。

1. 基于 SRAM 、 DRAM 等已知器件的存内计算

    这一类方法开发了这些存储器件的计算潜力。
    比如，直接在字线上进行电荷共享[^3CSRAM]、逻辑计算[^TCAM] [^DrAcc]，或在 cell 内执行多比特相乘[^Conv-RAM]。

1. 基于新器件的存内计算

    这个方式是利用一些新兴的阻性器件构成的阵列来计算，其中就包括了本文的主角——ReRAM。

[^pim]: online: [https://zhuanlan.zhihu.com/p/98912754](https://zhuanlan.zhihu.com/p/98912754)
[^3CSRAM]: Z. Jiang, S. Yin, J. Seo, and M. Seok, "[C3SRAM: In-Memory-Computing SRAM Macro Based on Capacitive-Coupling Computing](https://ieeexplore.ieee.org/abstract/document/8877969/)," IEEE Solid-State Circuits Letters, vol. 2, no. 9, pp. 131-134, 2019, doi: 10.1109/LSSC.2019.2934831.
[^TCAM]: S. Jeloka, N. B. Akesh, D. Sylvester, and D. Blaauw, "[A 28 nm Configurable Memory (TCAM/BCAM/SRAM) Using Push-Rule 6T Bit Cell Enabling Logic-in-Memory](https://ieeexplore.ieee.org/document/7400984/)," IEEE Journal of Solid-State Circuits, vol. 51, no. 4, pp. 1009-1021, 2016-04-01 2016, doi: 10.1109/jssc.2016.2515510.
[^DrAcc]: Q. Deng, L. Jiang, Y. Zhang, M. Zhang, and J. Yang, "[DrAcc: a DRAM based Accelerator for Accurate CNN Inference](https://dl.acm.org/doi/abs/10.1145/3195970.3196029)," in 2018 55th ACM/ESDA/IEEE Design Automation Conference (DAC), 24-28 June 2018 2018, vol. 77, no. DRAM  PIM, p. 6, doi: 10.1109/DAC.2018.8465866. 
[^Conv-RAM]:  A. Biswas and A. P. Chandrakasan, "[Conv-RAM: An energy-efficient SRAM with embedded convolution computation for low-power CNN-based machine learning applications](https://ieeexplore.ieee.org/abstract/document/8310397/)," in 2018 IEEE International Solid - State Circuits Conference - (ISSCC), 11-15 Feb. 2018 2018, pp. 488-490, doi: 10.1109/ISSCC.2018.8310397. 