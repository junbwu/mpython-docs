汇编指令
====================

标记
------

* 标记(INNER1)

这定义了一个用于转移指令的标记。因此，在代码中其他地方， ``b(INNER1)`` 将使得在标记指令后继续执行指令。

定义内联数据
--------------------

以下汇编指令有助于将数据嵌入到汇编代码中。

* data(size, d0, d1 .. dn)

数据指令在内存中创建数据值数组。第一个参数指定后续参数的大小（字节为单位）。因此，以下第一条语句将使得汇编程序将三个字节
（其值为2、3、4）放入连续的存储单元中，而第二个语句将使其发送两个四字节字。

::

    data(1, 2, 3, 4)
    data(4, 2, 100000)

大于一字节的数据值将以低位优先格式储存在内存中。

* align(nBytes)

将以下指令与n字节值对齐。ARM Thumb-2指令须为两字节对齐，因此建议在 ``data`` 指令后、在任何后续代码前发送 ``align(2)`` 。
这将确保代码在任何数据数组为任何大小时都可运行。