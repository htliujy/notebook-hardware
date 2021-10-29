# 分贝dB相关定义

分贝（Decibel<sup>[1]</sup>）：

问题：分贝数dB的计算，什么时候用$$10log \left( signal \right)$$，什么时候用$$20log \left( signal \right)$$？

答：幅度用$$20log$$，功率用$$10log$$.

## dBc

dBc<sup>[2]</sup>:

**dBc (decibels relative to the carrier)** is the power ratio of a signal to a carrier signal, expressed in decibels. For example, phase noise is expressed in dBc/Hz at a given frequency offset from the carrier. dBc can also be used as a measurement of Spurious-Free Dynamic Range (SFDR) between the desired signal and unwanted spurious outputs resulting from the use of signal converters such as a digital-to-analog converter or a frequency mixer.

If the dBc figure is positive, then the relative signal strength is greater than the carrier signal strength. If the dBc figure is negative, then the relative signal strength is less than carrier signal strength.

### 举例

If a carrier ( reference signal ) has a power of $$C = 0.1 mW$$, and noise signal has power of $$S = 10 μW$$.

那么信号的大小用分贝数表示为：

$$
\begin{aligned}
P_{\mathrm{C}}=10 \log \left(\frac{0.1 \mathrm{~mW}}{1 \mathrm{~mW}}\right)=-10 \mathrm{dBm}
\end{aligned}
$$

噪声的大小用分贝数表示为:

$$
P_{\mathrm{S}}=10 \log \left(\frac{10 \mu \mathrm{W}}{1 \mathrm{~mW}}\right)=-20 \mathrm{dBm}
$$

那么就可以计算出参考信号和噪声之间的相对值$\mathrm{dBc}$：

$$
P_{\mathrm{S}}-P_{\mathrm{C}}=-20 \mathrm{dBm}-(-10 \mathrm{dBm})=-10 \mathrm{dBc}
$$

可以不用分贝数，直接用功率值计算：

$$
P_{\mathrm{S}}-P_{\mathrm{C}}=10 \log \left(\frac{\mathrm{S}}{\mathrm{C}}\right)=10 \log \left(\frac{10 \mu \mathrm{W}}{0.1 \mathrm{~mW}}\right)=-10 \mathrm{dBc}
$$

## 参考及引用

[1] Decibel. Wikipedia. <https://en.wikipedia.org/wiki/Decibel>.
[2] dBc. Wikipedia. <https://en.wikipedia.org/wiki/DBc>.
