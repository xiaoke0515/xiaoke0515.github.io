---
layout: post
title: "神经网络二阶优化总结"
date:   2021-02-25 19:43:00 +0800
categories: "optimal_algorithm"
description: 这里总结了神经网络的一些二阶优化算法
keywords: ["Neural Network", "second order optimal"]
---

最近在看神经网络的二阶优化，总结一下看过的现有技术。
从牛顿法到自然梯度法，再到现在的 Mindspore框架。
在这里写的多为思想上的一些总结，技术细节引用了一些文章和博客。

# 牛顿法

## 基础算法：牛顿法
**牛顿法**是一个比较传统的二阶优化方法，具体细节与推导可以参考一些教材 [^sun_optimal]。
由于在对参数更新时参考了二阶的梯度，因此相比于一阶优化算法，可以更快地找到梯度下降的方向。
牛顿法的梯度下降更新公式为：
<span id="eqn:1">\begin{equation}
    w_{k+1}=w_k+\alpha H_k^{-1} \nabla_w J_{k} \tag{1}
    \label{eqn:1}
\end{equation}</span>
其中， $w$ 为权值， $H$ 代表 Hessian 矩阵（二阶梯度）， $J$ 为Jacobian 矩阵（一阶梯度）， 角标 $k$ 表示迭代的次数。
$\alpha$ 用于调节步长，也就是说，这个公式实际上已经是牛顿法的一个衍生算法，即**带步长的牛顿法**。
这是由于对于非二阶凸优化问题，原始的牛顿法不一定能直接到位，故由牛顿法得到优化方向，再另外设置步长。
由于本文就针对的就是非二阶优化问题，因此在本文中我们就以这种带步长的牛顿法为基础算法进行讨论。


牛顿法在实际应用时有一个重大缺陷，就是计算复杂度太大。
这个问题就出在表示二阶梯度的 Hessian 矩阵上。
问题可以总结为以下三点：

1. 问题一： Hessian 矩阵大小过大

    根据 Hessian 阵的定义我们可以知道， Hessian 阵的大小为参数量的平方。
    以一个比较常见的神经网络 ResNet-50 为例， 它的参数量大概在 25MB 左右（这个数我只是简单搜了一下，具体多少待考证），那么对应的 Hessian 阵的大小就是 5PB 。
    这个参数量别说 GPU ，硬盘都放不下。

1. 问题二： Hessian 矩阵求逆困难

    这个问题有一部分原因是 Hessian 矩阵过大，然而矩阵求逆本身就是一个费计算资源的操作。
    无论是一些分解算法（如 SVG 分解），还是利用优化方法迭代，都需要大量计算。
    好在 Hessian 矩阵是一个对称方阵，但这似乎也不会改善任何现状。

1. 问题三： 神经网络的 Hessian 矩阵本身求解困难

    一阶的 Jacobian 矩阵可以利用反向传播的方式求解，但二阶的 Hessian 矩阵就困难了。
    这是因为 Jacobian 矩阵在不同层之间是无关的，而 Hessian 不同。
    因此在计算 Hessian 阵时，只能以一个奇怪的顺序来传播 [^Mizutani_second]。
    如果说一阶的 Jacobian 矩阵的反向传播的顺序是以一个一维的轴从右向左计算，那么二阶的 Hessian 矩阵的反向传播就是二维的平面从右下到左上传播。
    此外，传播过程中计算 Hessian 阵的复杂程度远超 Jacobian 矩阵。

## 拟牛顿法

现有的拟牛顿法主要有两种，分别为 **DFP 法**和 **BFGS 法**。
两种方法也是传统的方法了，针对的就是后两个问题，作了如下优化[^sun_optimal]：
1. 不直接求解 Hessian 阵，而是在每次迭代过程中估计一个新老 Hessian 阵的差值 $\Delta \hat{H}\_{k}\approx \Delta H_k=H_{k+1}-H_k$ 。
1. 假定这个差值矩阵估计值 $\Delta \hat{H}\_{k}$ 的秩为 2 。

在这里我们在 $\Delta H_k$ 上加一个 $\hat{\cdot}$ 符号来表示它是一个估计值。
那么如何估计这个 $\Delta \hat{H}\_k$ 呢，这就要提到**拟牛顿条件**了。
这里简单说一下拟牛顿条件是怎么来的。
从公式 [$(1)$](#eqn:1) 的基础上，我们定义， $s_k=w_{k+1}-w_k$ ， $y_k=\nabla_w J_{k+1}-\nabla_w J_{k}$ ， $B_k=H_k^{-1}$  。
我们认为 $H_k$ 的变化是缓慢的（做了一个近似），因此可以得到拟牛顿条件的公式：
<span id="eqn:2">\begin{equation}
    y_k=B_{k+1}\cdot s_k \tag{2}
\end{equation}</span>
我们认为 $H_k$ 只要满足拟牛顿条件，误差就可以接受。
在此基础上我们可以得到 DFP 法和 BFGS 法的公式，具体推导可以参考引用的博文 [^BFGS] ：

这样就可以减少计算 Hessian 阵的复杂度，且摆脱了求逆的困扰。
其中， DFP 法直接在 Hessian 阵的逆阵上更新秩 2 矩阵， BFGS 在 Hessian 阵上更新秩 2 矩阵。
由于 DFP 算法在收敛性证明上缺失，且在数值上有缺陷，因此 BFGS 应用更广泛 [^DFP_fault]。

BFGS 算法依旧面临着 Hessian 矩阵过大的问题，因此衍生出了 **L-BFGS 算法** [^sun_optimal]。
其中的 L 就表示所需的 memory 更 low 。
它的思想是不存储 Hessian 阵，而是只存储 BFGS 算法中近几次迭代的秩 2 矩阵。
之后，将这些秩 2 矩阵作用在单位阵上近似成 Hessian 阵。
之所以可以减少存储，是因为秩 2 矩阵在存储时可以无损压缩得很少。
（但这种方法没人用，我猜可能是效果不好吧，具体可能得试一下才能知道。）

## Levenberg-Marquardt 法

**L-M 算法**是针对二阶回归问题的一种牛顿法，恰好适合于损失函数为交叉熵的神经网络。
此方法中的 $H$ 矩阵被近似成了如下的形式：  
$$H=\dfrac{1}{C}\mathcal{I} + \dfrac{1}{l}\sum_{i=1}^l\left(j^i\right)^TJ^i$$  
也就是说，不必求解 Hessian 阵，求得 Jacobian 矩阵就可以了。 
但是这个方法的局限也很明显，效果也不如一阶算法 [^Wang_Distrubuted]。

> L-M 算法的推导  
> $$y=1$$ 
> to be continue... 

# 自然梯度法

自然梯度法是比牛顿

[^sun_optimal]: 孙文瑜, 徐成贤, 朱德通. 最优化方法[M]. Gao deng jiao yu chu ban she, 2004.
[^Mizutani_second]: E. Mizutani, S. E. Dreyfus, and J. W. Demmel, "Second-order backpropagation algorithms for a stagewise-partitioned separable Hessian matrix," in Proceedings. 2005 IEEE International Joint Conference on Neural Networks, 2005., 2005: IEEE, doi: 10.1109/ijcnn.2005.1555994. 
[^DFP_fault]: online: [https://zhuanlan.zhihu.com/p/144736223](https://zhuanlan.zhihu.com/p/144736223)
[^Wang_Distrubuted]: C.-C. Wang et al., "Distributed Newton Methods for Deep Neural Networks," Neural Computation, vol. 30, no. 6, pp. 1673-1724, 2018-06-01 2018, doi: 10.1162/neco_a_01088.
[^BFGS]: online: [https://zhuanlan.zhihu.com/p/29672873](https://zhuanlan.zhihu.com/p/29672873)