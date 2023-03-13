# Xilinx_时序约束

何为时序？

- setup time: data must reach its new value at least ts before CLOCK edge.
- Hold Time: data must hold constant for at least th after CLOCK edge.
- typical:
  - IO之间: ts = 5ns,th = 3ns
  - 内部逻辑: ts = -50ps, th = 300ps
  - 疑问：ts为什么可以是复数？

## 时序约束语法

- Create clocks
  - create_clock
  - create_generated_clock
  - set_system_jitter
  - set_input_jitter
  - set_clock_uncertainty
  - set_external_delay
- Input/Output Delays
  - set_input_delay
  - set_output_delay
- Clock Groups and CDC
  - set_clock_groups
  - set_false_path
- Timing Exceptions
  - set_false_path
  - set_min/max_delay
  - set_multicycle_path
  - set_case_analysis
  - set_disable_timing

## 如何约束异步信号

结论就是不用约束，但为了 "keep 'check_timing' happy", 可以象征性约束一下<sup>[1][2]</sup>。

## 参考及引用

[1] how to handle asynchronous signals? xilinx support. <https://support.xilinx.com/s/question/0D52E00006hpsvFSAQ/how-to-handle-asynchronous-signals?language=en_US>
[2] How to treat asynchronous inputs to be excluded from STA. <https://support.xilinx.com/s/question/0D52E00006iHs9ASAS/how-to-treat-asynchronous-inputs-to-be-excluded-from-sta?language=en_US>
[3] UG903 Vivado Design Suite User Guide: Using Constraints.
[4] UG949 UltraFast Design Methodology Guide for Xilinx FPGAs and SoCs.
