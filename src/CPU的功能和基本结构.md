# CPU 的功能和基本结构

CPU的基本功能

1.指令控制。完成取指令、分析指令和执行指令的操作，即程序的顺序控制。

2.操作控制。一条指令的功能往往是由若干操作信号的组合来实现的。CPU管理并产生由内存取出的每条指令的操作信号，把各种操作信号送往相应的部件，从而控制这些部件按指令的要求进行动作。

3.时间控制。对各种操作加以时间上的控制。时间控制要为每条指令按时间顺序提供应有的控制信号。

4.数据加工。对数据进行算术和逻辑运算。

5.中断处理。对计算机运行过程中出现的异常情况和特殊请求进行处理。

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530105623.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530114416.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530114500.png)

CPU内部单总线方式：将所有寄存器的输入端和输出端都连接到一条公共的通路上。

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530114114.png)

暂存寄存器：用于暂存从主存读来的数据，这个数据不能存放在通用寄存器中，否则会破坏其原有内容。

如：两个操作数分别来自主存和R0，最后结果存回R0，那么从主存中取来的操作数直接放入暂存器，就不会破坏运算前R0的内容。

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530115241.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530115504.png)

![](https://cdn.jsdelivr.net/gh/Rosefinch-Midsummer/MyImagesHost03/img/20240530115651.png)