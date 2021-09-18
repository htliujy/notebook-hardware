# System Monitor and XADC

xilinx 官方提供的系统监测器有SYSMON和XADC

Device Support：

|                             | Virtex 5/6 | 7-Series       | UltraScale          | UltraScale+                     |
| --------------------------- | ---------- | -------------- | ------------------- | ------------------------------- |
| AMS  Block                  | SYSMON     | XADC           | SYSMON              | SYSMON                          |
| Number of blocks per device | 1          | 1              | 1-3                 | 1-4                             |
| Interface                   | JTAG, DRP  | JTAG, DRP, AXI | I2C, JTAG, DRP, AXI | PMBus, I2C, JTAG, DRP, AXI, ATB |

## System Monitor (SYSMON)

Xilinx’s System Monitor technology enhances the overall safety, security, and reliability of your system by monitoring the physical environment via on-chip power supply, temperature sensors and external analog inputs.

SYSMON is a key part of the power management infrastructure for the board, providing telemetry information for the supplies for the Xilinx device and the various other on-board supplies.

### System Monitor Architecture Overview

- 17 differential external inputs for measuring external voltages and currents
- ADC for digitizing voltages, currents, and temperatures
- On-chip supply voltage sensors accurate to +/-1% (max)
- On-chip temp sensor  accurate to +/-4˚C (max)
- Access via DRP directly, JTAG, I2C, PMBus or AXI

The <font face="黑体" color=red>System Management Wizard</font> can be used to easily configure the SYSMON to operate to the particular system requirements.

## XADC - Integrated Analog with Digital Customization

The 7 Series FPGA and Zynq-7000 SoC AMS technology provides use models ranging from simple system monitoring to more complex analog measurements that require digital post-processing such as linearization, filtering, calibration, and oversampling. The XADC delivers advantages in flexibility, integration, and cost savings across a wide range of applications.

### XADC Architecture Overview

- Dual 12-bit 1Msps analog-to-digital converters
- Dual independent rack and hold (T/H) amplifiers
- On-chip voltage references
- On-chip thermal and supply sensors
- External analog input channels

## Key Documents
| Syntax                                                                                                                                                                                     | Description | Description |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- | ----------- |
| [Analog Mixed Signal Technology Product Brief](https://www.xilinx.com/content/dam/xilinx/publications/prod_mktg/analog-mixed-signal-product-brief.pdf)                                     | 607 KB      | 01/18/2013  |
| [UltraScale Architecture System Monitor User Guide](https://www.xilinx.com/content/dam/xilinx/support/documentation/user_guides/ug580-ultrascale-sysmon.pdf)                               | 2 MB        | 09/15/2021  |
| [Virtex-6 FPGA System Monitor User Guide](https://www.xilinx.com/content/dam/xilinx/support/documentation/user_guides/ug370.pdf)                                                           | 2 MB        | 09/18/2014  |
| [Virtex-5 FPGA System Monitor User Guide](https://www.xilinx.com/content/dam/xilinx/support/documentation/user_guides/ug192.pdf)                                                           | 3 MB        | 02/02/2011  |
| [System Management Wizard v1.1 Product Guide](https://www.xilinx.com/content/dam/xilinx/support/documentation/ip_documentation/system_management_wiz/v1_1/pg185-system-management-wiz.pdf) | 1 MB        | 10/01/2014  |
| [XADC Layout Guidelines](https://www.xilinx.com/content/dam/xilinx/support/documentation/application_notes/xapp554-xadc-layout-guidelines.pdf)                                             | 3 MB        | 02/13/2013  |
| [Driving the Xilinx Analog-to-Digital Converter Application Note](https://www.xilinx.com/content/dam/xilinx/support/documentation/application_notes/xapp795-driving-xadc.pdf)              | 575 KB      | 02/24/2016  |
| [/content/dam/xilinx/support/documentation/white_papers/wp398_AMS_and_Analog.pdf](https://www.xilinx.com/content/dam/xilinx/support/documentation/white_papers/wp398_AMS_and_Analog.pdf)   |             |             |

## 参考及引用

[1] System Monitor and XADC. <https://www.xilinx.com/products/technology/analog-mixed-signal.html>
