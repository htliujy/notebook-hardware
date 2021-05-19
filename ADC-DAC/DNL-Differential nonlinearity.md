# DNL-Differential nonlinearity

微分非线性，评估ADC和DAC的性能指标之一，评估的是，每1LSB(Least Significant Bit)对应的模拟量是否是相等的，偏差程度如何<sup>[1]</sup>。

与之对应的，微分线性（Differential linearity）代表恒定的输入与输出变化关系。

公式：

$$
\begin{aligned}
\mathrm{DNL}(\mathrm{i})=\frac{V_{\text {out }}(i+1)-V_{\text {out }}(i)}{\text { ideal LSB step width }}-1
\end{aligned}\tag{1.0}
$$

图片示意：

<div  align="center">
<img src="./DNL-Differential%20nonlinearity/Differential_linearity.svg" width = "100%" height = "100%" alt="图片" align=center />
</div>

Demonstrates A. Differential Linearity where a change in the input produces a corresponding change in output and B. Differential Non-linearity, where the relationship is not directly linear.

DNL影响：

- If the DNL of an ADC is smaller than -1, missing codes appear in the transfer function, i.e. there are codes for which there is no input voltage to get the at the ADC output.
- If the DNL of a DAC is bigger than 1, the transfer function of the DAC becomes non-monotonic. A non-monotonic DAC is especially not desired in closed-loop control application as it may cause stability problems, i.e. it may cause oscillations.

参考及引用：

[1] Wikipedia-Differential nonlinearity <https://en.wikipedia.org/wiki/Differential_nonlinearity>