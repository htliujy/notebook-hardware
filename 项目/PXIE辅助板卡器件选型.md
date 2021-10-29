# PXIE辅助板卡器件选型

辅助板功能

- sine out
- TTL out
- Channel out * 2
- ADC in * 2
- reference

## 一、sine out

功能：

- 16bits
- 2MSPS（那么信号频率最高1MHz）
- 频率：f = 500kHz
- 幅度：±10V
- 压摆率：slew_rate = 2pi*f*V = 6.28 * 0.5 * 10 V/us = <font face="黑体" color=red>31.4V/us</font>

选型：

- DAC选型：<font face="黑体" color=red>DAC8811</font>
  - 16bits
  - 接口：50-MHz
  - 3MSPS?
- DAC输出运放：<font face="黑体" color=red>OPA828</font>
  - offset: 400uV max
  - noise:
    - 4 nV/√Hz @ 1kHz
    - 7.5 nV/√Hz @ 10Hz
  - 输入阻抗：10<sup>12</sup>Ω
  - 带宽：45MHz
  - 压摆率：150V/us
  - <font face="黑体" color=red>单通道</font>，用2个单运放
- sallenkey滤波器运放：<font face="黑体" color=red>ADA4898-2</font>
  - offset：160uV max
  - 输入阻抗：30MΩ（CM），5kΩ（DM）
  - 带宽: 65MHz
  - 压摆率：55V/us
- sine out输出运放：<font face="黑体" color=red>ADA4898-2</font>
  - noise:
    - 0.9 nV/√Hz @ 1kHz
    - 2.4 pA/√Hz @ 1kHz
  - 输出电流能力：40mA

## 二、TTL out

功能：

- 500kHz Clock

选型：

- 比较器：<font face="黑体" color=red>LT1016CS8</font>
- 异或门：<font face="黑体" color=red>SN74AHC1G86DBV</font>

## 三、channel out

功能：

- 16bits
- 1MHz
- 双通道

选型：

- DAC：DAC8812
  - 16bits
  - 接口：50MHz
  - 双通道
  - 单通道输出：50MHz/16bit = 3.12MSPS
  - 双通道输出：3.12MSPS/2 = 1.56MSPS

选型：

## ADC in

set http_proxy=http://127.0.0.1:8001