# lesson 3作业分析



目前只用sysbench的三种方式进行了压测。通过对cpu profile的分析，发现cpu的占用较多的是读写操作，但怀疑是磁盘为机械硬盘的原因导致到。具体分析过程如下。

![image-20200901234210713](picture\image-20200901234210713.png)

​																                              ***oltp_point_select的火焰图***



![image-20200901234318622](C:\Users\liuxiao23\AppData\Roaming\Typora\typora-user-images\image-20200901234318622.png)

​		这里的系统调用更是接近30%。（有点高）





![image-20200901234535684](C:\Users\liuxiao23\AppData\Roaming\Typora\typora-user-images\image-20200901234535684.png)

​																		***oltp_update_index 火焰图***

![image-20200901234752854](C:\Users\liuxiao23\AppData\Roaming\Typora\typora-user-images\image-20200901234752854.png)

这里的系统调用都是有点高的。

建议:采用batch处理，优化batch的粒度或采用异步io

提的issue : https://github.com/pingcap/tidb/issues/19685 , 感觉还不太理解，只是大胆提问哈。