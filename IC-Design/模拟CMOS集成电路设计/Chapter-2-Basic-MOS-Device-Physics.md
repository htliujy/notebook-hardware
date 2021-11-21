---
title: Chapter 2 Basic MOS Device Physics
date:  20200221 18:00:00
categories: 模拟CMOS集成电路设计
tags: 
 - 读书笔记
mathjax: true
---
# Chapter 2 Basic MOS Device Physics

## 2.1 通识

## 2.2 IV曲线

### 2.2.1阈值电压

$$
V_{TH}=\varPhi_{MS} + 2\varPhi_F+\frac{Q_{dep}}{C_{ox}} \tag{2.1}
$$

其中：

- $$\varPhi_{MS}$$是gate多晶硅和硅衬底之间的功函数的差;
- $$\varPhi_F=(kT/q)ln(N_{sub}/n_i)$$, *k*玻尔兹曼常量，$$N_{sub}$$是衬底的参杂浓度, $$n_i$$是本征半导体的电子浓度;  
- $$Q_{dep}$$是耗尽区的电荷,$$Q_{dep}=\sqrt{4q\epsilon_{si}|\varPhi_F|N_{sub}}$$,$$\epsilon_{si}$$是介电常数;  
- $$C_{ox}$$是gate电容密度($$C/m^2$$),在厚度$$t_{ox}=20Å$$的情况下，$$C_{ox} \approx 17025fF/\mu m^{2}$$, The value of $$C_{ox}$$ can then be scaled proportionally for other oxide thicknesses（线性调整，应该是反比吧！能这么描述么？）。

### 2.2.2 I/V特征派生

柱形导体中的电流，其中$$Q_d$$为单位长度中的电荷量。

$$
I=Q_d·v \tag{2.2}
$$

在MOS中：  

$$
Q_d = WC_{ox}(V_{GS}-V_{TH}) \tag{2.3}
$$

因为D极和S极的电压其实不一致，那么有：  

$$
Q_d(x) = W C_{ox}[V_{GS}-V(x)-V_{TH}] \tag{2.4}
$$

$$
I_D = -W C_{ox}[V_{GS}-V(x)-V_{TH}]v \tag{2.5}
$$

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/figure&#32;2.10&#32;channel&#32;chage&#32;.png" width = "50%" height = "50%" alt="沟道电荷分布" align=center />
</div>

因为$$v=\mu * E$$ 以及$$E(x) = -dV/dx$$, 有：

$$
Id = W C_{ox}(V_{GS}-V(x)-V_{TH})\mu_n\frac{dV(x)}{dx} \tag{2.6}
$$

根据公式2.5有：

$$
\displaystyle \int^{L}_{x=0}I_ddx = \int^{V_{DS}}_{V=0}WC_{ox}(V_{GS}-V(x)-V_{TH})\mu_ndV\tag{2.7}
$$

积分推导，得到(20200221推导验证)：

 $$
 I_D=\mu_nC_{ox}\frac{W}{L}[(V_{GS}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}]\tag{2.8}
 $$

 **注意L是有效长度**
图2.11就是上面公式的抛物曲线，可以知道，当$$V_{DS}=V_{GS}-V_{TH}$$时，的到电流最大值(求导数$${\partial{I_D}}/{\partial{V_{GS}}}$$)：

$$
I_{D,max}= \frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})^2 \tag{2.9}
$$

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/figure&#32;2.11&#32;Drain&#32;&#32;current&#32;versus&#32;drain-source&#32;voltage&#32;in&#32;the&#32;triode&#32;region.png" width = "100%" height = "100%" alt="漏极电流与漏极电压的关系曲线" align=center />
</div>

这样，我们得到**过驱动电压（overdrive voltage）**$$V_{DS}=V_{GS}-V_{TH}$$,以及平面特征（aspect ratio）宽长比。

**三极管区：** 如果$$V_{DS}≤(V_{GS}-V_{TH})$$，那么我们就说器件进入三极管区。

**线性区：** 如果$$V_{DS}≪(V_{GS}-V_{TH})$$，那么我们就说器件进入线性区，因为(是否可以叫电阻区)：

$$
I_D≈\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})V_{DS}\tag{2.10}
$$

此时，MOS的电阻值为：

$$
R_{on}=\frac{1}{\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})}\tag{2.11}
$$

在这个区域内，**MOS可以看成是压控电阻，这很重要，** 后续我们需要用到这个功能。

**饱和区：** 在$$V_{DS}>(V_{GS}-V_{TH})$$时，电流并不满足抛物曲线（figure2.11），而是出现**夹断效应**，进入饱和区，且，当$$V_{DS}$$增大时，夹断区会逐渐往S极移动。如图2.16：

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.16&#32;Pinch-off&#32;behavior.png" width = "100%" height = "100%" alt="Pinch-off behavior" align=center />
</div>

若$$L^′$$是图2.16中的有效沟道长度，将公式2.7变形，得到：

$$
\displaystyle \int^{L^′}_{x=0}I_ddx = \int^{V_{GS}-V_{TH}}_{V=0}WC_{ox}(V_{GS}-V(x)-V_{TH})\mu_ndV\tag{2.7.1}
$$

推导，得到：

$$
I_D=\frac{1}{2}\mu_nC_{ox}\frac{W}{L^′}(V_{GS}-V_{TH})^2\tag{2.13}
$$

为横流区，电流基本不随$$V_{DS}$$变化。

**疑问：** 为何耗尽区的长度相对于$$L$$很小，为何耗尽区能走电流，何来的载流子？

**答疑：** ？

公式(2.13)是从$$V_{GS}$$得到$$I_{D}$$，反过来，可以从确定的横流电流$$I_{D}$$得到$$V_{GS}$$，为：

$$
V_{GS}=\sqrt{\frac{2I_D}{\mu_nC_{ox}\frac{W}{L^′}}}+V_{TH} \tag{2.14}
$$

实际的电流如图2.15:

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.15&#32;Saturation&#32;of&#32;drain&#32;current.png" width = "100%" height = "100%" alt="Saturation of drain current" align=center />
</div>

由以上分析可知$$V_{D,sat}=V_{GS}-V_{TH}$$是进入横流模式的最低D极电压，$$V_D$$越大，那么在电路中留给其他电路的电压摆幅（voltage headroom）范围将会更窄（这是我们不希望看到的）。

对于PMOS，将公式（2.8)和公式(2.13)改写为：

**三极管区：**

$$
I_D=-\mu_pC_{ox}\frac{W}{L}[(V_{GS}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}]\tag{2.15}
$$

**饱和区：**

$$
I_D=-\frac{1}{2}\mu_pC_{ox}\frac{W}{L^′}(V_{GS}-V_{TH})^2\tag{2.16}
$$

空穴移动方向与电场一致，电流方向与空穴一致。

### 2.2.3 MOS跨导

跨导（transconductance）$$ g_m $$，一般是定义在饱和区，定义如下：

$$
\begin{aligned}
g_m &= \frac{\partial{I_D}}{\partial{V_{GS}}}|_{VDS const} \\
&=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH}) \\
\end{aligned} \tag{2.17 2.18}
$$

若是用$$I_D$$表达，根据公式2.13和2.14有：

$$
\begin{aligned}
g_m &=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})\\
&=\mu_nC_{ox}\frac{W}{L}\sqrt{\frac{2I_D}{\mu_nC_{ox}\frac{W}{L^′}}} \\
&=\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}\\
&=\frac{2I_D}{V_{GS}-V_{TH}}
\end{aligned} \tag{2.19 2.20}
$$

那跨导跟几个参数的关系如下图（2.20）
<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.20&#32;Approximate&#32;MOS&#32;transconductance&#32;as&#32;a&#32;function&#32;of&#32;overdrive&#32;and&#32;drain&#32;current.png" width = "100%" height = "100%" alt="Approximate MOS transconductance as a function of overdrive and drain current" align=center />
</div>

**Example 2.3** 画出跨导随$$V_{DS}$$的变化趋势，如下图：

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.21.png" width = "100%" height = "100%" alt="跨导随$$V_D$$电压的趋势曲线" align=center />
</div>

当$$V_{DS}≤(V_{GS}-V_{TH})$$时，MOS管处于**三极管区**，此时：

$$
\begin{aligned}
g_m &=\frac{\partial}{\partial V_{GS}}\{\mu_nC_{ox}\frac{W}{L}[(V_{GS}-V_{TH})V_{DS}-\frac{1}{2}V_{DS}^{2}]\}\\
&=\mu_nC_{ox}\frac{W}{L}V_{DS}
\end{aligned} \tag{2.20 2.21}
$$

当$$V_{DS}>(V_{GS}-V_{TH})$$时，进入饱和区，此时见公式（2.18）：$$g_m=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})$$，可见$$g_m$$相对于$$V_{DS}$$为常数。

## 2.3 二次效应(Second-order effects)

**Body Effects 体效应**bulk与S极之间有电压差，导致阈值电压偏离。

疑问，在有B极连接的情况下（BS）相连，如果SD反接（也就是BD正偏），那么将会如何，有电流，跟垂直沟道的功率MOS的体二极管，有怎样的差异？

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.22&#32;NMOS&#32;device&#32;with&#32;negative&#32;bulk&#32;voltage.png" width = "100%" height = "100%" alt="NMOS bulk 模型" align=center />
</div>

体效应现象：
<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.23&#32;Variation&#32;of&#32;depletion&#32;region&#32;charge&#32;with&#32;bulk&#32;voltage.png" width = "100%" height = "100%" alt="体效应" align=center />
</div>

加入体效应后的阈值电压为：

$$
V_{TH}=V_{TH0}+\gamma(\sqrt{2\varPhi_F+V_{SB}}-\sqrt{|2\varPhi_F|}) \tag{2.23}
$$

其中:

- $$V_{TH0}$$见公式（2.1），$$V_{TH}=\varPhi_{MS} + 2\varPhi_F+\frac{Q_{dep}}{C_{ox}}$$；
- $$\gamma=\sqrt{2q\epsilon_{si}N_{sub}}/C_{ox}$$,是体效应系数；

**Example 2.4**画漏极电流与bulk电压关系曲线

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.24&#32;Example&#32;2.4.png" width = "100%" height = "100%" alt="例题2.4" align=center />
</div>

解：
a、当$$V_{TH}$$大于1.2V时，M1关闭，解方程

$$
1.2V=0.3V+0.4V^{1/2}(\sqrt{0.7V+V_{SB}}-\sqrt{0.7V})
$$

得到$$V_{SB}=8.827V$$，因此，当$$V_{SB}>8.827V$$时，M1处于关闭状态；

b、当$$V_{SB}=8.827V$$时，M1处于临界导通状态；

c、又因为当$$V_{SB}=0V$$时(此时不用计算也知道$$V_{TH}=V_{TH0}=0.3V$$)：

$$
\begin{aligned}
V_{TH}&=V_{TH0}+\gamma(\sqrt{2\varPhi_F+V_{SB}}-\sqrt{|2\varPhi_F|})\\
&=0.3V+0.4V^{1/2}(0)
&=0.3V
\end{aligned}
$$

因此有$$V_{DS}=2V>(V_{GS}-V_{TH})$$，器件仍然处于横流区，也就是$$0V<V_{SB}=8.827V$$时，器件处于横流区，见公式2.13，电流大小为：

$$
\begin{aligned}
I_{D}&=\frac{1}{2}\mu_nC_{ox}\frac{W}{L}[V_{GS}-V_{TH0}-\gamma(\sqrt{2\varPhi_F+V_{SB}}-\sqrt{|2\varPhi_F|})]^2
\end{aligned}
$$

**Channel-Length Modulation 沟道长度调制效应**:当$$V_D$$电压升高时，有效沟道长度减少，写成$$L^′=L-\varDelta L$$，有$$1/L^′≈(1+\varDelta L/L)/L$$,若假设$$\varDelta L/L$$与$$V_{DS}$$成线性关系，如：$$\varDelta L/L=\lambda V_{DS}$$,那么，根据公式，就有

$$
\begin{aligned}
I_D&=\frac{1}{2}\mu_nC_{ox}\frac{W}{L^′}(V_{GS}-V_{TH})^2\\
&≈\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})^2(1+\lambda V_{DS})
\end{aligned}\tag{2.27}
$$

课本中没有解释清楚一个结论，$$L$$越大，$$\lambda$$越小。个人自观感受是：在特定的$$\varDelta V_{DS}$$下，$$\varDelta L$$的大小与$$L$$长度的大小相关系数很小。那么就有$$L$$大，而$$\varDelta L$$基本不变的情况下，则$$\varDelta L/L$$小。

另外，跨导$$g_m$$需重新表达，原来：

$$
\begin{aligned}
g_m &= \frac{\partial{I_D}}{\partial{V_{GS}}}|_{VDS const} \\
&=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH}) \\
\end{aligned} \tag{2.17 2.18}
$$

$$
\begin{aligned}
g_m &=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})\\
&=\mu_nC_{ox}\frac{W}{L}\sqrt{\frac{2I_D}{\mu_nC_{ox}\frac{W}{L^′}}} \\
&=\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}\\
&=\frac{2I_D}{V_{GS}-V_{TH}}
\end{aligned} \tag{2.19 2.20}
$$

重新表达为：
$$
\begin{aligned}
g_m &=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})(1+\lambda V_{DS})\\
&=\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D(1+\lambda V_{DS})}\\
&=\frac{2I_D}{V_{GS}-V_{TH}}
\end{aligned} \tag{2.30 2.31 2.20}
$$

其中公式2.20未变：

$$
g_m=\frac{2I_D}{V_{GS}-V_{TH}} \tag{2.20}
$$

The dependence of ID upon VDS in saturation may suggest that the bias current of a MOSFET can be defined by the proper choice of the drain-source voltage, allowing freedom in the choice of VGS − VTH . However, since the dependence on VDS is much weaker, the drain-source voltage is not used to set the current. That is, we always consider VGS − VTH as the current-defining parameter. The effect of VDS on ID is usually considered an error, and it is studied in Chapter 5.

**Subthreshold Conduction 亚阈值导通**，在$$V_{DS}$$电压达到$$V_{TH}$$之前，其实就有电流开始流过DS，虽然$$I_D$$很小，但是它随着$$V_{GS}$$的增加呈指数增长，可大体上表述为如下公式：

$$
I_D=I_0exp\frac{V_{GS}}{\xi V_T} \tag{2.33}
$$

其中：

- $$I_0∝W/L$$；
- $$\xi>1$$，是个非理想因子（何为非理想因子nonideality factor？）；
- $$V_T=kT/q$$，当T=293K（20摄氏度）时，$$V_T=2.52mV$$。

在亚阈值导通的影响下，我们需要关闭时的$$V_{GS}$$电压远小于$$V_TH$$（但在正常使用中，闭合时$$V_{GS}=0V$$，这就要求$$V_{TH}$$不能太低），这样才能保证闭合时的漏电流$$I_D$$很小。

**Voltage Limitations 电压限制**：G极耐压及击穿限制，D的电压太高时会使得耗尽区达到S极，从而会有极大的漏极电流（This effect is called “punchthrough.”），等等，这些效应见7章。

## 2.4 MOS器件模型

### 2.4.1 layout

见下图：

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.29&#32;Bird’s-eye&#32;and&#32;vertical&#32;views&#32;of&#32;a&#32;MOS&#32;device.png" width = "100%" height = "100%" alt="单个MOS layout" align=center />
</div>


<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.30&#32;Example&#32;2.9.png" width = "100%" height = "100%" alt="多个MOS" align=center />
</div>

### MOS Device Capacitances

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.31&#32;MOS&#32;capacitances.png" width = "50%" height = "50%" alt="电容在电路符号中的表征" align=center />
</div>

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure%202.32%20MOS电容在layout中的体现.png" width = "80%" height = "80%" alt="MOS电容在layout中的体现" align=center />
</div>

**存疑：**寄生电容的具体公式表征如何？

**Example 2.10**折叠结构的电容改变

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.33.png" width = "70%" height = "70%" alt="折叠器件的电容" align=center />
</div>

**提示：**$$C_{DB}$$ will be smaller than origin device, and $$C_{SB}$$ will be lager.

随着$$V_{GS}$$增加，$$C_{GD}$$和$$C_{GS}$$的变化趋势如何？

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.34&#32;Variation&#32;of&#32;gate-source&#32;and&#32;gate-drain&#32;capacitances&#32;versus&#32;VGS.png" width = "100%" height = "100%" alt="$$C_{GD}$$和$$C_{GS}$$的变化趋势" align=center />
</div>

**疑问：** 为什么$$WLC_{ox}$$的系数是2/3？

### 2.4.3 MOS小信号模型

输出电阻$$r_o$$，在横流区，如下图：

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.37&#32;small-signal&#32;model.png" width = "100%" height = "100%" alt="MOS小信号模型" align=center />
</div>

根据恒流区电流公式（2.27），可以知道

$$
\begin{aligned}
I_D&=\frac{1}{2}\mu_nC_{ox}\frac{W}{L^′}(V_{GS}-V_{TH})^2\\
&≈\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})^2(1+\lambda V_{DS})
\end{aligned} \tag{2.27}
$$

$$
\begin{aligned}
r_o&=\frac{\partial V_{DS}}{\partial I_D}\\
&=\frac{1}{\partial I_D/\partial V_{DS}}\\
&=\frac{1}{\frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})^2·\lambda}\\
&≈\frac{1+\lambda V_{DS}}{\lambda I_D}\\
&≈\frac{1}{\lambda I_D}
\end{aligned} \tag{2.44-2.48}
$$

将bulk的电势影响考虑进去，也就是B极考虑成另一个gate（门），也调制了漏源电流，我们将之写为$$g_{mb}V_{bs}$$，其中$$g_{mb}=\partial I_D/\partial V_{BS}$$，在饱和区：

参考2.9及2.13（考虑沟道长度调制效应）：

$$
I_{D,max}= \frac{1}{2}\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})^2 \tag{2.9}
$$

$$
I_D=\frac{1}{2}\mu_nC_{ox}\frac{W}{L^′}(V_{GS}-V_{TH})^2\tag{2.13}
$$

参考（2.23）

$$
V_{TH}=V_{TH0}+\gamma(\sqrt{2\varPhi_F+V_{SB}}-\sqrt{|2\varPhi_F|}) \tag{2.23}
$$

那么$$g_{mb}$$为：

$$
\begin{aligned}
g_{mb}&=\frac{\partial I_{D}}{\partial V_{BS}}\\
&=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})(-\frac{\partial V_{TH}}{\partial V_{BS}})
\end{aligned}\tag{2.49 2.50}
$$

其中：

$$
\begin{aligned}
\frac{\partial V_{TH}}{\partial V_{BS}}&=-\frac{\partial V_{TH}}{\partial V_{SB}}\\
&=-\frac{\gamma}{2}(2\varPhi_F+V_{SB})^{-1/2}
\end{aligned}\tag{2.51 2.52}
$$

Thus,

$$
\begin{aligned}
g_{mb}&=\frac{\partial I_{D}}{\partial V_{BS}}\\
&=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})(-\frac{\partial V_{TH}}{\partial V_{BS}})
\end{aligned}\tag{2.49 2.50}
$$

又因为：

$$
\begin{aligned}
g_m &=\mu_nC_{ox}\frac{W}{L}(V_{GS}-V_{TH})\\
&=\mu_nC_{ox}\frac{W}{L}\sqrt{\frac{2I_D}{\mu_nC_{ox}\frac{W}{L^′}}} \\
&=\sqrt{2\mu_nC_{ox}\frac{W}{L}I_D}\\
&=\frac{2I_D}{V_{GS}-V_{TH}}
\end{aligned} \tag{2.19 2.20}
$$

所以有：

$$
\begin{aligned}
g_{mb}&=g_m\frac{\gamma}{2\sqrt{2\varPhi_F+V_{SB}}}\\
&=\eta g_m
\end{aligned}\tag{2.53 2.54}
$$

其中，$$\eta=g_{mb}/g_m$$，典型值为0.25，从公式2.53可以看出，当$$V_{SB}$$增加时，$$g_mb$$降低。

**Example 2.12** $$g_m$$和$$g_{mb}$$随$$I_1$$的变化趋势？

<div  align="center">
<img src="./.assets/Chapter-2-Basic-MOS-Device-Physics/Figure&#32;2.40.png" width = "100%" height = "100%" alt="$$g_m$$和$$g_{mb}$$随$$I_1$$的变化趋势" align=center />
</div>

公式：？？？

## 2.5 附录A：FinFETs

## 2.6 附录B

## The End
