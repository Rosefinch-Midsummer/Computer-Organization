# I/O控制方式

<!-- toc -->

## 程序查询方式

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605163632.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605164849.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605164928.png)

## 程序中断方式

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605165008.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605174117.png)

### 中断请求的分类

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605174229.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605174339.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605174421.png)






### 中断判优-优先级设置

1. 硬件故障中断属于最高级，其次是软件中断；
2. 非屏蔽中断优于可屏蔽中断；
3. DMA请求优于I/O设备传送的中断请求
4. 高速设备优于低速设备；
5. 输入没备优于输出设备；
6. 实时设备优于普通设备。



### 中断处理过程

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605221207.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605221130.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240605221429.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607155932.png)

### 多重中断

单重中断： 执行中断服务程序时不响应新的中断请求。

多重中断 又称中断嵌套，执行中断服务程序时可响应新的中断请求。

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607162711.png)

### 中断屏蔽技术

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607162742.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607162830.png)

### 中断系统小结

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607162853.png)

### 程序中断方式传输数据


![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607165404.png)





![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607165335.png)


## DMA 方式

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607170650.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607171224.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607171509.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607171944.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607172131.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607172355.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240607172548.png)


## 通道方式

[组成原理(二十一)：输入输出系统之 通道控制方式 来源](https://www.cnblogs.com/RunningSnails/p/17693782.html)

### 通道的功能

接收CPU和I/O指令，按指令要求与指定外设进行联系；

从主存取出属于该通道程序的通道指令，经译码后向设备控制器和设备发送各种命令。

实施主存和外设间的数据传送，提供数据中间缓存的空间以及指示数据放的主存地址和传送的数据量。

从外设获得设备的状态信息，形成并保存通道本身的状态信息。

将外设的中断请求和通道本身的中断请求按次序报告给CPU。

### 通道的类型和结构

按输入输出信息的传送方式，通道可分为字节多路通道、选择通道和数组多路通道。

![0](https://img2023.cnblogs.com/blog/1680081/202309/1680081-20230911160005064-603832025.png)

字节多路通道，用于连接与管理多台低速设备，以字节交叉方式传送信息。

![0](https://img2023.cnblogs.com/blog/1680081/202309/1680081-20230911160005078-1102865493.png)

选择通道又称高速通道，在物理上可连接多个设备，这些设备分时工作，选择通道一次只能选择一台设备进行数据传送，只有当它和主存交换完信息后，才能选择另一台外部设备并执行该设备的通道程序。

数组多路通道是字节多路通道 和 选择通道的结合。当某设备进行数据传送时，通道只为该设备服务；当设备在执行辅助操作时，通道暂时断开与这个设备的连接，挂起该设备的通道程序，去为其他设备服务。

数据传输率/流量：通道在单位时间内传送的位数或字节数，代表了计算机的吞吐量。

### 通道的结构

通道的逻辑结构中包含3个重要的寄存器CSWR、CAWR、CCWR。

![0](https://img2023.cnblogs.com/blog/1680081/202309/1680081-20230911160005103-245088500.png)

CCWR是通道命令寄存器，用来存放通道命令字(CCW)。

CAWR是通道地址字寄存器，指出通道程序在主存中的起始地址，工作时，通道根据提供的地址到主存中取出CCW并加以执行。

CSWR是通道状态字寄存器，记录了通道程序执行后本通道和相应设备的各种状态信息，这些信息称为通道状态字(CSW)。

### 通道程序

通道指令也是通道命令字(CCW)，用来编制通道程序，并由管理程序将它存放在主存中。用通道地址字(CAW)指出通道程序的起始地址。

在主CPU执行启动I/O指令，启动指定通道后，通道将执行通道程序来实现的I/O操作，直到组成通道程序的全部CCW执行完毕。

通道程序由一条或几条CCW组成。

### 通道工作过程

通道完成一次数据传输的主要过程如下：

![0](https://img2023.cnblogs.com/blog/1680081/202309/1680081-20230911160005151-1422167643.png)

1、用户程序中使用访问管指令进入管理程序，由CPU通过管理程序组织一个通道程序，并启动通道；

2、通道执行CPU为它组织的通道程序，完成指定的数据输入输出工作；

3、通道程序结束后向CPU发出中断请求。CPU响应该中断请求后，第二次调用管理程序对中断请求进行处理。

每完成一次输入输出工作，CPU只需要两次调用管理程序，大大减少了对用户程序的打扰。


## DMA方式和通道方式区别

通道是实现外设和主存之间直接交换数据的控制器。两者的区别在于：

DMA控制器是通过设计的硬件控制逻辑实现对数据传送的控制；通道是一个具有特殊功能的处理器，具有更强的独立处理数据的输入和输出功能。

DMA控制器通常只能控制一台或少数几台同类设备；一个通道可以同时控制众多同类或不同类设备。

### DMA方式（完全硬件）

在 I/O设备与外设之间有直接数据通路，传送过程中不需要CPU参与，而是 DMA控制器控制完成。

DMA工作过程：

1）预处理

CPU收到 设备发出的DMA请求，它做为 司令，会向 DMA发布一些命令，启动DMA，测试I/O设备，初始化寄存器等

2）数据传送

完全由DMA硬件完成

3）后处理

完成数据传送后，DMA控制器向CPU发送中断请求。

### 通道方式（有程序参与）

I/O 通道是指专门负责输入/输出的处理机，每个通道都挂接外设，主机在执行 I/O命令时，只需要启动通道，然后通道会执行通道程序。

通道方式是对DMA方式的发展，由一个数据块的读写发展成为对一组数据块的处理。

通道的工作过程：CPU只要向 I/O通道发送一条 I/O指令，哪怕是一组相关的读写操作，通道会执行通道程序，完成一组数据的传送。

DMA与通道方式的区别：

1）一些控制信息，如数据块的大小，内存位置，DMA方式下由CPU来控制，但是通道方式下由通道控制

2）每个DMA控制器对应一台设备与内存交换数据，但是通道可以控制多台设备与内存的数据进行交换。