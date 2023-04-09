# RC滤波器计算

## RC电路阶跃响应

$$
\begin{aligned}
I_R = \frac{V_R}{R}
\end{aligned}
$$

$$
\begin{aligned}
I_C = C \frac{dV_c}{dt}
\end{aligned}
$$

$$
\begin{aligned}
V_R + V_C = V_{IN}
\end{aligned}
$$

$$
\begin{aligned}
I_R = I_C
\end{aligned}
$$

求输出$$V_{out} = V_C$$

根据上面4条公式有：

$$
\begin{aligned}
C \frac{dV_c}{dt} = I_C = I_R \
& = \frac{V_R}{R} \
& = \frac{V_{IN} - V_C}{R}
\end{aligned}
$$

有：

$$
\begin{aligned}
RC \frac{dV_c}{dt} + V_C = V_{IN}
\end{aligned}
$$

解方程得到：

$$
\begin{aligned}
V_{out} &= V_C \
&=V_{IN}*(1-e^{-t/RC})
\end{aligned}
$$

## 二阶RC的阶跃响应分析

将$$V_{out} = V_{IN}*(1-e^{-t/RC})$$ 作为第二阶RC电路的输入，也就是替代公式 $$ RC \frac{dV_c}{dt} + V_C = V_{IN} $$ 中的 $$V_{IN}$$， 得到：

$$
\begin{aligned}
RC \frac{dV_c}{dt} + V_C = V_{IN}*(1-e^{-t/RC})
\end{aligned}
$$

该方程如何求解？

## 参考及引用
