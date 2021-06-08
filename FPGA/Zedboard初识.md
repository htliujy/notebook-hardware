# Zedboard初识

本文转载自： zedboard初识. CSDN <https://blog.csdn.net/u012582664/article/details/51870335>

zedboard简介
Zedboard是第一款面向开源社区的Zynq-7000系列开发板，而Zynq-7000系列FPGA，也称为完全可编程（All Programable）SoC，是Xilinx一个有重大意义的产品系列。

在FPGA里集成高性能的处理器内核一直是众多FPGA厂商以及客户的需求，Zynq-7000的面世标志着Xilinx在SoC集成度上的一个突破，实现了双核Cortex-A9 MPcore和最新的28nm 7系列可编程逻辑的紧密集成。

上图可以看出Zynq芯片内部可以分为两部分PS（Processing System）和PL（Programmable Logic），其中PS部分有点像传统的处理器内部结构，包括CPU核、图形加速、浮点运算、存储控制器、各种通信接口外设以及GPIO外设，而PL部分就是传统的可编程逻辑和支持多种标准的IO，它们之间通过内部高速总线互联。这种架构既提高了系统性能（处理器和各种外设控制的”硬核“），又简化了系统的搭建（可编程的外设配置），同时提供了足够的灵活性（可编程逻辑）。

## 参考及引用
