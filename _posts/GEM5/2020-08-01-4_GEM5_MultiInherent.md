---
layout: post
title: GEM5- GEM5 中 SimObject 多继承的问题
categories: GEM5
tags:
    - "GEM5"
    - "simulator"
    - "cycle accurate"
---

之前遇到了一个比较蠢的问题，记录一下。

在定义一个 SimObject 时，突发奇想搞了个多继承，即既继承 SimObject 和另一个基类。
就这样出了问题。
观察 python/m5/simulate.py/instantiate() 发现，在实例化的过程中调用了基类中的函数，导致运行的错误。

所以

##  **不要用多继承**