# xilinx ZYNQ 引脚

如何下载Zynq-7000 SoC Package Files（ASCII格式，txt文件）：<https://www.xilinx.com/support/package-pinout-files/zynq7000-pkgs.html>

```txt
W11   TMS_0              NA     0     NA     NA      CONFIG    NA
W10   TDO_0              NA     0     NA     NA      CONFIG    NA
V11   TDI_0              NA     0     NA     NA      CONFIG    NA
R8    INIT_B_0           NA     0     NA     NA      CONFIG    NA
V9    PROGRAM_B_0        NA     0     NA     NA      CONFIG    NA
T7    CFGBVS_0           NA     0     NA     NA      CONFIG    NA
W9    DONE_0             NA     0     NA     NA      CONFIG    NA
W8    RSVDVCC1           NA     0     NA     NA      CONFIG    NA
U8    RSVDVCC3           NA     0     NA     NA      CONFIG    NA
V8    RSVDVCC2           NA     0     NA     NA      CONFIG    NA
W14   IO_0_12            NA     12    NA     NA      HR        NA
Y12   IO_L1P_T0_12       0      12    NA     NA      HR        NA
Y11   IO_L1N_T0_12       0      12    NA     NA      HR        NA
AB12  IO_L2P_T0_12       0      12    NA     NA      HR        NA
```

GTX 和 GTP 是什么？

SRCC和MRCC 是什么，有什么区别？

以Zynq7035（xc7z035ffg676pkg）为例：

```txt
AC12  IO_L11P_T1_SRCC_12       1                  12    NA            NA                  HR        NA
AD11  IO_L11N_T1_SRCC_12       1                  12    NA            NA                  HR        NA
AC13  IO_L12P_T1_MRCC_12       1                  12    NA            NA                  HR        NA
AD13  IO_L12N_T1_MRCC_12       1                  12    NA            NA                  HR        NA
AC14  IO_L13P_T2_MRCC_12       2                  12    NA            NA                  HR        NA
AD14  IO_L13N_T2_MRCC_12       2                  12    NA            NA                  HR        NA
AB15  IO_L14P_T2_SRCC_12       2                  12    NA            NA                  HR        NA
AB14  IO_L14N_T2_SRCC_12       2                  12    NA            NA                  HR        NA
```

bank12有2对SRCC和2对MRCC引脚。

参考：

[Xilinx FPGA的专用时钟引脚及时钟资源相关](https://www.cnblogs.com/lazypigwhy/p/11081972.html)

[Xilinx 7系列FPGA架构之时钟资源（一）](https://www.eefocus.com/fpga/486263)

另外，参考UG472，有：

Single-ended clock inputs <font face="黑体" color=red>must be assigned to the P (master) side</font>  of the clock-capable input pin pair.

## 参考及引用

[1] Zynp Pins - Deep Dive: How to understand Zynq Pins! <https://www.avnet.com/wps/portal/us/products/avnet-boards/support/faq/zynq-pins-deep-dive/>
[2] Zynq-7000 SoC Packaging and Pinout Product Specification **UG865**.
[3] Xilinx FPGA 引脚功能详细介绍. CSDN <https://blog.csdn.net/a164409980/article/details/109045187>
[4] Package Files Portal <https://www.xilinx.com/support/package-pinout-files.html>
[5] Zynq-7000 SoC Package Files <https://www.xilinx.com/support/package-pinout-files/zynq7000-pkgs.html>
