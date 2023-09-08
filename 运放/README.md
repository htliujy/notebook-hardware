# 运算放大器

待写

- 运放分类
- 电容型可编程运放，[Integrated Capacitive PGAs in ADCs: Redefining Performance](https://www.analog.com/en/analog-dialogue/articles/integrated-capacitive-pgas-in-adcs.html)
- Trade-offs Between CMOS, JFET, and Bipolar Input Stage-TI <https://www.ti.com/lit/an/sboa355/sboa355.pdf?ts=1613967086331&ref_url=https%253A%252F%252Fwww.google.com%252F>
- 比较器和运放区别
- rail-to-rail
  - 什么时候用rail-to-rail
  - 为什么有时候非rail-to-rail的运放输出可以做到更低的输出电压
- 单电源供电和双电源供电的区别如果将双电源的运放用单电源供电，是否有问题，反之，单电源运放用双电源供电呢？

差分、全差分、普通运放：

1. 差分运放：差分输入，单端输出，输出电压为有限增益倍的输入电压差。
2. 全差分运放：差分输入，差分输出，输出电压差为有限增益倍的输入电压差，通常用于长距离信号传输。
3. 普通运放：差分输入，单端输出，输出电压为无穷大增益倍的输入电压差，但通常不能开环使用，必须施加深度负反馈使闭环增益稳定。

举例：

1. 差分运放：AD620（应该是个仪表运放），LTC2053
2. 全差分运放：THS4509
3. 普通运放：OP07

特殊运放：

1. 输入真正实现rail-to-rail的运放：
   1. OPA325: 输入级使用charge pump抬升电压范围，实现输入级实现真正的rail to rail, 因为charge pump是开关电源，所以更需要磁珠去耦。
2. 输入电压超过电源轨道电压的：
