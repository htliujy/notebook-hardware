# 压敏电阻-MOV

MOV (Metal Oxide Varistor)

## Choosing the right MOV for Protection<sup>[2]</sup>

You should know about the various numbers of parameters of a MOV to choose the right device for your pieces of equipment. The **Specification of a MOV** depends on the following

- Maximum Working Voltage:  It is the steady-state DC voltage to which the typical leakage current will be less than the specified value.
- Clamping voltage: It is the voltage at which the MOV starts to conduct and dissipate the surge current.
- Surge Current: It is the maximum peak current that can be given to the device without causing any device damage; it is mostly expressed in ‘current for a given time’. Although the device can handle the surge current the manufacturers recommend replacing the device if there is an occurrence of surge current.
- Surge Shift: Whenever the device experiences a surge the rated clamping voltage decreases, the variation in the voltage after the surge is called the surge shift.
- Energy Absorption: The maximum amount of energy that the MOV can dissipate for a specified peak pulse time of a specific waveform during a surge. This value can be determined by running all the devices within a specific controlled circuit with specific values. The Energy is usually expressed in standard transient x/y where x is the transient rise and y is the time to reach its half peak value.
- Response Time: It is the time at which the varistor starts conducting after the occurrence of the surge, in many instances, there isn’t an exact response time. The typical response time is always fixed as 100nS.
- Maximum AC Voltage: It is the maximum RMS line voltage that can be given to the varistor constantly, the maximum RMS value should be chosen to be slightly above the actual RMS line voltage. The peak voltage of the sine wave should not overlap with the minimum varistor, if it does, it might reduce the lifetime of the components. The manufacturers will specify the maximum AC Voltage that we can provide to the device in the product description itself.
- Leakage Current: It is the amount of current drawn by the varistor when it is operating below the clamping voltage that is when there is no surge in the network. Usually, the leakage current will be specified at a given operating voltage across the device.

翻译：

参考及引用：

[1] [Varistor](https://en.wikipedia.org/wiki/Varistor)
[2] [Metal Oxide Varistor (MOV) – Working, Application, Design Tips and Selection Guide](https://components101.com/articles/metal-oxide-varistor-mov-overview)
