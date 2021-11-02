# PXIE辅助板卡器件选型

辅助板功能

1. sine out
2. TTL out
3. Channel out * 2
4. ADC in * 2
5. reference

运放对比：
| OP         | Chs   | Supply Volt | BW MHz | SR V/us | In Impedance    | noise            | offset/mV | out cur      | note       |
| ---------- | ----- | ----------- | ------ | ------- | --------------- | ---------------- | --------- | ------------ | ---------- |
| AD8066     | 2     | 5~24V       | 145    |         |                 | 7nV/√Hz@10kHz    |           |              | 电压轨太窄 |
| OPA828     | 1     | ±4~±18V     | 45     | 150     | 10^12           | 4nV/√Hz          | 0.4 max   | 30mA         |            |
| ADA4898    | 1/2   | ±5~±16V     | 65     | 50      | 30MΩ/5kΩ(DM)    | 0.9nV/√Hz        | 0.16 max  | 40mA         |            |
| LF347M     | 1     | ±3.5V~±18V  | 3      | 13      | 10^12           | 18nV/√Hz         | 10 max    |              | 偏置太大   |
| OPA1611/2  | 1/2   | ±2.25V~±18V | 40     | 27      | 1GΩ/20kΩ(DM)    | 1.1nV/√Hz        | 0.5 max   | ±30mA        |            |
| OPA1642    | 1/2/4 | ±2.25~±16V  | 11     | 20      | 10^13           | 5.1nV/√Hz        | 3.5 max   | 36/–30mA(SC) | 偏置太大   |
| OPA2810    | 1     | 4.75V ~27V  | 105    | 192     |                 | 5.7nV/√Hz@100kHz |           |              | 电压轨太窄 |
| LME49720MA | 2     | ±2.5~±17V   | 55     | 15      | 1000MΩ/30kΩ(DM) | 2.7nV/√Hz        | 0.7 max   |              |            |

疑问：
  噪声密度跟频率的关系是怎样的。

## 一、sine out

功能：

- 16bits
- 2MSPS（那么信号频率最高1MHz）
- 频率：f = 500kHz
- 幅度：±10V
- 压摆率：slew_rate = 2pi\*f\*V = 6.28 * 0.5 * 10 V/us = <font face="黑体" color=red>31.4V/us</font>

选型：

- DAC选型：<font face="黑体" color=green>DAC8811</font>
  - 16bits
  - 接口：50-MHz
  - 3MSPS?
- DAC输出运放：<font face="黑体" color=green>OPA828</font>
  - input offset: 400uV max
  - noise:
    - 4 nV/√Hz @ 1kHz
    - 7.5 nV/√Hz @ 10Hz
  - 输入阻抗：10<sup>12</sup>Ω
  - 带宽：45MHz
  - 压摆率：150V/us
  - <font face="黑体" color=red>单通道</font>，用2个单运放
- sallenkey滤波器运放：<font face="黑体" color=green>ADA4898-2</font>
  - offset：160uV max
  - 输入阻抗：30MΩ（CM），5kΩ（DM）
  - 带宽: 65MHz
  - 压摆率：55V/us
- sine out输出运放：
  - ADA4898-2（双运放用其中一个)
    - noise:
      - 0.9 nV/√Hz @ 1kHz
      - 2.4 pA/√Hz @ 1kHz
    - 输出电流能力：40mA
  - <font face="黑体" color=green>OPA828</font>
    - 输出电流能力: 30mA

## 二、TTL out

功能：

- 500kHz Clock

选型：

- 比较器：<font face="黑体" color=green>LT1016CS8</font>
- 异或门：<font face="黑体" color=green>SN74AHC1G86DBV</font>

## 三、channel out

功能：

- 16bits
- 1MSPS
- 双通道
- 频率：100kHz??
- 峰值电压：Vp = 10V
- 压摆率：slew_rate = 2pi\*f\*Vp = 6.28 * 0.1 * 10 V/us = <font face="黑体" color=red>6.28V/us</font>

选型：

- DAC选型：<font face="黑体" color=green>DAC8812</font>
  - 16bits
  - 接口：50MHz
  - 双通道
  - 单通道输出：50MHz/16bit = 3.12MSPS？？
  - 双通道输出：3.12MSPS/2 = 1.56MSPS？？
- DAC输出运放选型（电流转电压）：
  - OPA1642
    - 带宽：11MHz
    - 压摆率：20V/us
    - 输入阻抗：10^13
    - 电流输出能力：（短路）36 mA and –30 mA (sourcing and sinking)
    - input Offset：<font face="黑体" color=red>3.5mV max</font>
  - <font face="黑体" color=green>OPA1612</font>
    - 带宽：40MHz
    - 压摆率：27V/us
    - 输入阻抗：<font face="黑体" color=green>20kΩ(DM)，10^9Ω(CM)</font>
    - 电流输出能力：（短路）55 mA and –62 mA (sourcing and sinking)
    - input Offset：0.5V max

## 四、ADC in

功能需求：

- 双通道输入
- 200 kSPS
- 16bits

选型：

- ADC选型：
  - AD7606BSTZ-4
    - 200 kSPS
    - 16bits
    - 四通道
  - <font face="黑体" color=green>LTC2353-16</font>
    - 550 kSPS/Ch
    - 16 bits
    - 2 Channels
    - <font face="黑体" color=green>compatalbe 1.8V IO</font>
- 输入buffer选型：<font face="黑体" color=green>OPA828</font>,单通道
  - input offset: 400uV max
  - noise:
    - 4 nV/√Hz @ 1kHz
    - 7.5 nV/√Hz @ 10Hz
  - 输入阻抗：10<sup>12</sup>Ω
  - 带宽：45MHz
  - 压摆率：150V/us
  - <font face="黑体" color=green>单通道</font>，每个通道用一个。

| ADC          | chs  | bits | kSPS   | interface  | price | note               |
| :----------- | :--- | :--- | :----- | :--------- | :---- | :----------------- |
| LTC2353-16   | 2    | 16   | 550/Ch | SPI & LVDS | 120   | compatalbe 1.8V IO |
| AD7606BSTZ-4 | 4    | 16   | 200/Ch | SPI        | 85    |                    |

## 五、reference

功能需求：

- 10V可以兼容上面的几个模块。
- buffer电流：9mA
  - sine out(DAC8811IDGK): 10V/5kΩ + 10V/10kΩ = 3mA
  - channel out(DAC8812IBPW): (10V/5kΩ + 10V/10kΩ) * 2 = 6mA

选型：

- 基准电压芯片：
  - <font face="黑体" color=green>ADR01</font>
    - 输出电压：10.0V
    - Initial accuracy: ± 0.1%
    - 输出电流能力: 10mA
    - 噪声：10 μV p-p (0.1 Hz to 10 Hz)
    - 温漂：
      - <font face="黑体" color=green>SOIC-8: 3 ppm/°C</font>
      - SC70-5/TSOT-5: 9 ppm/°C
- buffer运放：
  - <font face="黑体" color=green>OPA1612</font>
    - input offset：500uVmax
    - 输出电流：30mA
    - Noise Density: 1.1 nV/√Hz at 1 kHz
    - <font face="黑体" color=green>供电：0-15V就行，不需要双电源。</font>
    - sine out DAC 用一个通道，2个channel out DAC共用一个通道
  - OPA1642
    - input offset: 3.5mV max, <font face="黑体" color=red>veto</font>
