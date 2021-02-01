# Modbus通信协议

Modbus协议不是物理层的，是通信中的传输数据结构协议，是软件协议。

## 简介

如下引用自一款变频器说明书：

*Modbus协议有两种传输模式:ASCII(American Standard Code for Information International Interchange)模式和RTU(远程终端单元，Remote Terminal Units)模式。在同一个Modbus网络中，所有的设备传输模式、波特率、数据位、校验位、停止位等基本参数必须一致。*

*Modbus 网络是一种单主多从的控制网络，也即同一个Modbus网络中只有一台设备是主机，其它设备都为从机。主机可以单独地对某台从机通讯，也可以对所有从机发布广播信息。对于单独访问的命令，从机都应返回一个回应信息；对应主机发出的广播信息，从机无需反馈回应信息给主机。*

另外，还有Modbus tcp协议协议，下面引用自CSDN<sup>[1]</sup>：

*Modbus rtu和Modbus tcp两个协议的本质都是MODBUS协议，都是靠MODBUS寄存器地址来交换数据；但所用的硬件接口不一样，Modbus RTU一般采用串口RS232C或RS485/422，而Modbus TCP一般采用以太网口。现在市场上有很多协议转换器，可以轻松的将这些不同的协议相互转换 如：Intesisbox可以把modbus rtu转换成Modbus tcp。*

*实际上Modbus协议包括ASCII、RTU、TCP。  
标准的Modicon控制器使用RS232C实现串行的Modbus。Modbus的ASCII、RTU协议规定了消息、数据的结构、命令和就答的方式，数据通讯采用Maser/Slave方式。  
Modbus协议需要对数据进行校验，串行协议中除有奇偶校验外，ASCII模式采用LRC校验，RTU模式采用16位CRC校验.  
ModbusTCP模式没有额外规定校验，因为TCP协议是一个面向连接的可靠协议。  
TCP和RTU协议非常类似，只要把RTU协议的两个字节的校验码去掉，然后在RTU协议的开始加上5个0和一个6并通过TCP/IP网络协议发送出去即可*

## 具体协议说明及应用

引用：

[1] [一文看懂Modbus, Rtu, Rs485等名词的联系](https://blog.csdn.net/w405722907/article/details/83537198)