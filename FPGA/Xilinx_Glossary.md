# Xilinx Glossary

xilinx的说明文档用了太多的专业术语以及缩略语了，记不下来，此笔记用于帮助记忆。

接口：

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

其他：

- RTL: Register-transfer level (寄存器传输级)
- MPSoC: multiprocessor system on a chip
- PS: Processing System
- PL: Programable Logic
- HP I/O: high-performance I/O
- HR I/O: high-range I/O
- SDR: Single Data Rate （一个周期一个信号）
- DDR: Double Data Rate (一个周期两个信号)
- QDR: [Quad data rate](https://en.wikipedia.org/wiki/Quad_data_rate), GDDR5X使用该技术但兼容DDR；
- DCI: digitally-controlled impedance
- MMCM: Mixed-Mode Clock Manager (Module);
- XDMA: Xilinx PCI Express DMA
- OCM: On chip memory
- FSBL: First Stage Bootloader
- BIF: Boot Image Format
- BSP: Board Support Package
- ILA: Integrated Logic Analyzer

Vivado：

- ECO 指的是 Engineering Change Order ，即工程变更指令。目的是为了在设计的后期，快速灵活地做小范围修改，从而尽可能的保持已经验证的功能和时序。ECO 是从 IC 设计领域继承而来，Vivado上 的 ECO 便相当于 ISE 上的 FPGA Editor。参考：[“揭秘” Xilinx FPGA 的 ECO 功能](http://xilinx.eetrend.com/content/2021/100091895.html)

## 参考及引用

[1] Glossary <https://www.xilinx.com/support/documentation/sw_manuals/xilinx10/help/iseguide/mergedProjects/fpga_editor/html/fe_glossary.htm>
