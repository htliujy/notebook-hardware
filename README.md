# 公开的笔记-硬件

这里一般写的硬件不包含功率电子，不包含单片机、嵌入式硬件（这个暂时写在Software里面，等到笔记较多需要独立整理出来后，再写入这个硬件的笔记里）。

临时记录（待写清单）：

1、图解电子系列丛书为什么有那么多的书籍，一下子说不完了，之前看到的都是《高低频电路设计与制作》没想到还有一本《高频电路设计与制作》；

<div  align="center">
<img src="./临时/高频电路设计与制作.png" width = "100%" height = "100%" alt="高频电路设计与制作" align=center />
</div>

史密斯图

我想找一个高频模拟开关的电路，Y字型的，但我总是记得在这个系列里面，那我就一个个都看全了，我就不信，找不出来。

| ISBN          |            书名             |                             是否检查 |
| ------------- | :-------------------------: | -----------------------------------: |
| 9787030165107 |     LC滤波器设计与制作      |                                   -- |
| 9787030165176 |    OP放大器应用技巧100例    |                                   -- |
| 9787030171825 | 测量电子电路设计——滤波器篇  |                           好像也没有 |
| 9787030171610 |  测量电子电路设计——模拟篇   | 看目录，好像也都是放大器的，应该没有 |
| 9787030165114 |     传感器应用技巧141例     |                                      |
| 9787030165060 |   电子元器件的选择与应用    |         都是阻容器件等选型，应该没有 |
| 9787030117830 |    高低频电路设计与制作     |                                      |
| 9787030174970 |    晶体管电路设计与制作     |                                      |
| 9787030174963 |  开关稳压电源的设计与应用   |                                      |
| 9787030165305 |    模拟技术应用技巧101例    |                                      |
| 9787030165282 | 锁相环（PLL）电路设计与应用 |                                      |
| 9787030173690 |     高频电路设计与制作      |                                      |

最后在高频电路设计与制作中找到了对应的电路图了，里面有各种详细解释。

<div  align="center">
<img src="./临时/高频开关电路.png" width = "100%" height = "100%" alt="高频开关电路" align=center />
</div>

负电阻

电容寿命：曲线或者说计算书。

灌封胶，真空度

- ATX（Advanced Technology Extended）主板规格由英特尔公司在1995年制定。
- 读懂开关管datasheet
  - Normalized 归一化参数
  - IV的SOA和温升-时间曲线
  - MOS的特性
- 惠斯通电桥
- Lead–lag compensator <https://en.wikipedia.org/wiki/Lead%E2%80%93lag_compensator>
- filter 设计，filter solution， matlab的filter工具FDA？？以及TI的filter Design Tool.
- 三极管和MOS管的饱和区定义为什么不一样？三极管：截止区、放大区、饱和区？MOS：截至区，三极管区（包含线性区），饱和区？
- 这里有个人用了仿真软件：icircuit，三极管倒置：[关于三极管饱和状态的分析](https://zhuanlan.zhihu.com/p/26617808)
- MOS管的gm，gd
- LT3757的典型应用电路。
  - 非隔离反击电路做升压，可否用两级boost：[LTC3788 Generates High Voltages Using a Two-Stage Boost Converter](https://www.analog.com/en/technical-articles/ltc3788-generates-high-voltages-using-a-two-stage-boost-converter.html)
  - 开关电源优势劣势对比
- 传输门，为什么用PMOS和NMOS并联。
- LEB，SPDT，简单的一些东西解释；
- 隔离运放
  - 方案：光，磁，电场（电容）
  - 数字：肯定会产生相移，还比较严重
  - 隔离差分探头用的是什么方案？
- ADC的技术分类，为什么隔离运放用的是sigama-delta型的运放？
- JET、FET？
- 示波器Lissajous显示（两个通道分为XY轴并输出）,借由使用利萨茹图形可以测量出两个信号的频率比与相位差？
- Software Frequency Response Analyzer (SFRA)
- passive PFC
  - PFC
- [SCALE 的短路保护基本原理](http://www.igbt8.com/qd/349.html)
- AN2007-04-AP99007-How to calculate and minimize the dead time requirement for IGBTs properly（infineon）:死区时间计算
- 继电器：
  - 4.触点粘连问题？触点粘连有两种情况,一种是触点接通电机启动时电流过大造成的过流发热,一种是触点断开电机产生的感应高压形成电弧造成触点烧蚀. 看是哪种,再想解决方法. 如果是第一种,就换触点电流容量更大的继电器,如果是第二种,就在触点上并压敏电阻.
  - 上面的说法看来不对，应该是接通电容导致，而不是接通电机，电机在接通瞬间也会有那么大电流吗？另外，若是电容导致，可以并联热敏用于给电容预充电。
  - AC和DC电压一个大，一个小的问题。
- 模拟信号隔离
  - 光隔离（运放）HCNR201；
  - 磁隔离
  - 电场
  - 衰减（差分探头用了电阻衰减），未能实现真隔离，但只要阻抗足够，就行了
  - AMC3330（ADC-DAC）
  - 防抖电路（参考chop电路）
- ADC
  - Pipline
  - 积分，双积分。ICL7106
  - SAR（逐次比较）
  - 权电阻网络
  - 倒T电阻网络
  - 并行比较ADC
  - $$\delta$$ & $$\sigma$$
  - 都有什么典型代表的芯片？
- 全平台开源EDA工具——MacOS下也能做Verilog开发/仿真/综合：<https://zhuanlan.zhihu.com/p/151433928>，源码：<https://github.com/steveicarus/iverilog>，MAC上写Verilog并编译仿真:<https://blog.csdn.net/Zach_z/article/details/78787509>
- verilog倍频电路<http://blog.chinaaet.com/Augus/p/5100001263>
- 运放
  - 单电源，双电源
  - offset，bias
- 斯密斯圆图<http://www.360doc.com/content/16/0610/15/32066980_566502324.shtml>
  - 斯密斯原图与共轭有什么关系？
  - 阻抗匹配：功率（共轭），信号一致（相等或成比例）。
  - RF变压器MABAES0010中出现的斯密斯圆图，需要看懂。
  - 当前工艺下，各种关键参数的极限在哪里（输入阻抗，输入offset电压，输出压摆率）。
- 轴承<https://luyaku.pixnet.net/blog/post/344239039-pc%E6%95%A3%E7%86%B1%E9%A2%A8%E6%89%87%E4%B9%8B%E7%A0%94%E7%A9%B6%E5%9B%9B%EF%BC%9A%E9%A2%A8%E6%89%87%E8%BB%B8%E6%89%BF>
  - 滚珠（ball）
  - 油封（sleeve）
  - 磁悬浮-（vapo）-MF80251V1-1000U-A99<http://portal.sunon.com.tw/pls/portal/sunonap.sunon_html_d_pkg.open_file?input_file_name=7264646F632F3230313531302F3231383034302F28443038303632373830472D3030292D302E706466>
- SPI接口通信协议分析：SPI时序、2线、3线、4线SPI及4种常用工作模式<https://www.cirmall.com/articles/32784>
  - 用verilog，写一个SPI软核，然后再写一个测试的。
- 理解MOSFET时间相关及能量相关输出电容Coss(tr)和Coss(er)-刘松-万国半导体元件(深圳)有限公司
  - 他说不能用积分，但其实他也是拆解为很小的模块，也是积分。也就是将积分过程的解析解变为数值解而已。

硬件相关算法

- 时域，PFC值，不一定是因为相位角度的问题。，另外，还有PFC中的谐波问题，所以要做FFT，算谐波，那就能定量计算谐波和PFC的关系了（基波频率和相位固定的情况下）。
- dB计算器（集成换算工具）
- scalar, tensor, vector分别是什么
- MOS 管最大功率，热阻，最大电流之间的关系。
- 使用IGBT的二极管测试junction温度。
- FOM
- RC IGBT？？
- GTR，IGBT
- 孔径时间、孔径抖动、孔径延迟时间——正本清源, 作者：Walt Kester, MT-007 TUTORIAL analog devices
