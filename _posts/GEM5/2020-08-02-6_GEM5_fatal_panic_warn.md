---
layout: post
title: GEM5- GEM5 中的 fatal 、 panic 、 warn
categories: GEM5
tags:
    - "GEM5"
    - "simulator"
    - "cycle accurate"
---

除了可以使用 assert 外， GEM5 中提供了三个用于检查的函数：

1. fatal / falal_if

    程序直接退出

1. panic / panic_ic

    程序退出当前函数，继续执行

1. warn / warn_if

    程序报 warning ，继续执行