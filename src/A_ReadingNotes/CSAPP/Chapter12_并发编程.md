# 并发编程
并发：逻辑控制流在时间上重叠的现象。

## 应用级并发常见场景：
 - 访问慢速I/O设备
 - 与人交互
 - 通过推迟工作以降低延迟
 - 服务多个网络客户端
 - 在多核机器上进行并行计算

## 构建并发程序的机制
 - 进程
 - I/O多路复用
 - 线程

## 线程内存模型
 - 每个线程都有自己的线程上下文：线程ID、栈、栈指针、程序计数器、条件码、通用目的寄存器值 - 。
寄存器不共享、虚拟内存总是共享的

## 将变量映射到内存
全局变量：虚拟内存的读写区域只包含每个全局变量的一个实例，任何线程都可以引用。

本地自动变量：每个线程栈都包含了所有的自动变量实例。

本地静态变量：与全局变量一样

## 共享变量
若一个变量v是共享的，当且仅当它的一个实例被一个以上的线程引用。

## 信号量
P操作。若s不为0，将s减1后返回。若s为0，挂起当前线程，直到s变成非0并且被另一个V操作重启，然后将s减1后返回。

V操作。将s加1，如果此时存在由于P操作而被阻塞的线程，则重启其中唯一一个线程，然后这个线程会完成其P操作。