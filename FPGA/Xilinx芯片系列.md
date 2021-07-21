# Xilinx芯片系列

FPGA按照产品系列分为<sup>[1][2]</sup>：

SPARTAN<sup>6</sup>，SPARTAN<sup>7</sup>，Artix, Artix UltraScale+<sup>TM</sup>, Zynq和Zynq UltraScale+<sup>TM</sup>等系列。

还有属于CPLD的CoolRunner-II系列。

如下图：

<div  align="center">
<img src="./Xilinx芯片系列/Xilinx芯片系列.png" width = "100%" height = "100%" alt="Xilinx芯片系列" align=center />
</div>

从图中可以看出，Xilinx的FPGA分类可以从几个方面分：

1. 按照性能分类：
   1. SPARTAN: 低端；
   2. ARTIX: 中低端；
   3. KINTEX: 中高端；
   4. VIRTEX: 高端；
   5. ZYNQ: 集成FPGA和ARM内核的异构芯片，既可以硬件编程，也可以软件编程。
2. 按照工艺节点（第几代工艺）：
   1. 7系列：28nm工艺节点（7系列是否指第七代？）；
   2. 6系列：45nm工艺节点（除了低端的SPARTAN系列，其他已经停产）；
   3. UltraSCALE: 20nm工艺节点（为什么使用UltraSCALE而不是8系列标识该工艺节点？）；
   4. UltraSCALE+: 16nm工艺节点（为什么使用UltraSCALE+而不是9系列标识该工艺节点？）；

另外，还有一个

## 器件型号命名规则

也就是供应商规格，见下图<sup>[2]</sup>：

<div  align="center">
<img src="./Xilinx芯片系列/Xilinx订货编号.png" width = "100%" height = "100%" alt="Xilinx订货编号" align=center />
</div>

规格标识解析（字段从左往右数）：

- 第一段编码都是"XC"，这俩字符表示该器件是Xilinx生产的商业级器件；
- 第二个字段代表该器件属于Xilinx的第几代器件，7系列的这个字段都是7；
- 第三个字段代表该器件属于哪个族，S代表Spartan、A代表Artix、K代表Kintex、V代表Virtex；
- 第四个字段，实际器件上印的是一位或多位阿拉伯数字，这个数字乘以1000就是该器件大致的资源数量；
- 第五个字段用于表示该器件的速度等级，-3最高，-1最低，带L的表示该器件是低功耗器件（低功耗器件的供电电压比普通器件更低）。这个参数是厂商对芯片测试筛选后印到芯片上的，是一个经验值。该值越大，表示Block RAM和高速IO等资源的最大时钟越高；
- 第六个字段标识封装类型；
- 第七个字段标识环保等级；
- 第八个字段：package designator, 只有SPARTAN  系列有，其他系列删除了；
- 第九个字段：封装引脚数；
- 第十个字段：温度等级。

## 参考及引用

[1] FPGA Leadership across Multiple Process Nodes. Xilinx <https://www.xilinx.com/products/silicon-devices/fpga.html>
[2] 5分钟了解FPGA之Xilinx 7系列. 电子创新网赛灵思社区 <http://xilinx.eetrend.com/content/2019/100042384.html>
