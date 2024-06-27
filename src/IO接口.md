# I/O 接口

<!-- toc -->

## I/O 接口概览


![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604192311.png)


![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604192215.png)

## IO接口作用

I/O 接口作用：

- 数据缓冲：通过数据缓冲寄存器（DBR）达到主机和外设工作速度的匹配
- 错误或状态监测：通过状态寄存器反馈设备的各种错误、状态信息，供CPU查用
- 控制和定时：接收从控制总线发来的控制信号、时钟信号
- 数据格式转换：串-并、并-串等格式转换
- 与主机和设备通信：实现主机一I/O接口一I/O设备之间的通信
## IO接口的工作原理

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604191308.png)

## 接口与端口

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604191640.png)

## I/O端口及其编址

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604191702.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240604192137.png)


## I/O 接口的类型

按数据传送方式可分为

- 并行接口：一个字节或一个字所有位同时传送。
- 串行接口：一位一位地传送。

注：这里所说的数据传送方式指的是外设和接口一侧的传送方式。接口要完成数据格式转换。

按主机访问I/O设备的控制方式可分为

- 程序查询接口
- 中断接口
- DMA接口

按功能选择的灵活性可分为

- 可编程接口
- 不可编程接口