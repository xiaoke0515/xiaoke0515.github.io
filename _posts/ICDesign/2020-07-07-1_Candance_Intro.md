---
layout: post
title: Candance 1： Candance的初步使用
categories: ICDesign
tags:
    - "ic"
    - "candance"
    - "virtuoso"
---

## Candance的安装

使用的是已经安装好的 candance ，没有涉及到安装问题，留出位置，以后遇到问题再补。

## Candance 启动

命令：

> virtuoso &

在我安装好的这个cadance中，virtuoso 打开的是6.1版本，icfb 打开的是5.1版本。6.1版本用的是oa库，5.1版本用的是cdb库，这两个库不兼容，使用时要注意。在此我用的是6.1版本。

## 安装库

安装时要注意是 cdb 库还是 oa 库。在我电脑中的库中，SMIC_13mmrf_1P6M_30k 是 cdb 库，FreePDK-45 是 OA 库，所以这里我将安装FreePDK库。

Tools - Library Manager - File - New Library， Directory选择 /path/to/pdk/FreePDK45/ncsu_basekit/lib/，Name 输入NCSU_Devices_FreePDK45，之后 OK。

![](/img/others/2_figure_New_Library.png)

在如下对话框中选择 Do not need process information 即可。

![](/img/others/2_figure_Technology_File_for_New_Library.png)

之后回到如下界面，在新的Library中出现 cell，即说明安装成功。每一个 cell 都有许多 View。双击一个 view 可浏览，如下图。

![](/img/others/2_figure_Library_Install_Done.png)

## 新建 cellview

在安装好库后就可以画 cell 了。在画 cell 之前要新建一个库，用于存放我们画的 cell。步骤与上一节相同，只不过我们的路径选择一个空文件夹即可。在这里我新建的库的名字叫 proj1。

File - New - CellView， Library 选择我们新建的库， cell 起一个名字（这里我要画一个反相器），Type 选择 schematic。OK 之后就会打开一个画图的界面。

![](/img/others/2_figure_New_File.png)

反相器由两个 mos 组成。接下来我们将画这两个 mos 。 Create - Instance， Library 选择 FreePDK 那个库， cell 选择一个mos， View 选择 Symbol， Name 随意取个名字。此时在光标处就会出现一个 mos 管的形状，点击就可以把它放在任何想要的位置。

![](/img/others/2_figure_Add_Instance.png)

画好两个 mos 后，接下来增加四个 pin， 分别对应 Vin 、 Vout 、 VDD 、 GND。 Create - Pin ，根据需要选择输入-输出类型，之后添加即可。最后将两个 mos 和四个 pin 用线连接起来。

![](/img/others/2_figure_Inverter_Done.png)

之后 File- Check and Save ，无 error 即可。

## 搭建 inverter 的仿真电路

首先要给我们画的 inverter 创建一个 symbol。这里我们为方便进行自动生成。 Create - CellView - From CellView。 按如下默认设置即可，选择 OK 。

![](/img/others/2_figure_CellView_from_CellView.png)

此时在 Library Manager 中，我们发现我们画的 inverter 多了个 symbol 的 view，说明创建成功。

![](/img/others/2_figure_Add_Symbol_Done.png)

之后我们将搭建 inverter 的仿真电路。同样地，我们新建一个 cellview，我这里取名为 inverter_sim，按下图添加周边电路元件。下面的元件都可以在 basic 库中找到。

![](/img/others/2_fiugre_Inverter_sim.png)

同样地， check and save。

## Spectre 仿真

在我们的 inverter_sim 的原理图界面，Launch - ADE L。


![](/img/others/2_figure_ADEL.png)

首先添加 model library。Setup - Model Library。 路径为 /path/to/pdk/FreePDK45/ncsu_basekit/models/hspice/tran_models ， 把所有的 .inc 文件添加进去。

![](/img/others/2_figure_Model_Library_Setup.png)

Analysis - choose， 这里就和 spice 一样了，选择一种 analysis 。

![](/img/others/2_figure_Choosing_Analysis.png)

Simulation - NetList and Run，弹出一个窗口，无 error 和 warning。

![](/img/others/2_figure_Simulation.png)

Results - Direct Plot - Main Form，按如下图选择并在原理图中选择一个点来 plot。我这里选择 inverter 的 Vout，直接在原理图上选择对应位置即可。

![](/img/others/2_figure_Direct_Plot_Form.png)

之后就会弹出一个窗口，就是绘制的曲线。

![](/img/others/2_figure_Visualization.png)

至此，我们的第一个 candance project 仿真完成。