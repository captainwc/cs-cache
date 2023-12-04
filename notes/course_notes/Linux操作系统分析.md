# Linux操作系统分析

## chapter 2

![image-20230303082839486](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303082839486.png)

---

![image-20230303082738586](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303082738586.png)

32位函数调用是通过压栈进行的，而64位则是通过寄存器传参

---

![image-20230303082805169](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303082805169.png)

可以参考[这里](https://www.cnblogs.com/beiluowuzheng/p/11326372.html)

<img src="https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/1334023-20190809115302856-2146181911.png" style="zoom: 67%;" />

---

通过`set disassemble-next-line on`，来使gdb同时输出每一步对应的汇编代码

![image-20230303092323826](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303092323826.png)

`rbp`是栈帧指针，`movl -0x14(%rbpp), %edx`，其实就是把`*(int *)(rbp - 0x14)`复制到edx。之所以是减`subl`，是因为栈是向低地址增长的。`pushl`就是先减\$4再赋值（间接寻址）的过程

其实就是对应32位的，`esp`是栈顶指针，`ebp`是栈底指针，base

**堆栈：**堆起来的栈，`movl %esp %ebp`，就是在原有栈的基础上**堆**起了一个空栈，此前要先保存现场，即`pushl %ebp`==【这里为什么是基指针呢？】==，此时ebp是调用main函数的东西，它的栈底。==这里esp还会减4==，为什么？

<img src="https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/v2-bd5a0aa1625c4445ba33e506b91dba29_r.png" style="zoom: 33%;" />

---

参考[这里](https://zhuanlan.zhihu.com/p/27339191)

![image-20230303094733922](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303094733922.png)

![image-20230303100139663](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303100139663.png)

---

直接看[ppt](D:\courses\Linux操作系统分析\ppt\2-计算机系统的基本工作原理.pdf)吧

<table style="border:none;text-align:center;">
	<tr>
		<td ><img src="https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230303103215868.png" alt="pSzbaSx.jpg" border="0" /></td>
		<td><img src="https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230308082113573.png" alt="pSzbaSx.jpg" border="0" /></td>
	</tr>
    <tr>
		<td style="width:75%"><strong>32位</strong></td>
		<td style="width:25%"><strong>64位</strong></td>

- `pop %rbq`或者`push %rbp`的时候，`%rsp`会跟着变，它始终指向栈顶
- 把sp赋值给bp，就是建立一个谁的空栈，把bp赋值给sp，就是恢复成谁谁的空栈，
- 这里，32为是通过压栈传递参数，而64位是通过寄存器传参了，因此会多一步`edi/rdi`寄存器。

---

C语言中嵌入汇编：

![image-20230308084315038](https://shuaikai-bucket0001.oss-cn-shanghai.aliyuncs.com/blog_img/image-20230308084315038.png)

---

