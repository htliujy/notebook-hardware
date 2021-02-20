# Howland Current Source

豪兰德电流源

先直接分析，然后再说优劣吧！

如下图，是否是为了小电流的恒流源而设计的呢？

<div  align="center">
<img src="./Howland%20Current%20Source/howland_circuit.png" width = "80%" height = "80%" alt="图1豪兰德电流源" align=center />
</div>

假设运放是理想运放，满足输入阻抗无穷大，增益无穷大，根据R1和R2的分压原理，有：

$$
\begin{align}
V_{out} = V_{in}(\frac{R_1+R_2}{R_1})
\end{align}\tag{1.0}
$$

负载电流等于流过R3和R4的电流叠加：

$$
\begin{align}
I_L = \frac{V_{out}-V_{in}}{R_3}+\frac{V_{ref}-V_{in}}{R_4}
\end{align}\tag{1.1}
$$

以及：

$$
\begin{align}
I_L = \frac{V_{in}}{R_L}
\end{align}\tag{1.2}
$$

从公式1.1和公式1.0可以推导出：

$$
\begin{align}
I_L = \frac{V_{in}R_2}{R_3 R_1}-\frac{V_{in}}{R_4}+\frac{V_{ref}}{R_4}
\end{align}\tag{1.3}
$$

同时将公式(1.2)代入（1.3）得到：

$$
\begin{align}
I_L &= \frac{I_L R_L R_2}{R_3 R_1}-\frac{I_L R_L}{R_4}+\frac{V_{ref}}{R_4}\\
&= \frac{V_{ref}}{R_4} + I_L R_L(\frac{R_2}{R_3 R_1}-\frac{1}{R_4})
\end{align}\tag{1.4}
$$

因此，当$$\frac{R_2}{R_3 R_1}=\frac{1}{R_4}$$时：

$$
\begin{align}
I_L = \frac{V_{ref}}{R_4}
\end{align}\tag{1.5}
$$

可以发现，此时，$$I_L$$与$$R_L$$无关，是个恒流源。  
但是，用公式表达太抽象了，若是可以用原理来解释，就会更清晰，电路原理分析如下图：

<div  align="center">
<img src="./Howland%20Current%20Source/Howlandcurrentsource-operation.jpg" width = "80%" height = "80%" alt="Howlandcurrentsource-operation" align=center />
</div>

豪兰德模型分析：

1. 假设$$R_1 = R_2 = R_3 = R_4 = R $$；
2. 那么根据$$R_1$$和$$R_2$$的分压，有$$V_{out} = 2V_{in}$$;
3. 那么流过$$R_3$$的电流为： $$I_{R3}=(V_{out}-V_{in})/R_3 = V_{in}/R$$
4. 流过$$R_4$$的电流：$$I_{R4} = (V_{ref} - V_{in})/R = V_{ref}/R-V_{in}/R$$
5. 因此有：$$I_L = I_{R3}+I_{R4} = V_{ref}/R$$


豪兰德等效模型

<div  align="center">
<img src="./Howland%20Current%20Source/howland电流源模型分析.jpg" width = "80%" height = "80%" alt="豪兰德等效模型" align=center />
</div>

疑问：

1. 下面公式如何推导出来？
    $$
    \begin{align}
    V_{o u t}=\frac{R_{3} R_{L} V_{R E F}}{R_{4} R_{L}-\frac{R 1}{R 1+R 2} R_{4} R_{L}-\frac{R 1}{R 1+R 2} R_{3} R_{L}+\frac{R 1}{R 1+R 2} R_{3} R_{4}}
    \end{align}
    $$

2. 输出阻抗如何评估及计算?
    以上推导都是基于电阻完全相等（没有偏差），运放输入偏置为0，运放增益无穷大，但实际模型并不能达到，请问这个时候，应该如何计算偏差值，以及输出阻抗？
3. 恒流源拓扑还有哪些？
4. 和其他恒流源相比，豪兰德的优点和缺点是什么？

参考及引用：

[1] 《你好，放大器》杨建国，西安交通大学
