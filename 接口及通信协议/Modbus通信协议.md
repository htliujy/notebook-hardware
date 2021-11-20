# Modbus通信协议

Modbus协议不是物理层的，是通信中的传输数据结构协议，是软件协议。

## 简介

如下引用自一款变频器说明书：

*Modbus协议有两种传输模式:ASCII(American Standard Code for Information International Interchange)模式和RTU(远程终端单元，Remote Terminal Units)模式。在同一个Modbus网络中，所有的设备传输模式、波特率、数据位、校验位、停止位等基本参数必须一致。*

*Modbus 网络是一种单主多从的控制网络，也即同一个Modbus网络中只有一台设备是主机，其它设备都为从机。主机可以单独地对某台从机通讯，也可以对所有从机发布广播信息。对于单独访问的命令，从机都应返回一个回应信息；对应主机发出的广播信息，从机无需反馈回应信息给主机。*

另外，还有Modbus tcp协议<sup>[1]</sup>：

实际上Modbus协议包括ASCII、RTU、TCP。  
Modbus的ASCII、RTU协议规定了消息、数据的结构、命令和应答的方式，数据通讯采用Maser/Slave方式。

<font face="黑体" color=red>校验：</font>

- 串行协议中除有奇偶校验外，ASCII模式采用LRC校验，RTU模式采用16位CRC校验.
- ModbusTCP模式没有额外规定校验，因为TCP协议是一个面向连接的可靠协议。

关于CRC校验和LRC校验，将会在另一篇博客里面记录。

## 数据的结构

Modbus RTU数据帧结构<sup>[2]</sup>：

Modbus RTU frame format (primarily used on asynchronous serial data lines like RS-485/EIA-485)
| Name     | Length (bits) | Function                                                        |
| -------- | ------------- | --------------------------------------------------------------- |
| Start    | 28            | At least 3 and 1/2 character times of silence (mark condition)  |
| Address  | 8             | Station address                                                 |
| Function | 8             | Indicates the function code; e.g., read coils/holding registers |
| Data     | n × 8         | Data + length will be filled depending on the message type      |
| CRC      | 16            | Cyclic redundancy check                                         |
| End      | 28            | At least 3 and 1/2 character times of silence between frames    |

也就是：

<div  align="center">
<img src="./.assets/Modbus通信协议/Modbus%20RTU数据帧结构.png" width = "80%" height = "80%" alt="Modbus RTU数据帧结构.png" align=center />
</div>

Modbus ASCII数据帧结构<sup>[2]</sup>：

Modbus ASCII frame format (primarily used on 7- or 8-bit asynchronous serial lines)

| Name     | Length (bytes) | Function                                                          |
| -------- | -------------- | ----------------------------------------------------------------- |
| Start    | 1              | Starts with colon : (ASCII hex value is 3A)                       |
| Address  | 2              | Station address                                                   |
| Function | 2              | Indicates the function codes like read coils / inputs             |
| Data     | n × 2          | Data + length will be filled depending on the message type        |
| LRC      | 2              | Checksum (Longitudinal redundancy check)                          |
| End      | 2              | Carriage return – line feed (CR/LF) pair (ASCII values of 0D, 0A) |

也就是：

<div  align="center">
<img src="./.assets/Modbus通信协议/Modbus%20ASCII数据帧结构.png" width = "80%" height = "80%" alt="Modbus ASCII数据帧结构" align=center />
</div>

Modbus TCP数据帧结构<sup>[2]</sup>：

Modbus TCP frame format (primarily used on Ethernet networks)

| Name                   | Length (bytes) | Function                                                  |
| ---------------------- | -------------- | --------------------------------------------------------- |
| Transaction identifier | 2              | For synchronization between messages of server and client |
| Protocol identifier    | 2              | 0 for Modbus/TCP                                          |
| Length field           | 2              | Number of remaining bytes in this frame                   |
| Unit identifier        | 1              | Slave address (255 if not used)                           |
| Function code          | 1              | Function codes as in other variants                       |
| Data bytes             | n              | Data as response or commands                              |

对比Modbus ASCII数据帧和Modbus RTU数据帧，可以发现

Modbus RTU是依靠发送数据的前后预留空闲时间，来区分一个数据帧：

- 好处：数据可以以hex形式发送
- 坏处：时序要求更高，软件处理的实时性要求更高

Modbus ASCII则是依靠起始符和终止符来区分数据帧：

- 好处：时序要求不高，接收方可以连续解析数据，而不用判断时间，将起始符和终止符之间的数据视为一帧，再行解析
- 坏处：数据需要以ASCII编码后发送，不能以原始hex形式发送（以hex发送可能会有0x3A, 0x0D, 0x0A这样的起始符和终止符，打乱数据结构，解析错误），接收后又需要解码，增加工作量以及数据长度（数据编码后变长，如hex数据为：0x01, 将'0'和'1'编码为ASCII后，为：0x30, 0x31，原本一个字节的数据，现在变成两个字节）

## 应用及代码

暂无

参考及引用：

[1] [一文看懂Modbus, Rtu, Rs485等名词的联系](https://blog.csdn.net/w405722907/article/details/83537198)
[2] [Modbus](https://en.wikipedia.org/wiki/Modbus)