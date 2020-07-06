---
layout: post
title: VMWare 提示与 Hyper-V冲突；如何在Windows 上彻底关闭Hyper-V
categories: others
tags:
    - "record"
---

前几天看到Windows功能中的虚拟机功能，突然好奇，手贱给打开了，觉得没什么意思，就也没动。直到今天打开VMWare提示与Hyper-V冲突。

>您的主机不满足在启用 Hyper-V 或 Device/Credential Guard 的情况下运行 VMware。

打开 VMWare 官方文档就是让关闭 Hyper-V。但是其实在我的个人版 Windows 是没有 Hyper-V 选项的。在搜了半天 Hyper-V 是啥才想到可能是和我前几天打开的那个虚拟机功能有关。

在我关闭这个功能之后，事情并没有改善，我一度以为思路错了，直到我继续谷歌半天才确定就是这个辣鸡虚拟机功能搞的鬼。***


## 解决问题记录

原因还是 Hyper-V 和 VMWare 不兼容。所以这里实际记录的实际上是如何彻底关闭 Hyper-V。

1. 小娜->启用和关闭Windows功能->关闭 虚拟机平台（或Hyper-V）

    ![](/img/others/1_figure_windows_function.jpg)

1. 小娜->计算机管理->服务和应用程序->服务->把所有带 Hyper-V 的停止并禁用。
    
    ![](/img/others/1_figure_windows_service.jpg)

1. 重启计算机

问题解决。
