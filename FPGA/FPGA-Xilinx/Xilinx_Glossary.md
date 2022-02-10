# Xilinx Glossary

xilinx的说明文档用了太多的专业术语以及缩略语了，记不下来，此笔记用于帮助记忆。

接口及通信协议：

- HP IO: High-performance I/O, The HP I/O banks are designed to meet the performance requirements of high-speed memory and other chip-to-chip interfaces
- HD IO: High-density I/O, The HD I/O banks are designed to support low-speed interfaces.
- HR IO: High-range I/O, The HR I/O banks are designed to support a wider range of I/O standards
- MIO: 多功能IO接口，属于Zynq的PS部分
- EMIO：扩展MIO，依然属于Zynq的PS部分，只是连接到了PL上，再从PL的引脚连到芯片外面实现数据输入输出。
- SRCC: Single Region Clock Capable
- MRCC: Multi-Region Clock Capable
- CCIO: Clock capable inputs
- MMCM: mixed-mode clock manager
- CMT: clock management tiles(each CMT containing one MMCM and one PLL, reside in the CMT column next to the I/O column.)
- PCAP：Processor Configuration. Access Port
- SDR: Single Data Rate （一个周期一个信号）
- DDR: Double Data Rate (一个周期两个信号)
- QDR: [Quad data rate](https://en.wikipedia.org/wiki/Quad_data_rate), GDDR5X使用该技术但兼容DDR；
- XDMA: Xilinx PCI Express DMA

硬件：

- PS: Processing System
- PL: Programable Logic
- AMBA: Advanced Microcontroller Bus Architecture（高级微控制器总线架构）是用于ARM架构下系统芯片（SoC）设计中的一种总线架构；
- MMCM: Mixed-Mode Clock Manager (Module);

软件：

- FSBL: First Stage Bootloader
- BIF: Boot Image Format
- BSP: Board Support Package. BSP是所有与硬件相关的代码体的集合

Vivado：

- ECO 指的是 Engineering Change Order ，即工程变更指令。目的是为了在设计的后期，快速灵活地做小范围修改，从而尽可能的保持已经验证的功能和时序。ECO 是从 IC 设计领域继承而来，Vivado上 的 ECO 便相当于 ISE 上的 FPGA Editor。参考：[“揭秘” Xilinx FPGA 的 ECO 功能](http://xilinx.eetrend.com/content/2021/100091895.html)
- ILA: Integrated Logic Analyzer

其他：

- RTL: Register-transfer level (寄存器传输级)
- HAL: Hardware Abstraction Layer(硬件抽象层)
- MPSoC: multiprocessor system on a chip
- DCI: digitally-controlled impedance
- OCM: On chip memory
- ILA: Integrated Logic Analyzer

## 参考及引用

[1] Glossary <https://www.xilinx.com/support/documentation/sw_manuals/xilinx10/help/iseguide/mergedProjects/fpga_editor/html/fe_glossary.htm>
