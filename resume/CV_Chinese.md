---
layout: cv
title: Yilong Zhao
email:
  url: mailto:sjtuzyl@sjtu.edu.cn
  text: sjtuzyl@sjtu.edu.cn
phone: 15221833996
homepage: 
  url: https://xiaoke0515.github.io/
  text: https://xiaoke0515.github.io/
---

<a href="{{"/resume/resume/index.html" | prepend: site.baseurl}}" style="margin-left:0.5em">English Version</a>


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

### **上海交通大学 (SJTU)** `2022.9 - 2026.6（预计）`

```
上海, 中国
```

- 计算机科学与技术 博士
- 导师：[蒋力](http://www.cs.sjtu.edu.cn/PeopleDetail.aspx?id=97) 研究员

### **上海交通大学 (SJTU)** `2018.9 - 2021.3`

```
上海, 中国
```

- 计算机技术 工程硕士
- 导师：[蒋力](http://www.cs.sjtu.edu.cn/PeopleDetail.aspx?id=97) 研究员
- GPA 3.49/4.0

### **上海交通大学(SJTU)** `2014.9 - 2018.6`

```
上海, 中国
```

- 电子科学与技术 工学学士
- 工商管理（第二专业）
- GPA 3.51/4.3


## 论文 （完整列表见[这里]({{ site.baseurl.url }}/publications)）

### 一作论文

1. **Yilong Zhao**, Fangxin Liu, Onur Mutlu, Mingyu Gao, Jian Liu, Li Liang, and Haibing Guan, "COMET: A Cooperative Scheduling Framework for Concurrent PIM/CPU Execution on Mobile Devices", in *Proceedings of the 53st International Symposium on Computer Architecture* (**ISCA’26, CCF-A**, Accepted)

1. **Yilong Zhao**, Fangxin Liu, Zongwu Wang, Mingjian Li, Mingxing Zhang, Chixiao Chen, and Li Jiang, **BLADE: Boosting LLM Decoding's Communication Efficiency in DRAM-based PIM**, in *Proceedings of the 31st Asia and South Pacific Design Automation Conference* (**ASP-DAC'26**, CCF-C)

1. **Yilong Zhao**, Fangxin Liu, Xiaoyao Liang, Mingyu Gao, Naifeng Jing, Chengyang Gu, Qidong Tang, Tao Yang, and Li Jiang, **STAMP: Accelerating Second-order DNN Training Via ReRAM-based Processing-in-Memory Architecture**, in *Proceedings of the 16th International Symposium on Advanced Parallel Processing Technology* (**APPT'25**, CCF-C)

1. **Yilong Zhao**, Mingyu Gao, Huanchen Zhang, Fangxin Liu, Gongye Chen, He Xian, Haibing Guan, and Li Jiang, **PUSHtap: PIM-based In-Memory HTAP with Unified Data Storage Format**, In *Proceedings of the 30th ACM International Conference on Architectural Support for Programming Languages and Operating Systems*, Volume 3 (**ASPLOS'25, CCF-A**)

1. **Yilong Zhao**, Mingyu Gao, Fangxin Liu, Yiwei Hu, Zongwu Wang, Han Lin, Ji Li, He Xian, Hanlin Dong, Tao Yang, Naifeng Jing, Xiaoyao Liang, and Li Jiang, **UM-PIM: DRAM-based PIM with Uniform & Shared Memory Space**, in *51st International Symposium on Computer Architecture* (**ISCA'24, CCF-A**)

1. **Yilong Zhao**, Li Jiang, Mingyu Gao, Naifeng Jing, Chengyang Gu, Qidong Tang, Fangxin Liu, Tao Yang, and Xiaoyao Liang, **RePAST: A ReRAM-based PIM Accelerator for Second-order Training of DNN**, *arXiv preprint 2022*

1. Weidong Cao, **Yilong Zhao(共一)**, Adith Boloor, Yinhe Han, Xuan Zhang, and Li Jiang, **Neural-PIM: Efficient Processing-In-Memory with Neural Approximation of Peripherals**, in *IEEE Transactions on Computers* (**TC, 2021, CCF-A**)

1. **Yilong Zhao**, Zhezhi He, Naifeng Jing, Xiaoyao Liang, and Li Jiang. 2021. **Re2PIM: A Reconfigurable ReRAM-Based PIM Design for Variable-Sized Vector-Matrix Multiplication**. In *Proceedings of the 2021 on Great Lakes Symposium on VLSI* (**GLSVLSI '21**, CCF-C)

### 其他论文

1. Yiwei Hu, Fangxin Liu, Zongwu Wang, **Yilong Zhao**, Tao Yang, Haibing Guan, and Li Jiang, **PLAIN: Leveraging High Internal Bandwidth in PIM for Accelerating Large Language Model Inference via Mixed-Precision Quantization**, In Proceedings of the 44th IEEE/ACM International Conference on Computer-Aided Design, (ICCAD’25).

1. Fangxin Liu, Wenbo Zhao, Zongwu Wang, **Yilong Zhao**, Tao Yang, Yiran Chen, Li Jiang, "**IVQ: In-Memory Acceleration of DNN Inference Exploiting Varied Quantization**", in IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, (TCAD, 2022)

1. Fangxin Liu, Wenbo Zhao, Zhezhi He, Zongwu Wang, **Yilong Zhao**, Yongbiao Chen, and Li Jiang, "**Bit-Transformer: Transforming Bit-level Sparsity into Higher Preformance in ReRAM-based Accelerator**", In Proceedings of the 40th International Conference on Computer-Aided Design (ICCAD '21).

1. Fangxin Liu, Wenbo Zhao, Zhezhi He, Zongwu Wang, **Yilong Zhao**, Tao Yang, Naifeng Jing, Xiaoyao Liang, and Li Jiang, "**SME: ReRAM-based Sparse-Multiplication-Engine to Squeeze-Out Bit Sparsity of Neural Network**," In Proceedings of the 39th IEEE International Conference on Computer Design (ICCD’21).

1. Tao Yang, Dongyue Li, Yibo Han, **Yilong Zhao**, Fangxin Liu, Xiaoyao Liang, Zhezhi He, and Li Jiang, "**PIMGCN: A ReRAM-Based PIM Design for Graph Convolutional Network Acceleration**", In Proceedings of the 58th ACM/IEEE Design Automation Conference, (DAC’21).

1. Ziqi Meng, Weikang Oian, **Yilong Zhao**, Yanan Sun, Rui Yang, and Li Jiang, "**Digital Offset for RRAM-based Neuromorphic Computing: A Novel Solution to Conquer Cycle-to-cycle Variation**," In Proceedings of the 24th Conference on Design, Automation and Test in Europe, (DATE’2021).

1. Yanan Sun, Chang Ma, Zhi Li, **Yilong Zhao**, Jiachen Jiang, Weikang Qian, Rui Yang, Zhezhi He and Li Jiang, "**Unary Coding and Variation-Aware Optimal Mapping Scheme for Reliable ReRAM-based Neuromorphic Computing**," in IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, (TCAD, 2021)

1. Zhuoran Song, **Yilong Zhao**, Yanan Sun, Xiaoyao Liang and Li Jiang.**ESNreram: An Energy-Efficient Sparse Neural Network Based on Resistive Random-Access Memory**. Proceedings of the 2020 on Great Lakes Symposium on VLSI, GLSVLSI. 2020: 291-296.

1. Chaoqun Chu, Yanzhi Wang, **Yilong Zhao**, Xiaolong Ma, Shaokai Ye, Yunyan Hong, Xiaoyao Liang, Yinhe Han and Li Jiang. **PIM-Prune: Fine-Grain DCNN pruning for Crossbar-based Process-In-Memory architecture.** ACM/IEEE Design Automation Conference, DAC, 2020

1. Jia Wang, **Yilong Zhao**, Xin Huang and Guangqiang He. **High Speed Polarization-Division Multiplexing Transmissions Based on the Nonlinear Fourier Transform**, ZTE COMMUNICATIONS 17, 3  (2019).

1. Aiguo Sheng, **Yilong Zhao**, and Guangqiang He, "**Characterization of Kerr Solitons in Microresonators with Parameter Optimization and Nonlinear Fourier Spectrum**," in Conference on Lasers and Electro-Optics, OSA Technical Digest (Optical Society of America, 2019), paper JW2A.47.

1. Aiguo Sheng, **Yilong Zhao**, and Guangqiang He, "**Quadratic soliton combs in doubly resonant half-harmonic generation**," in Nonlinear Optics (NLO), OSA Technical Digest (Optical Society of America, 2019), paper NTu4A.18.

### **专利**

1. 刘方鑫, 蒋力, **赵怿龙**，“大语言模型的解码加速方法、系统、设备及可读存储介质”。 发明专利，申请号：2025118583915.5

1. 蒋力，**赵怿龙**，“**可重构架构、加速器、电路部署和计算数据流方法**”。发明专利，申请号：202010910280.5；授权号：CN112181895B

1. 蒋力，**赵怿龙**，崔晓松，陈云，廖健行，“**神经网络电路**”。发明专利，申请号：202010729402.05；公开号：CN114004344A
 
## 获奖

1. Student Travel Grant, International Symposium on Advanced Parallel Processing Technology (APPT), 2025

1. 2025年度 优秀实习生，上海期智研究院

## 项目经历

### **上海期智研究院**

华为合作项目 __--面向光通信、无线通信的的存算一体实现--__ `2021.03-2022.06`
  
  研究目的是基于存算一体技术实现光通信与无线通信的接收机，负责工作如下：
  
  - 设计基于存算一体的光通信、无线通信系统总体架构，包括算子拆分与算法的重构。
  - 实现部分算子的电路仿真。
  - 针对高功耗计算模块进行AI化，在误差允许的条件下达到比现有数值算法更低的计算量。


### **上海羿煜电子科技有限公司**

实习 `2020.07-2021.07`

使用Candance为电路设计版图并验证。

### **上海交通大学, 先进计算机体系结构实验室** 

[蒋力](http://www.cs.sjtu.edu.cn/PeopleDetail.aspx?id=97) 研究员指导

华为合作项目   __--基于ReRAM的高效可靠DNN加速器技术研究--__ `2019.4 - 2020.4`
  
  项目研究基于ReRAM的DNN加速器中，提升计算可靠性以及利用稀疏性提升能效，负责工作如下：
  
  - 设计并编写了一个周期准确的ReRAM神经网络加速器架构的仿真器。仿真器以GEM5为基础编写，可以仿真存储器与架构中各计算电路模块的交互行为，从而更准确地仿真计算周期数与功耗等指标。
  - 根据项目要求，改写仿真器以支持稀疏性网络的计算与可靠性的评估，仿真器的结果作为项目评估算法的重要指标。
  - 设计一个基于ReRAM的DNN加速器架构，以支持稀疏性网络的计算。


### **上海交通大学，量子非线性光子学实验室**

[何广强](http://qnp.sjtu.edu.cn/content.aspx?info_lb=80&flag=39) 教授指导

研究 __--光频梳的产生与演化条件的研究--__ `2018.3 - 2018.6`
  
  - 研究光孤子与光频梳在光学微腔中的产生演化条件，并搭建仿真系统。
  - 首次使用非线性本征值分析光频梳在光学微腔中的演化，得到光孤子数量与非线性本征值的关系。


中兴合作项目 __--基于硅基微纳谐振腔的量子纠缠光频梳产生及传输问题研究--__ `2017.6 - 2018.3`
  
  项目研究利用非线性频域编码以解决长距离传输过程中光信号的演化衰变问题，负责工作如下：
  
  - 用 Matlab 编写系统中的非线性傅里叶变换与反变换模块
  - 光纤信号传输仿真系统的搭建


### **利思电器** 

实习 `2016.07 - 2016.08`


### **上海交通大学，大学生创新计划**

[赵春宇](http://www.ie.sjtu.edu.cn/Data/View/261)教授指导

利思合作项目  __--带蓝牙接口的DTU的开发--__ `2015.12 - 2016.12`
  
  定制一个数据转发单元（DTU）电路与数据分析显示程序，负责工作如下：

  - 作为项目的负责人，负责项目的进展与最终汇报
  - 设计并开发了一个DTU。包括电路设计、焊接与嵌入式编程，并解决电路在应用场景下的电磁干扰问题


### **助教**

  - **算法设计与分析 (CS222)** `上海交通大学, 2019-2020 秋` <br>

## -

<hr style=" height:2px;border:none;border-top:2px dotted #185598;" /> 
Last updated: 2026.04 
