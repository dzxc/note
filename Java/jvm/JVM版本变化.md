# JVM 
|JVM|说明|
|---|---|
|HotSpot|Longview Technologies开发 被SUN收购，2006年 Java开源 并建立OpenJDK，HotSpot  成为Sun JDK和OpenJDK中所带的虚拟机，2010年Oracle 收购 Sun得到Hotspot|
|JRockit VM|2008 年 Oracle收购BEA得到JRockit VM，Oracle宣布在JDK8时整合JRockit和Hotspot，优势互补，在Hotspot基础上，移植JRockit优秀特性|
|KVM|SUN发布，IOS Android前，广泛用于手机系统CDC/CLDC手机、电子书、PDA等设备上建立统一的Java编程接口，J2ME的重要组成部分|
|IBM J9 VM|IBM内部使用|
|Apache Harmony|兼容于JDK 1.5和JDK 1.6的Java程序运行平台，与Oracle关系恶劣 退出JCP ，Java社区的分裂，OpenJDK出现后，受到挑战 2011年 退役|没有大规模商用经历|

# JVM 规范

Java语言规范定义了什么是Java语言
Java语言和JVM相对独立

Groovy
Clojure
Scala
JVM主要定义二进制class文件和JVM指令集等



#### Class 文件格式
数字的内部表示和存储
Byte  -128 to 127 (-27 to 27 - 1)
returnAddress 数据类型定义
指向操作码的指针。不对应Java数据类型，不能在运行时修改。Finally实现需要




一些特殊的方法
<clinit>
<init>


#### VM指令集
类型转化
l2i  
出栈入栈操作
aload  astore
运算
iadd  isub
流程控制
ifeq ifne
函数调用
invokevirtual invokeinterface  invokespecial  invokestatic 


#### JVM需要对Java Library 提供以下支持：
反射 java.lang.reflect
ClassLoader
初始化class和interface
安全相关 java.security
多线程
弱引用

JVM的编译
源码到JVM指令的对应格式
Javap
JVM反汇编的格式
<index> <opcode> [ <operand1> [ <operand2>... ]] [<comment>]

---

    void spin() {
      int i; 
      for (i = 0; i < 100; i++) { ;
         // Loop body is empty
       }
     } 
    

    0   iconst_0       // Push int constant 0
    1   istore_1       // Store into local variable 1 (i=0)
    2   goto 8         // First time through don't increment
    5   iinc 1 1       // Increment local variable 1 by 1 (i++)
    8   iload_1        // Push local variable 1 (i)
    9   bipush 100     // Push int constant 100
    11  if_icmplt 5    // Compare and loop if less than (i < 100)
    14  return         // Return void when done

