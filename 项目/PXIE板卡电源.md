# PXIE板卡电源

## 电源树

- 12Vin（PXIE或者独立端子输入）
  - +18V：0.3A（DCDC：LMR62014）
    - +15V（LDO：MC78M15CDTRKG）
  - +5.5V（DCDC：LMZM23601）
    - +5.0V（LDO：ADM7171ACPZ-5.0-R7），或者可调ADM7171ACPZ-R7；
    - +3.0V（LDO：ADM7171ACPZ-3.0-R7），或者可调ADM7171ACPZ-R7；
  - +3.3V（选用方案2）：
    1. 方案1、（LDO：ADM7171ACPZ-3.3-R7），或者可调ADM7171ACPZ-R7；
    2. 方案2、DCDC：LMZM23601
  - -18V(预估实际最高：0.2A）设计额定：0.3A（DCDC：ADP5073ACPZ-R7）
    - -15V（LDO：MC79M15CDTRKG）
    - -5V（LDO：LT3094，或者 LM337IMP/NOPB）：直接从-18V，压降高，损耗大，但好在电流不大。
  - 9V（核心板供电）：不需要，直接用12V输入不必转9V
  - 1.8V：不需要，用核心板的1.8V输出

## 电源功耗评估

### -15V电源供电电流评估

- -15V电源供电电流评估，**200mA**
  - 评估静态功耗，累计：**90mA**
    - THS4131: 14mA typ
    - OPA828: 5.5mA typ（3）：17mA
    - ADA4898: 7.9mA typ *(4+3+1)：56mA
    - AD8065: 6.4mA（这个是ref in的，原理图应该画错了）
    - AD5291（DAC）：1uA
    - DG411（模拟开关）：1uA
  - 评估运放的输出电流（电阻负载）：不容易评估，就当作**50mA**吧！
  - -5V芯片的供电：**20mA？**

## 器件选型

### 15V LDO 电源选型

| module        | price   | dropout          | PSRR | noise   | input V | output V    | Current | package | nothing | conclusion       |
| :------------ | :------ | :--------------- | :--- | :------ | :------ | :---------- | :------ | :------ | :------ | :--------------- |
| LM2940        |         |                  |      | 450uV   |         |             |         |         |         | noise too high   |
| LT3080        | `$`1.81 | 1.235V(ctrl pin) |      | 40uVrms | 1.2-36  | 0V to ?     | 1.1A    | SOT-223 |         | acceptable       |
| LT1963        | ¥30     | 340mV            |      | 40uVrms |         | 1.21 to 20V | 1.5A    | SOT-223 |         | too expensive    |
| LM317DCYR     |         | 3V               |      |         |         |             |         |         |         | dropout too high |
| MC78M15CDTRKG | ¥ 2     | 2V               |      | 90uVrms | 36max   | 15V         | 0.5A    | TO-252  |         | **chose this**   |

### -15V电源选型(LDO)

| module        | price | dropout | PSRR | noise   | input V | output V | Current | package | nothing | conclusion |
| :------------ | :---- | :------ | :--- | :------ | :------ | :------- | :------ | :------ | :------ | :--------- |
| MC79M15CDTRKG | ¥ 2   | 1.1V    |      | 90uVrms | -35max  | -15V     | 0.5A    | TO-252  |         | chose this |

### -5V电源选型（LDO）

| module        | price | dropout | PSRR | noise             | input V     | output V       | Current | package | nothing | conclusion    |
| :------------ | :---- | :------ | :--- | :---------------- | :---------- | :------------- | :------ | :------ | :------ | :------------ |
| LT3094        | ¥30   | 235mV   |      | 3uVrms            | -1.8 ~ -20V | 0 ~ -19.5V     | 500mA   | DFN-12  |         | too expensive |
| LM337IMP/NOPB | ¥5    | 2V      |      | 0.003% = 150uVrms | 0 ~ -40V    | −1.25V to −37V | 1.5A    | SOT-223 |         | acceptable    |

### 5V电源选型（LDO）

| module  | price | dropout | PSRR | noise  | input V | output V        | Current | package | nothing | conclusion |
| :------ | :---- | :------ | :--- | :----- | :------ | :-------------- | :------ | :------ | :------ | :--------- |
| ADM7171 | 8     | 42 mV   |      | 6uVrms | 2.3~6.5 | 1.2V to Vin−Vdo |         |         |         | excellent  |

Vdo means dropout voltage.

使用可调的ADM7171，支持：5.0V，3.3V，3.0V, 型号：ADM7171ACPZ-R7，立创商城编号： C207710。

### 3.3V电源选型（DCDC）

方案1：使用可调的ADM7171，与3.0V，5.0V一致。
方案2：使用DCDC，选型如下：

| module    | price | frequency                  | input V | output V    | Current | package  | others | conclusion                             |
| :-------- | :---- | :------------------------- | :------ | :---------- | :------ | :------- | :----- | :------------------------------------- |
| tps82130  | ¥27   | 2MHz nominal, vary by load | 3V~17V  | 0.9V to 6V  | 3A      | µSiL     |        | frequency strategy does not acceptable |
| LMZM23601 | ¥20   | 1.0MHz or 0.7~1.1MHz sync  | 4V~36V  | 1.2V to 15V | 1A      | MicroSiP |        | good                                   |

### +5.5V电源选型（DCDC）

同3.3V开关电源选型，用LMZM23601。

### +18V开关电源（DCDC）

| module   | price | frequency  | input V | output V | Current      | package | others              | conclusion                      |
| :------- | :---- | :--------- | :------ | :------- | :----------- | :------ | :------------------ | :------------------------------ |
| LMR62014 | ¥ 3   | 1.6M fixed | 2.7-14V | 20V      | 0.5A capable | SOT-23  | need ext inductance | 1.6MHz freq is good, chose this |

## -17～-18V(DCDC)

| module         | price | frequency                     | input V      | output V       | Current         | package  | others        | conclusion        |
| :------------- | :---- | :---------------------------- | :----------- | :------------- | :-------------- | :------- | :------------ | :---------------- |
| LT1931         |       |                               |              |                |                 |          |               | complecated       |
| LM2611         |       | 1.4MHz                        | 2.7V to 14V  | −1.23~ Vin-36V | 300 mA          | SOT-23   | Cuk Converter | current too small |
| LM25575        |       |                               |              |                |                 |          |               |                   |
| LMZ34002       |       |                               |              |                |                 |          |               |                   |
| ADP5073ACPZ-R7 | ¥15   | 1.2/2.4MHz or 1.0~2.6MHz sync | 2.85V to 15V | ? to Vin−39V   | 1.2A Curr-limit | 16-LFCSP |               | good              |
| LMZM23601      | ¥20   | 1.0MHz or 0.7~1.1MHz sync     | 4V~36V       | Vin to -15V    | 1A              | MicroSiP |               | U out of range    |

对于ADP5073ACPZ-R7，如果过流保护点1.2A太小，可以选择ADP5074ACPZ-R7，有2.4A。

What is ADIsimPower tool set in Analog Device?

上周工作总结:
1、PXIe板卡锁放：
	a、和志健一起，确认了ADS1675的功能（ENBO，THD），同时也测试了它的Overload指示功能，正常；
	b、整理锁放原理图，前级和PXIe的接口（主要是志健给的）
	c、调研电源树方案，调研具体电源器件选型（DCDC和LDO），并和志健讨论。


下周计划：
1、和仕杰一起初步完成PXIE锁放原理图绘制。

2、安排源表组讨论主控系统方案。
