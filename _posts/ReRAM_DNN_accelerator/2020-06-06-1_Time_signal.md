---
layout: post
title: Time signal 论文：Analysis and Design of Energy Efficient Time Domain Signal Processing
categories: ReRAM_paper
tags:
    - "analog computing"
    - "analog signal processing"
---

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

>Zhengyu Chen, Jie Gu, Analysis and Design of Energy Efficient Time Domain Signal Processing, International Symposium on Low Power Electronic Design (ISLPED), 2016.

My first time ever heard about using time signal for ReRAM accelerator. Found this paper to learn some details.

Let's see abstract first：

>Time domain signal processing (TDSP) encodes information into time rather than voltage with higher efficiency than conventional digital design. This paper performs systematical analysis on the design principle and energy efficiency of TDSP. Variation impact, which poses significant challenges to TDSP, is evaluated and a variation driven design methodology is proposed to achieve an optimum tradeoff between energy efficiency and design robustness. Several novel circuit level design techniques such as dual encoding strategy and bit-scalable design are also proposed in this work to significantly improve the energy efficiency of TDSP. Design example on a critical building block of facial recognition application was used to demonstrate the potential of the technique. The result in a 45nm technology shows 3.3X energy-delay product reduction and 34% area saving can be achieved using TDSP compared with conventional digital.

## 1. Time signal processing

### 1.1 system

System is described in figure below. It's composed of en/decoders and time domain logic.

<!--![System overview](/img/ReRAM_DNN_accelerator/1_figure_system.jpg)-->
<img src="/img/ReRAM_DNN_accelerator/1_figure_system.jpg" alt="System overview" width="300" align="bottom" />

### 1.2 Time Encoder

Time encoder is also called DTC (Digital-to-Time Converter). Figure below shows some impementation of DTCs.

<!--![TE](/img/ReRAM_DNN_accelerator/1_figure_te.jpg)-->
<img src="/img/ReRAM_DNN_accelerator/1_figure_te.jpg" alt="TE" width="300" align="bottom" />

Tech. (a) is proposed in [This Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6630119). $$T_{in}$$ is the time signal, such as *Step Signal*. $$D_{in}$$ is the digital signal. By selecting different path with $$D_{in}$$, delay of signal $$T_{out}$$ is decided. The design suffer from energy problem because of (1) multiple gates (2) signal returning to original stage which cause $$2\times$$ energy consumption.

Tech. (b) can encode multi-bit with a single inverter. (1) $$3\times$$ energy saving compared to (a). (2) energy consumption is a constant even if embedding multi-bit.

Tech. (c)(d) are "Cascade TE". To be further discuess in the next sections.

### 1.3 Dual-encoding Scheme

Compared to Tech. (a), which only encode information to only one kind of edge (raising or falling), this scheme means that encode information into both the two edges for energy saving. For more details, please refer to the paper.

### 1.4 Time Logic Cell (TLC)

No more words, see the figure below.

<!--![TLC](/img/ReRAM_DNN_accelerator/1_figure_TLC.jpg)-->
<img src="/img/ReRAM_DNN_accelerator/1_figure_TLC.jpg" alt="TLC" width="300" align="bottom" />

### 1.5 Time Decoder

A technology is described in figure blew. It is explicit and no more words.

<img src="/img/ReRAM_DNN_accelerator/1_figure_TDC.jpg" alt="TDC" width="300" align="bottom" />

## 2. Variation-Driven Design Methodology

### 2.1 Variation driven design

The auther introduces a energy-variation trade-off here. Consider the two kind of Tech. (c) (named cascade) and (d) (named cascode). As shown in figure below, cascade-type DTC has a larger energy but a smaller variation. Cascode-type DTC has an opposite characteristic. In order to trade off between energy and variation, a hybrid DTC is used.

<img src="/img/ReRAM_DNN_accelerator/1_figure_tradeoff.jpg" alt="trade off" width="500" align="bottom" />

Details of energy consumption and variation is described with the following equations:  
$$\Delta T_{cascade\_TE}=\sqrt{2N}\sigma_1$$  
$$\Delta T_{cascode\_TE}=\sqrt{\sum_{i=1}^{n}\left(A+N_i\sigma_2\right)^2}$$  
$$\Delta T_{hybrid\_TE}=\sqrt{\sum_{i=1}^m\left(A+N_i\sigma_2\right)^2+\sum_{j=1}^{n-m}2^j\left(A+2^{m-1}\sigma_2\right)^2}$$  
$$E_{cascade\_TE}=2N\cdot CV_{dd}^2$$  
$$E_{cascode\_TE}=2nCV_{dd}^2$$  
$$E_{hybrid\_TE}=\left(m+2^{n-m}\right)*2CV^2=\left(2m+2^{n-m+1}\right)CV^2$$

### 2.2 Simulated Variation Impact

Simulated variation compared to conventional adder is shown in the figure below. It is amazing that time signal computing can achieve a such low variation.

<img src="/img/ReRAM_DNN_accelerator/1_figure_variation_result.jpg" alt="variation_res" width="300" align="bottom">

## 3. Case Study

The following cases are studed in the origin paper:
1. Big-scalable design
1. Efficient MAX/MIN/CMP operation
1. Parallel operation with short cirtical path  

For more details, please refer to the origin paper.

## 4. Conclusion

Energy and area result is summrized in the following table:

<!--| | CPU | Conventional ASIC | TDSP |
|:---:|:---:|:---:|:---:|
|Technology||||-->

<table align="center" border="1" frame="box">
    <tr align="center">
        <td>&nbsp;</td> 
        <th>CPU</th> 
        <th>Conventional ASIC</th> 
        <th>TDSP</th>
    </tr>
    <tr align="center">
        <th> Technology </th>
        <td colspan="3"> 45nm, 1.1V </td>
    </tr>
    <tr align="center">
        <th> Energy (fJ)</th>
        <td> 2304 </td>
        <td> 323 </td>
        <td> 224.4 </td>
    </tr>
    <tr align="center">
        <th> Area (<span><script type="math/tex">\mu m^2</script></span>)</th>
        <td> N/A </td>
        <td> 115 </td>
        <td> 75.6 </td>
    </tr>
    <tr align="center">
        <th> Delay (ns)</th>
        <td> 3.2 </td>
        <td> 0.98 </td>
        <td> 0.43 </td>
    </tr>
</table>


---

## Thoughts

First ReRAM-based DNN accelerator that uses time signal is [Timely architecture](). The author claims that TDC is much more energy efficient than ADC. This paper solve my confusion on how DTC and TDC works.

Actually, I think DAC and TDC can also be a conversion pair. With a capacitance used as integrator, along with a comparator, analog signal can be converted to time signal.

Moreover, the design in timely uses a circuit to store time signal, which is also what I am confused about.