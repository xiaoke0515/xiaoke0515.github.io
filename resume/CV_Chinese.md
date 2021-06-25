---
layout: cv
title: Yilong Zhao
email:
  url: mailto:sjtuzyl@sjtu.edu.cn
  text: sjtuzyl@sjtu.edu.cn
phone: 15221833996
homepage: 
  url: https://xiaoke0515.github.io/page/
  text: https://xiaoke0515.github.io/page/
---

<a href="{{"/resume/resume/index.html" | prepend: site.baseurl}}" style="margin-left:0.5em">英文版</a>


# 赵怿龙

<!--
include contact information from the front matter
Supported arguments:
    - homepage: url, text
    - phone
    - email
-->
<div id="contact-info">

    {% if page.homepage %}
    <i class="fi-home" style="margin-left:1em"></i>
    <a href="{{ page.homepage.url }}" style="margin-left:0.5em"> {{ page.homepage.text }}</a>
    {% endif %}

    {% if page.email %}
    <i class="fi-mail" style="margin-left:1em"></i>
    <a href="{{ page.email.url }}" style="margin-left:0.5em">{{ page.email.text }}</a>
    {% endif %}

    {% if page.phone %}
    <i class="fi-telephone" style="margin-left:1em"></i>
    {{ page.phone }}
    {% endif %}

</div>

## 教育经历

### **上海交通大学 (SJTU)** `2018.9 - 至今`

```
上海, 中国
```

- 计算机技术 工程硕士
- 导师：[蒋力](http://www.cs.sjtu.edu.cn/PeopleDetail.aspx?id=97) 教授
- GPA 3.49/4.0

### **上海交通大学(SJTU)** `2014.9 - 2018.6`

```
上海, 中国
```

- 电子科学与技术 工学学士
- 工商管理（第二专业）
- GPA 3.51/4.3


## 论文


**Yilong Zhao**, Zhezhi He, Naifeng Jing, Xiaoyao Liang, and Li Jiang. 2021. **Re2PIM: A Reconfigurable ReRAM-Based PIM Design for Variable-Sized Vector-Matrix Multiplication**. In Proceedings of the 2021 on Great Lakes Symposium on VLSI (GLSVLSI '21). Association for Computing Machinery, New York, NY, USA, 15–20. 

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/10.1145_3453688.3461494.txt)]
  [[url](https://dl.acm.org/doi/10.1145/3453688.3461494)]

Yanan Sun, Chang Ma, Zhi Li, **Yilong Zhao**, Jiachen Jiang, Weikang Qian, Rui Yang, Zhezhi He and Li Jiang, "**Unary Coding and Variation-Aware Optimal Mapping Scheme for Reliable ReRAM-based Neuromorphic Computing**," in IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, 2021

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/9323041.txt)]
  [[url](https://ieeexplore.ieee.org/document/9323041)]

Zhuoran Song, **Yilong Zhao**, Yanan Sun, Xiaoyao Liang and Li Jiang.**ESNreram: An Energy-Efficient Sparse Neural Network Based on Resistive Random-Access Memory**. Proceedings of the 2020 on Great Lakes Symposium on VLSI, GLSVLSI. 2020: 291-296.

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/10.1145_3386263.3406897.txt)]
  [[url](https://dl.acm.org/doi/abs/10.1145/3386263.3406897)]

Chaoqun Chu, Yanzhi Wang, **Yilong Zhao**, Xiaolong Ma, Shaokai Ye, Yunyan Hong, Xiaoyao Liang, Yinhe Han and Li Jiang. **PIM-Prune: Fine-Grain DCNN pruning for Crossbar-based Process-In-Memory architecture.** ACM/IEEE Design Automation Conference, DAC, 2020

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/92185237.txt)]
  [[url](https://ieeexplore.ieee.org/abstract/document/9218523)]

Jia Wang, **Yilong Zhao**, Xin Huang and Guangqiang He. **High Speed Polarization-Division Multiplexing Transmissions Based on the Nonlinear Fourier Transform**, ZTE COMMUNICATIONS 17, 3  (2019).

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/jia2019high.txt)]
  [[url](http://tech-en.zte.com.cn/CN/abstract/abstract140.shtml)]
  [[pdf](http://qnp.sjtu.edu.cn/userfiles/files/High%20Speed%20Polarization-Division%20Multiplexing%20Transmissions%20Based%20on%20the%20Nonlinear%20Fourier%20Transform(1).pdf)]

Aiguo Sheng, **Yilong Zhao**, and Guangqiang He, "**Characterization of Kerr Solitons in Microresonators with Parameter Optimization and Nonlinear Fourier Spectrum**," in Conference on Lasers and Electro-Optics, OSA Technical Digest (Optical Society of America, 2019), paper JW2A.47.

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/8749866.txt)]
  [[url](https://ieeexplore.ieee.org/abstract/document/8749866)]
<!--[[BibTeX]({{ page.homepage.url }}/assets/siggraph20-penrose.txt)]-->

Aiguo Sheng, **Yilong Zhao**, and Guangqiang He, "**Quadratic soliton combs in doubly resonant half-harmonic generation**," in Nonlinear Optics (NLO), OSA Technical Digest (Optical Society of America, 2019), paper NTu4A.18.

  [[BibTeX]({{ site.baseurl.url }}/resume/publications/bibtex/8959308.txt)]
  [[url](https://ieeexplore.ieee.org/abstract/document/8959308)]

### **专利**

蒋力，**赵怿龙**，“可重构架构、加速器、电路部署和计算数据流方法”。发明专利，申请号：202010910280.5

蒋力，**赵怿龙**，崔晓松，陈云，廖健行，“神经网络电路”。发明专利，申请号：202010729402.05
 

## 科研经历

### **上海交通大学, 先进计算机体系结构实验室** 

[蒋力](http://www.cs.sjtu.edu.cn/PeopleDetail.aspx?id=97) 教授指导

___基于ReRAM的可重构CNN加速器架构设计___`2019.8 - 至今`
  - 设计了一个可重构的 ReRAM 神经网络加速器架构
  - 设计了一个高能效的 ReRAM 神经网络加速器数据流

项目 ___基于ReRAM的高效可靠DNN加速器技术研究___`2019.4 - 2020.4`
  - 以GEM5仿真器为基础编写了一个ReRAM神经网络加速器架构的仿真器
  - ReRAM神经网络加速器的稀疏性架构设计

### **上海交通大学，量子非线性光子学实验室**

[何广强](http://qnp.sjtu.edu.cn/content.aspx?info_lb=80&flag=39) 教授指导

项目 ___光频梳的产生与演化条件的研究___ `2018.3 - 2018.6`
  - 研究光孤子与光频梳在光学微腔中的产生演化条件
  - 分析光孤子在光学微腔演化时非线性本征值与频谱的演化

项目 ___基于硅基微纳谐振腔的量子纠缠光频梳产生及传输问题研究___ `2017.6 - 2018.3`
  - 用 Matlab 编写系统中的非线性傅里叶变换与反变换模块
  - 光纤信号传输仿真系统的搭建

### **上海交通大学，大学生创新计划**

[赵春宇](http://www.ie.sjtu.edu.cn/Data/View/261)教授指导

作为项目 ___带蓝牙接口的DTU的开发___ 的负责人 `2015.12 - 2016.12`
  - 设计并开发了一个带蓝牙接口的数据转发单元（DTU）。主要负责电路设计、焊接与嵌入式编程

### **助教**

  - **算法设计与分析 (CS222)** `上海交通大学, 2019-2020 秋` <br>

## --

<hr style=" height:2px;border:none;border-top:2px dotted #185598;" /> 
Last updated: Mar. 2021 
