# xilinx-zynq-ultrascale+复位

如何设置PL复位，PS复位，PS和PL一起复位?

Zynq 7000复位：PSS_RST_CTRL <sup>[1]</sup>.

Zynq ultrascale+复位： GLOBAL_RESET (PMU_GLOBAL) Register. <sup>[2][3]</sup>

1. PS reset only:
2. PL reset only:
3. PS and PL reset together:

SKD 中相关参数：

- XPAR_PSU_PMU_GLOBAL_0_S_AXI_BASEADDR (XRESETPS_PMU_GLB_BASE) 0xFFD80000
  - XRESETPS_PMU_GLB_RST_CTRL: 0x00FFD80608 (BASE + 0x0000000608)
    - PS_ONLY_RST
    - FPD_RST
    - RPU_LS_RST
  - XRESETPS_PMU_GLB_PS_CTRL : 0x00FFD80004 (BASE + 0x0000000004)

添加PMU初始化：PMU Firmware. <https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18841724/PMU+Firmware>

## 参考及引用

[1] Zynq 系列 PS 软件复位详解. 知乎. <https://zhuanlan.zhihu.com/p/147533256>
[2] Zynq UltraScale+ Devices Register Reference. <https://www.xilinx.com/htmldocs/registers/ug1087/ug1087-zynq-ultrascale-registers.html>
[3] Zynq US+ How to use GLOBAL_RESET.PS_ONLY_RST in application? <https://support.xilinx.com/s/question/0D52E00006ihQMTSA2/zynq-us-how-to-use-globalresetpsonlyrst-in-application?language=en_US>
