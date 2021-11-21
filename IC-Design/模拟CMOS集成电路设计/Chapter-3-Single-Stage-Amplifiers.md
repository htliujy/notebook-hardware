---
title: Chapter 3 Single-Stage Amplifiers
date:  20200223 18:00:00
categories: 模拟CMOS集成电路设计
tags: 
 - 读书笔记
mathjax: true
---

# Chapter 3 Single-Stage Amplifiers

## 章节介绍

- 本章开始，为打字方便（懒得切中英文输入法），以及懒得翻译，将会出现中英文混合记录。

我们将会分析一阶放大电路的低频特征行为，分析大信号、小信号模型，建立技术上的直觉以及用于分析复杂电路的有用的模型。获取检查电路行为的直觉，而不是靠冗长的运算。

## 3.1 应用 Applications

在小信号接收时，我们需要低噪声放大器（LNA），在传输时，我们需要功率放大（PA），等等，对我们的设计提出挑战。

## 3.2 普通因素考虑

理想放大器应该是线性的，输出$y(t)$与输入$x(t)$应该满足：

$$
y(t)=\alpha_1x(t) \tag{3.1}
$$

其中$$\alpha_1$$代表增益。若是叠加直流量，则有 $$y(t)=\alpha_0+\alpha_1x(t)$$，当信号变大，增益有各种偏差时：

$$
y(t)=\alpha_0+\alpha_1x(t)+\alpha_2x^2(t)+\cdots+\alpha_nx^n(t)\tag{3.2}
$$

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.1&#32;General&#32;RF&#32;transceiver.png" width = "100%" height = "100%" alt="RF 传输" align=center />
</div>
<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.2&#32;Input-output&#32;characteristic.png" width = "100%" height = "100%" alt="输入输出特性" align=center />
</div>

**运放的什么性能是重要的呢？** 增益，速度，功率耗散，供电电压，线性度，噪声，压摆幅。还有输入输出阻抗。在实际设计中，这些参数互相制衡，使得设计变成一个多维度的优化问题。如图3.3中的“模拟设计八角”：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.3&#32;Analog&#32;design&#32;octagon.png" width = "100%" height = "100%" alt="模拟设计权衡八角形" align=center />
</div>

表3.1中是本章介绍的放大器概览，在这些放大器中我们需要：1、设置正确的静态偏置点；2、分析电路的小信号及大信号行为特征。本章主要分析电路的小信号模型及大信号模型，而将静态偏置留到第五章。

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Table&#32;3.1&#32;Amplifier&#32;categories.png" width = "100%" height = "100%" alt="放大器分类" align=center />
</div>

## 3.3 共源（Common-Source Stage）

### 3.3.1 电阻负载电路中的共源级（Common-Source Stage with Resistive Load）

如图：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.4&#32;common-source&#32;stage.png" width = "100%" height = "100%" alt="共源" align=center />
</div>

图中，我们以$$V_{in}$$从0V往更高电势分析：

- 当$$V_{in}$$=$$V_{TH}$$时，这时M1开始导通，$$V_{out}$$仍然接近$$V_{DD}$$，M1处于横流区（见公式2.9）；

$$
V_{out}=V_{DD}-R_D\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH})^2 \tag{3.3}
$$

- 当$$V_{in}$$>$$V_{TH}+V_{out}$$,M1进入三极管区(见公式2.8)；

$$
V_{out}=V_{DD}-R_D\mu_nC_{ox}\frac{W}{L}[(V_{in}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}] \tag{3.5}
$$

- 当$$V_{in}$$足够大，使得$$V_{out}≪2(V_{in}-V_{TH})$$时，M1进入深度三极管区（线性区，M1等效为电阻）：
  
$$
\begin{aligned}
V_{out}&=V_{DD}\frac{R_{on}}{R_{on}+R_D}\\
&=\frac{V_{DD}}{1+\mu_nC_{ox}\frac{W}{L}R_D(V_{in}-V_{TH})}
\end{aligned} \tag{3.6 3.7}
$$

**重要：** 我们一般让MOS工作在横流区，也就是$$V_{out}>V_{in}-V_{TH}$$，这样增益比较大，根据公式3.3，我们有：

$$
\begin{aligned}
A_{v}&=\frac{\partial V_{out}}{\partial V_{in}}\\
&=-R_D\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH})\\
&=-g_mR_D
\end{aligned} \tag{3.8 3.9 3.10}
$$

如何获得更高的增益？将公式3.10改写为：

$$
\begin{aligned}
A_{v}&=-\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}\frac{V_{RD}}{I_D}\\
&=-\sqrt{2\mu_nC_{ox}\frac{W}{L}}\frac{V_{RD}}{\sqrt{I_D}}\\
\end{aligned} \tag{3.12 3.13}
$$

其中$$V_{RD}$$代表$$R_D$$两端的电势差，要增大增益，我们可以增加$$V_{RD}$$或者$$W/L$$，或者降低$$I_D$$。这里$$W/L$$涉及到器件尺寸，而$$V_{RD}$$涉及$$V_{out}$$摆幅。但若是$$V_{RD}$$不变，而降低$$I_D$$，那么将会有更大的时间常数（寄生电容效应），降低器件的速度。

且更大的$$R_D$$将会使得沟道长度调制效应更加明显。

$$
A_v=-g_m\frac{R_oR_D}{r_o+R_D} \tag{3.17}
$$

小信号模型见下图：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.7&#32;Small-signal&#32;model&#32;of&#32;CS&#32;stage&#32;including&#32;the&#32;transistor&#32;output&#32;resistance.png" width = "100%" height = "100%" alt="CS 的小信号模型" align=center />
</div>

从Example 3.3中可以知道，若是将$$R_D$$改为恒流源，那么公式3.17中的$$R_D$$（图3.7）为无穷大，有：

$$
A_v=-g_mr_o \tag{3.18}
$$

### 3.3.2 二极管连接的共源级（CS Stage with Diode-Connected Load）

当MOS的DG相连，如图3.10，我们称为二极管连接，很容易知道，此MOS总是处于饱和区（当然，这里只是相对于三极管区而言，因为还有截止区）：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.10&#32;Diode&#32;connect.png" width = "100%" height = "100%" alt="二极管连接" align=center />
</div>

图3.10中应有：

$$
I_X=V_X/r_o+g_mV_X
$$

但，当S极不接地时，实际电路连接及其等效模型分析，如下图（此时考虑body effect）：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.11&#32;Diode&#32;connect&#32;analysis.png" width = "100%" height = "100%" alt="二极管连接的电路及小信号模型" align=center />
</div>

$$
(g_m+g_{mb})V_X+\frac{V_X}{r_o}=I_X \tag{3.21}
$$

从公式3.21可以得到：

$$
\begin{aligned}
\frac{V_X}{I_X}&=\frac{1}{g_m+g_{mb}+r_o^{-1}}\\
&=\frac{1}{g_m+g_{mb}}||r_o\\
&≈\frac{1}{g_m+g_{mb}}
\end{aligned} \tag{3.22 3.23 3.24}
$$

结论：当考虑body effect时，从S极看进去此电路，阻抗更小，从D极看进去，阻抗更大。

**提问：** 图3.12和图3.11的区别

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.12&#32;Impedance&#32;seen&#32;at&#32;the&#32;source.png" width = "100%" height = "100%" alt="添加$Z_L$后的二极管连接及小信号模型" align=center />
</div>

**答：** ？？

现在，我们就来看看带有二极管连接MOS作为负载的共源stage，暂时先忽略沟道长度调制效应，

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.13CS&#32;stage&#32;with&#32;diode-connected&#32;load.png" width = "100%" height = "100%" alt="CS stage with diode-connected load" align=center />
</div>

根据公式3.10和公式3.24，

$$
\frac{V_X}{I_X}≈\frac{1}{g_m+g_{mb}} \tag{3.24}
$$

$$
A_{v}=-g_mR_D \tag{3.10}
$$

有：
$$
\begin{aligned}
A_{v}&=-g_{m1}\frac{1}{g_{m2}+g_{mb2}}\\
&=-\frac{g_{m1}}{g_{m2}}\frac{1}{1+\eta}
\end{aligned} \tag{3.27 3.28}
$$

其中，$$\eta=g_{mb2}/g_{m2}$$，这本书太坑爹了，$$\eta$$竟然定义得那么隐晦，如果定义成$$\eta=\partial{V_{TH}}/\partial{V_{SB}}$$会不会更简单点？

根据公式2.19：$$g_m =\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}$$，且$$I_{D1}=I_{D2}$$有

$$
\begin{aligned}
A_{v}&=-\frac{\sqrt{2\mu_nC_{ox}({W}/{L})_1I_{D1}}}{\sqrt{2\mu_nC_{ox}({W}/{L})_2I_{D2}}}\frac{1}{1+\eta}\\
&=-\sqrt{\frac{({W}/{L})_1}{({W}/{L})_2}}\frac{1}{1+\eta}
\end{aligned} \tag{3.29 3.30}
$$

This equation reveals an interesting property: if the variation of η with the output voltage is neglected, the gain is independent of the bias currents and voltages (so long as M1 stays in saturation). In other words, as the input and output signal levels vary, the gain remains relatively constant, indicating that the input-output characteristic is relatively linear.

大信号模型分析

$$
\frac{1}{2}\mu_nC_{ox}(\frac{W}{L})_1(V_{in}-V_{TH1})^2=\frac{1}{2}\mu_nC_{ox}(\frac{W}{L})_2(V_{DD}-V_{out}-V_{TH2})^2 \tag{3.31}
$$

开方得到：

$$
\sqrt{(\frac{W}{L})_1}(V_{in}-V_{TH1})=\sqrt{(\frac{W}{L})_2}(V_{DD}-V_{out}-V_{TH2}) \tag{3.32}
$$

两边都对$$V_{in}$$求导（思考：求导的物理意义是？）

$$
\sqrt{\left (\frac{W}{L}\right )_1}=\sqrt{\left (\frac{W}{L}\right )_2}\left(-\frac{\partial V_{out}}{\partial V_{in}}- \frac{\partial V_{TH2}}{\partial V_{in}} \right) \tag{3.33}
$$

因$$\partial{V_{TH2}}/\partial{V_{in}} = (\partial{V_{TH2}}/\partial{V_{out}})(\partial{V_{out}}/\partial{V_{in}})=\eta(\partial{V_{out}}/\partial{V_{in}})$$（其中$$\eta=g_{mb}/g_{m}$$在公式3.28中定义，**那为什么**$$(\partial{V_{TH2}}/\partial{V_{out}})=\eta$$?需要自行计算验证，主要是要明白一点$$g_m=\partial{I_D}/\partial{V_{GS}}=-\partial{I_D}/\partial{V_{TH}}$$，这个在物理上很好理解），有：

$$
\frac{\partial V_{out}}{\partial V_{in}}=-\sqrt{\frac{(W/L)_1}{(W/L)_2}}\frac{1}{1+\eta} \tag{3.34}
$$

图3.14中，若是电流源$$I_1$$很小，将会发生生么呢？

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.14&#32;Diode&#32;connect&#32;with&#32;current&#32;source.png" width = "100%" height = "100%" alt="二极管接法串接电流源" align=center />
</div>

随着$$I_1$$减少，是否$$V_{GS2}≈V_{TH2}$$，同时$$V_{out}≈V_{DD}-V_{TH2}$$？但在实际中，因为亚阈值导通的情况，$$V_{out}$$将会逐渐逼近$$V_{DD}$$，但另一方面，因为输出电容的处在，将会导致$$V_{out}$$从$$V_{DD}-V_{TH2}$$向$$V_{DD}$$的压摆率降低，因此，若是在高频开关中，这样的电路，我们仍然假定$$V_{out}$$保持在$$V_{DD}-V_{TH2}$$附近。

问题：画出图3.13中的$$V_{in} V_{out}$$曲线：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.15&#32;Input-output&#32;characteris-&#32;tic&#32;of&#32;a&#32;CS&#32;stage&#32;with&#32;diode-connected&#32;load.png" width = "100%" height = "100%" alt="图3.13的$$V_{in} V_{out}$$曲线" align=center />
</div>

问题：分析若是将M2改为P管，$$A_v$$为？提示：没有body effect，同时我们先忽略channel-length modulation。

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.16&#32;CS&#32;stage&#32;with&#32;diode-&#32;connected&#32;PMOS&#32;device.png" width = "100%" height = "100%" alt="图3.13中的 M2换为P管" align=center />
</div>

关于图16，作者给我们挖个坑，让我们思考：

他先是证明：

$$
A_v=-\sqrt{\frac{\mu_n(W/L)_1}{\mu_p(W/L)_2}} \tag{3.35}
$$

又因为

$$
\mu_nC_{ox}(\frac{W}{L})_1(V_{GS1}-V_{TH1})^2=\mu_pC_{ox}(\frac{W}{L})_2(V_{GS2}-V_{TH2})^2 \tag{3.36}
$$

得到：

$$
A_v=\frac{|V_{GS2}-V_{TH2}|}{V_{GS1}-V_{TH1}} \tag{3.37}
$$

但是，显而易见的是$$g_m=\mu_pC_{ox}(\frac{W}{L})(V_{GS}-V_{TH})$$：

$$
\begin{aligned}
|A_{v}|&=\frac{g_{m1}}{g_{m2}}\\
&=\frac{\mu_nC_{ox}(\frac{W}{L})_1(V_{GS1}-V_{TH1})}{\mu_pC_{ox}(\frac{W}{L})_2|V_{GS2}-V_{TH2}|}
\end{aligned} \tag{3.38}
$$

问题：为什么公式3.37和公式3.38，一个与$$｜V_{GS2}-V_{TH2}｜$$成正比，一个成反比呢，且对于$$(V_{GS1}-V_{TH1})$$也是如此？

回答：个人看来，|V_{GS2}-V_{TH2}|本身就不是自变量，是因变量，在同时含有自变量和因变量的表达式（而且两个变量本身的关系模型还比较复杂的情况），其实很难一眼看出具体的关系。如果将公式3.38除以公式3.37，正好得到公式3.36，就是因变量$$｜V_{GS2}-V_{TH2}｜$$和自变量$$V_{GS1}-V_{TH1}$$需要满足的关系式。所以$$A_{v}$$与$$｜V_{GS2}-V_{TH2}｜$$这个参数，既没有成正比，也没有成反比，只是在多个非独立的参数所表达的公式中，恰好有那样的关系式而已。若是真正的正比或者反比，应该有(正比)$$A_{v}=\alpha ｜V_{GS2}-V_{TH2}｜$$，其中$$\alpha$$是与$$｜V_{GS2}-V_{TH2}｜$$无关的常数。

Example 3.6 （20200301 下次有看到在自己推导一遍）

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.17&#32;Example&#32;3.6.png" width = "100%" height = "100%" alt="习题3.6" align=center />
</div>

图3.13中，若是考虑沟道长度调制效应，则增益为：

$$
A_u=-g_{m1}\left(\frac{1}{g_{m2}}||r_{o1}||r_{o2}\right) \tag{3.45}
$$

### 3.3.3 CS Stage with Current-Source Load

上面说的二极管接法或者电阻接法的CS stage，若要获得较大的增益，需要用更大的电阻，如$$R_D$$，带来其他问题，那就是输出负载导致的压降太大。这种情况可以用电流源负载来解决，如图3.18:

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.18&#32;CS&#32;stage&#32;with&#32;current-source&#32;load.png" width = "100%" height = "100%" alt="Figure 3.18 CS stage with current-source load" align=center />
</div>

那么就有：

$$
A_v=-g_{m1}(r_{o1}||r_{o2}) \tag{3.46}
$$

我们假设$$\lambda ∝ 1/L$$，这样的话，就有$$r_o ∝ L/I_D$$，又因为图3.18中的增益与$$r_{o1}||r_{o2}$$成正比，因此，L越长，增益越大。

M1和M2分开考虑，如果增加L1，那么我们也许要同比例增加W1。原因如下：1、给定的D电流，$$V_{GS1}-V_{TH1}∝1/\sqrt{(W/L)_1}$$，如果只是改L1，那么overdrive电压也会升高，限制输出电压摆幅；2、$$g_{m1}∝\sqrt{(W/L)_1}$$，单独增加L，会降低$$g_{m1}$$。

如果这些问题可以不考虑，那么我们就可以单独改变L1，而保持W1不变，那么M1的本征增益：

$$
g_{m1}r_{o1}=\sqrt{2\left(\frac{W}{L}\right)_1\mu_nC_{ox}I_D\frac{1}{\lambda I_D}} \tag{3.47}
$$

可以看出增益随着L增大而增大（因$$\lambda$$），$$g_{m1}r_{o1}$$随$$I_D$$的增加而降低。

### 3.3.4 CS Stage with Active Load 有源负载

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.20&#32;CS&#32;stage&#32;with&#32;active&#32;load.png" width = "100%" height = "100%" alt="图3.20 CS Stage with Active Load" align=center />
</div>

增益：

$$
A_v=-(g_{m1}+g_{m2})(r_{o1}||r_{o2}) \tag{3.48}
$$

但是这个电路有许多问题：如电源抑制比很差

$$
\begin{aligned}
\frac{V_{out}}{V_{DD}}&=\frac{g_{m2}r_{o2}+1}{r_{o2}+r_{o1}}r_{o1}\\
&=\left(g_{m2}+\frac{1}{r_{o2}}\right)(r_{o2}||r_{o1})
\end{aligned} \tag{3.49 3.50}
$$

其中3.49的由来根据$$V_{out}$$节点的电流可以得到：

$$
V_{out}/r_{o1}=\frac{V_{DD}-V_{out}}{r_{o2}}+g_{m2}V_{DD}
$$

可以看出Vout与VDD的关系约为$$A_v$$的一半，太高了！

### 3.3.5 CS Stage with Triode Load

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.22&#32;CS&#32;stage&#32;with&#32;triode&#32;load.png" width = "100%" height = "100%" alt="图3.22 CS stage with triode load" align=center />
</div>

$$
R_{on2}=\frac{1}{\mu_pC_{ox}(W/L)_2(V_{DD}-V_b-|V_{THP}|)} \tag{3.51}
$$

Among the five CS variants studied above, those employing resistive, current-source, or active loads find wider usage than the other two (diode connect, Triode Load).

### 3.3.6 CS Stage with Source Degeneration

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.23&#32;CS&#32;stage&#32;with&#32;source&#32;degeneration.png" width = "100%" height = "100%" alt="图3.23 CS stage with source degeneration" align=center />
</div>

推导得到：

$$
A_v=-\frac{g_mR_D}{1+g_mR_S} \tag{3.57}
$$

添加body effect和channel-length modulation

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.24&#32;Small-signal&#32;equivalent&#32;circuit&#32;of&#32;a&#32;degenerated&#32;CS&#32;stage.png" width = "100%" height = "100%" alt="图 3.24 Small-signal equivalent circuit of a degenerated CS stage" align=center />
</div>

**问题：** 剩下的一些公式推导，后续再次推导并在此补全。

## 3.4 Source Follower (“common-drain” stage)

source follower意义：作为输出，降低输出阻抗。

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.34&#32;source&#32;follower.png" width = "100%" height = "100%" alt="图3.34 source Follower" align=center />
</div>

忽略沟道长度调制效应，有：

$$
\begin{aligned}
\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH}-V_{out})^2R_S=V_{out}
\end{aligned} \tag{\3.82}
$$

计算小信号增益：

$$
\begin{aligned}
\frac{1}{2}\mu_nC_{ox}\frac{W}{L}2(V_{in}-V_{TH}-V_{out})\big(1-\frac{\partial V_{TH}}{\partial V_{in}}-\frac{\partial V_{out}}{\partial V_{in}}\big)R_S=\frac{\partial V_{out}}{\partial{V_{in}}}
\end{aligned} \tag{3.83}
$$

因：$$\partial{V_{TH}}/\partial{V_{in}}=(\partial{V_{TH}}/\partial{V_{SB}})(\partial{V_{SB}}/\partial{V_{in}})=\eta\partial{V_{out}}/\partial{V_{in}}$$，有：

$$
\begin{aligned}
\frac{\partial{V_{out}}}{\partial{V_{in}}}=\frac{\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH}-V_{out})R_S}{1+\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH}-V_{out})R_S(1+\eta)}
\end{aligned} \tag{3.84}
$$

将如下公式带入(如下公式从何而来)

$$
\begin{aligned}
g_m=\mu_nC_{ox}\frac{W}{L}(V_{in}-V_{TH}-V_{out})
\end{aligned} \tag{3.85}
$$

有：

$$
\begin{aligned}
A_v=\frac{g_mR_S}{1+(g_m+g_{mb})R_S}
\end{aligned} \tag{3.86}
$$

但如果应用小信号等效模型，我们将可以很快得到这个结论（算Rs电流等于gmV1以及gmbVbs的和）：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.35&#32;Small-signal&#32;equivalent&#32;circuit&#32;of&#32;source&#32;follower.png" width = "100%" height = "100%" alt="图3.35 Small-signal equivalent circuit of source follower" align=center />
</div>

实际全范围增益曲线：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.36&#32;Voltage&#32;gain&#32;of&#32;source&#32;follower&#32;versus&#32;input&#32;voltage.png" width = "100%" height = "100%" alt="Figure 3.36 Voltage gain of source follower versus input voltage" align=center />
</div>

为了减小电流差异导致的$$V_{GS}$$电压的变化，影响增益，我们可以用电流源替代$$R_S$$。

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.37&#32;Source&#32;follower&#32;using&#32;current&#32;source.png" width = "100%" height = "100%" alt="Figure 3.37 Source follower using (a) an ideal current source, and (b) an NMOS transistor as a current source" align=center />
</div>
** Example3.12 ** 下次再推演公式。

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Example&#32;3.12.png" width = "100%" height = "100%" alt="Example 3.12" align=center />
</div>

计算source follower 的输出阻抗：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.39&#32;Calculation&#32;of&#32;the&#32;output&#32;impedance&#32;of&#32;a&#32;source&#32;follower.png" width = "100%" height = "100%" alt="Figure 3.39Calculation of the output impedance of a source follower" align=center />
</div>

$$
\begin{aligned}
I_x-g_mV_{X}-g_{mb}V_{X}=0
\end{aligned} \tag{3.90}
$$

因此：

$$
\begin{aligned}
R_{out}=\frac{1}{g_{m}+g_{mb}}
\end{aligned} \tag{3.91}
$$

也就是说：

$$
\begin{aligned}
R_{out}&=\frac{1}{g_m}||\frac{1}{g_{mb}}\\
&=\frac{1}{g_{m}+g_{mb}}
\end{aligned} \tag{3.92 3.93}
$$

其实就是将$$1/g_{mb}$$看成一个电阻，如下图：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.40&#32;Source&#32;follower&#32;including&#32;body&#32;effect.png" width = "100%" height = "100%" alt="Figure 3.40 Source follower including body effect" align=center />
</div>

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.41&#32;Representation&#32;of&#32;intrinsic&#32;source&#32;follower&#32;by&#32;a&#32;Thevenin&#32;equivalent.png" width = "100%" height = "100%" alt="Figure 3.41 Representation of intrinsic source follower by a Thevenin equivalent" align=center />
</div>

$$
\begin{aligned}
A_v&=\frac{\frac{1}{g_{mb}}}{\frac{1}{g_m}+\frac{1}{g_{mb}}}\\
&=\frac{g_m}{g_{m}+g_{mb}}
\end{aligned} \tag{3.94 3.95}
$$

推而广之：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.42&#32;Source&#32;follower&#32;driving&#32;load&#32;resistance.png" width = "100%" height = "100%" alt="Figure 3.42 Source follower driving load resistance" align=center />
</div>

$$
\begin{aligned}
A_v&=\frac{R_{eq}}{R_{eq}+\frac{1}{g_{m}}}
\end{aligned} \tag{3.96}
$$

如何消除body effect，用两个P管，DB相连，如下：

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/Figure&#32;3.44&#32;PMOS&#32;source&#32;follower&#32;with&#32;no&#32;body&#32;effect.png" width = "100%" height = "100%" alt="Figure 3.44 PMOS source follower with no body effect" align=center />
</div>

## 3.5 Common-Gate Stage

<div  align="center">
<img src="./.assets/Chapter-3-Single-Stage-Amplifiers/figure&#32;3.48&#32;common-gate&#32;stage.png" width = "100%" height = "100%" alt="figure 3.48 common-gate stage" align=center />
</div>

## 3.6 Cascode Stage

### 3.6.1 Folded Cascode

## 3.7 Choice of Device Models

## The END
