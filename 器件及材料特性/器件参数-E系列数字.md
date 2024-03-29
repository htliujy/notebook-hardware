# 器件参数-E系列数字

在器件参数选型时，如贴片电阻，经常看到E24，E48这样的数值表，这些数值都是怎样分布的？

E系列（E-series）是电子学中常用的从优数，包括E3、E6、E12、E24、E48、E96及E192等系列<sup>[1]</sup><sup>[2]</sup>。

例如E12就是将大于等于1，小于10的数字中选出适当的12个数字，使所有1到10之间的数字在一定的比例范围内(E12系列是10%)，都可以找到一个E12系列中的数字。

这样做，既方便了元器件的生产企业，也方便了元器件应用的研发。

按照精度的要求，厂家预先可以批量生产覆盖整个应用区间的参数。

因为这些值在特定的精度要求下，总是覆盖十倍的数字区间（十倍数值后又开始用同样的十倍的对应数值去覆盖）。
E6系列，1、1.5、2.2、3.3、4.7、6.8：能够满足 $$20%$$ 的精度要求:

- 1±20%: 0.8-1.2
- 1.5±20%: 1.2-1.8
- 2.2±20%: 1.76-2.64
- 3.3±20%: 2.64-3.96
- 4.7±20%: 3.76-5.64
- 6.8±20%: 5.44-8.16

完整覆盖了0.8-8.0（其实是8.16）这十倍的数值区间，那么生产企业生产出的产品就不用浪费了，反正都能满足E6系列某个阻值的精度需求。

研发应用也是如此，因为这些值以接近等比数列的形式存在，同时以10倍为一个周期循环，挑选器件时，比较容易获得精度要求足够且参数接近的器件。

至于说等比数列，仍然以E6为例，E本就是Exponential spacing（指数间距）的缩写，指数自然就是等比：

- E6数值（末尾补了数值10）： 1.0, 1.5, 2.2, 3.3, 4.7, 6.8, 10
- E6 下一个数值与上一个数字的比值（从1.0-10）：1.5, 1.466666667, 1.5, 1.424242424, 1.446808511, 1.470588235

也就是，每个数字参数增加50%就到了下一个可用的数值参数。在参数的精度要求不高的情况下（这里是20%），总能在这些参数值里选择一个合适的。

容易看出，若是用等差数值去覆盖这些参数范围，那么在同样的精度下，需要用更多的数值去覆盖相同的参数范围，那样会更复杂。

如果仔细思考这个问题，会发现，这个与经常用对数坐标是一样的道理。比如放大器的频率响应曲线（幅频、相频），对数坐标就更容易查看分析，而不是线性坐标。数值范围比较大的时候，比如覆盖多个数量级，那么对数坐标在不同数值范围内都有差不多相同的“分辨率”。

## 列表

List of values for each E series<sup>[1]</sup>:

- E3 values (40% tolerance)
  - 1.0, 2.2, 4.7
- E6 values (20% tolerance)
  - 1.0, 1.5, 2.2, 3.3, 4.7, 6.8
- E12 values (10% tolerance)
  - 1.0, 1.2, 1.5, 1.8, 2.2, 2.7, 3.3, 3.9, 4.7, 5.6, 6.8, 8.2
- E24 values (5% tolerance)
  - 1.0, 1.1, 1.2, 1.3, 1.5, 1.6, 1.8, 2.0, 2.2, 2.4, 2.7, 3.0, 3.3, 3.6, 3.9, 4.3, 4.7, 5.1, 5.6, 6.2, 6.8, 7.5, 8.2, 9.1
- E48 values (2% tolerance)
  - 1.00, 1.05, 1.10, 1.15, 1.21, 1.27, 1.33, 1.40, 1.47, 1.54, 1.62, 1.69, 1.78, 1.87, 1.96, 2.05, 2.15, 2.26, 2.37, 2.49, 2.61, 2.74, 2.87, 3.01, 3.16, 3.32, 3.48, 3.65, 3.83, 4.02, 4.22, 4.42, 4.64, 4.87, 5.11, 5.36, 5.62, 5.90, 6.19, 6.49, 6.81, 7.15, 7.50, 7.87, 8.25, 8.66, 9.09, 9.53
- E96 values (1% tolerance)
  - 1.00, 1.02, 1.05, 1.07, 1.10, 1.13, 1.15, 1.18, 1.21, 1.24, 1.27, 1.30, 1.33, 1.37, 1.40, 1.43, 1.47, 1.50, 1.54, 1.58, 1.62, 1.65, 1.69, 1.74, 1.78, 1.82, 1.87, 1.91, 1.96, 2.00, 2.05, 2.10, 2.15, 2.21, 2.26, 2.32, 2.37, 2.43, 2.49, 2.55, 2.61, 2.67, 2.74, 2.80, 2.87, 2.94, 3.01, 3.09, 3.16, 3.24, 3.32, 3.40, 3.48, 3.57, 3.65, 3.74, 3.83, 3.92, 4.02, 4.12, 4.22, 4.32, 4.42, 4.53, 4.64, 4.75, 4.87, 4.99, 5.11, 5.23, 5.36, 5.49, 5.62, 5.76, 5.90, 6.04, 6.19, 6.34, 6.49, 6.65, 6.81, 6.98, 7.15, 7.32, 7.50, 7.68, 7.87, 8.06, 8.25, 8.45, 8.66, 8.87, 9.09, 9.31, 9.53, 9.76
- E192 values (0.5% and lower tolerance)
  - 1.00, 1.01, 1.02, 1.04, 1.05, 1.06, 1.07, 1.09, 1.10, 1.11, 1.13, 1.14, 1.15, 1.17, 1.18, 1.20, 1.21, 1.23, 1.24, 1.26, 1.27, 1.29, 1.30, 1.32, 1.33, 1.35, 1.37, 1.38, 1.40, 1.42, 1.43, 1.45, 1.47, 1.49, 1.50, 1.52, 1.54, 1.56, 1.58, 1.60, 1.62, 1.64, 1.65, 1.67, 1.69, 1.72, 1.74, 1.76, 1.78, 1.80, 1.82, 1.84, 1.87, 1.89, 1.91, 1.93, 1.96, 1.98, 2.00, 2.03, 2.05, 2.08, 2.10, 2.13, 2.15, 2.18, 2.21, 2.23, 2.26, 2.29, 2.32, 2.34, 2.37, 2.40, 2.43, 2.46, 2.49, 2.52, 2.55, 2.58, 2.61, 2.64, 2.67, 2.71, 2.74, 2.77, 2.80, 2.84, 2.87, 2.91, 2.94, 2.98, 3.01, 3.05, 3.09, 3.12, 3.16, 3.20, 3.24, 3.28, 3.32, 3.36, 3.40, 3.44, 3.48, 3.52, 3.57, 3.61, 3.65, 3.70, 3.74, 3.79, 3.83, 3.88, 3.92, 3.97, 4.02, 4.07, 4.12, 4.17, 4.22, 4.27, 4.32, 4.37, 4.42, 4.48, 4.53, 4.59, 4.64, 4.70, 4.75, 4.81, 4.87, 4.93, 4.99, 5.05, 5.11, 5.17, 5.23, 5.30, 5.36, 5.42, 5.49, 5.56, 5.62, 5.69, 5.76, 5.83, 5.90, 5.97, 6.04, 6.12, 6.19, 6.26, 6.34, 6.42, 6.49, 6.57, 6.65, 6.73, 6.81, 6.90, 6.98, 7.06, 7.15, 7.23, 7.32, 7.41, 7.50, 7.59, 7.68, 7.77, 7.87, 7.96, 8.06, 8.16, 8.25, 8.35, 8.45, 8.56, 8.66, 8.76, 8.87, 8.98, 9.09, 9.20, 9.31, 9.42, 9.53, 9.65, 9.76, 9.88

这里面，不论是E96还是E192，都没有5.0这个数值，只有4.99，所以一般贴片电阻就只有4.99这个阻值，反倒没有5.0，应用上可能会让人困惑（也许做成等差数列取值就没有这个困惑了）。

根据数值表，E12 电阻的常见取值（单位：Ω）：

- 10, 12, 15, 18, 22, 27, 33, 39, 47, 56, 68, 82,
- 100, 120, 150, 180, 220, 270, 330, 390, 470, 560, 680, 820,
- 1 k, 1.2 k, 1.5 k, 1.8 k, 2.2 k, 2.7 k, 3.3 k, 3.9 k, 4.7 k, 5.6 k, 6.8 k, 8.2 k,
- 10 k, 12 k, 15 k, 18 k, 22 k, 27 k, 33 k, 39 k, 47 k, 56 k, 68 k, 82 k,
- 100 k, 120 k, 150 k, 180 k, 220 k, 270 k, 330 k, 390 k, 470 k, 560 k, 680 k, 820 k,
- 1 M, 1.2 M, 1.5 M, 1.8 M, 2.2 M, 2.7 M, 3.3 M, 3.9 M, 4.7 M, 5.6 M, 6.8 M, 8.2 M,
- 10 M

这里，小于10Ω和大于10MΩ的没有列举。

公式描述<sup>[3]</sup>：

<div  align="center">
<img src="./.assets/器件参数-E系列数字/Mathcad计算Exponential%20spacing电阻值.jpg" width = "100%" height = "100%" alt="图片" align=center />
</div>

数字参数曲线：

<div  align="center">
<img src="./.assets/器件参数-E系列数字/Exponential%20spacing阻值曲线.jpg" width = "100%" height = "100%" alt="图片" align=center />
</div>

## 参考及引用

[1] E series of preferred numbers. Wikipedia. <https://en.wikipedia.org/wiki/E_series_of_preferred_numbers>  
[2] E系列数字. Wikipedia. <https://zh.wikipedia.org/wiki/E%E7%B3%BB%E5%88%97%E6%95%B8%E5%AD%97>  
[3] 一个分压电阻选型小技巧 - 介绍E系列电阻阻值特性. 知乎. <https://zhuanlan.zhihu.com/p/364755594>
