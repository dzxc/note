### GC参数
垃圾收集器相关的常用参数

|参    数|描    述|
|---||
|UseSerialGC|虚拟机运行在Client模式下的默认值，打开此开关后，使用Serial + Serial Old的收集器组合进行内存回收|
|UseParNewGC|打开此开关后，使用ParNew + Serial Old的收集器组合进行内存回收|
|UseConcMarkSweepGC|打开此开关后，使用ParNew + CMS + Serial Old的收集器组合进行内存 回收。Serial Old收集器将作为CMS收集器出现Concurrent Mode Failure 失败后的后备收集器使用|
|UseParallelGC|虚拟机运行在Server模式下的畎认值，打开此开关后，使用Parallel Scavenge + Serial Old CPS MarkSweep)的收集器组合进行内存回收|
|UseParallelOldGC|打开此开关后，使用Parallel Scavenge + Parallel Old的收集器级合进行 内存回收|
|SurvivorRatio|新生代中Eden区域与Survivor区域的容量比值，默认为8,代表 Eden : Survivor=8 : 1|
|PretenureSizeThreshold|直接晋升到老年代的对象大小，设置这个参数后，大于这个参数的对象 将直接在老年代分配|
|MaxTenuringThreshold|晋升到老年代的对象年龄.每个对象在坚持过一次MinwOC之后，年 龄就增加1.当超过这个参数值时就进人老年代|
|UseAdaptiveSizePolicy|动态调整Java堆中各个区域的大小以及进人老年代的年龄|
|HandlePromolionFailure|是否允许分配担保失败，即老年代的刺余空间不足以应付新生代的整个 Eden和Survivor区的所有对象部存活的极端悄况|
|GCTimeRatio|GC时间占总时间的比率，默认值为99,即允许1%的GC时间，仅在 使用Parallel Scavenge收集器时生效|
|MaxGCPauseMillis|设置GC的最大停頓时间。仅在使用Parallel Scavenge收集器时生效|
|CMSlnitiatingOccupancyFraclion|没置CMS收集器在老年代空间被使用多少后触发垃圾收集。默认值为 68%,仅在使用CMS收集器时生效|
|UseCMSCompactAlFullCollection|设置CMS收集器在完成垃圾收集后是否要进行一次内存碎片整理。仅 在使用CMS收集器时生效|
|CMSFullGCsBcforeCompaction|设罝CMS收集器在进行若干次垃圾收集后再启动一次内存碎片整理。 仅在使用CMS收集器时生效|



### 日志参数列表

-XX:+PrintGC 输出GC日志
-XX:+PrintGCDetails 输出GC的详细日志
-XX:+PrintGCTimeStamps 输出GC的时间戳（以基准时间的形式）
-XX:+PrintGCDateStamps 输出GC的时间戳（以日期的形式，如 2013-05-04T21:53:59.234+0800）
-XX:+PrintHeapAtGC 在进行GC的前后打印出堆的信息
-Xloggc:../logs/gc.log 日志文件的输出路径


    
    CommandLine flags: -XX:InitialHeapSize=268435456 -XX:MaxHeapSize=1073741824 -XX:+PrintGC -XX:+PrintGCDateStamps -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+UseParallelGC 
    2018-08-26T09:54:15.829-0800: 1.540: [GC (Allocation Failure) [PSYoungGen: 65536K->10733K(76288K)] 65536K->20308K(251392K), 0.0364459 secs] [Times: user=0.08 sys=0.01, real=0.04 secs] 
    2018-08-26T09:54:16.719-0800: 2.431: [GC (Allocation Failure) [PSYoungGen: 76269K->10721K(141824K)] 85844K->34754K(316928K), 0.0461743 secs] [Times: user=0.12 sys=0.01, real=0.05 secs] 
    2018-08-26T09:54:21.269-0800: 6.980: [GC (Metadata GC Threshold) [PSYoungGen: 78522K->10747K(141824K)] 102555K->48966K(316928K), 0.0472953 secs] [Times: user=0.13 sys=0.02, real=0.05 secs] 
    2018-08-26T09:54:21.317-0800: 7.028: [Full GC (Metadata GC Threshold) [PSYoungGen: 10747K->0K(141824K)] [ParOldGen: 38219K->45314K(175104K)] 48966K->45314K(316928K), [Metaspace: 19654K->19654K(1069056K)], 0.1417794 secs] [Times: user=0.40 sys=0.01, real=0.14 secs] 
    2018-08-26T09:54:23.849-0800: 9.560: [GC (Metadata GC Threshold) [PSYoungGen: 69644K->10728K(215040K)] 114958K->62039K(390144K), 0.0405109 secs] [Times: user=0.06 sys=0.01, real=0.04 secs] 
    2018-08-26T09:54:23.889-0800: 9.601: [Full GC (Metadata GC Threshold) [PSYoungGen: 10728K->0K(215040K)] [ParOldGen: 51310K->44320K(217088K)] 62039K->44320K(432128K), [Metaspace: 32307K->32307K(1081344K)], 0.2018016 secs] [Times: user=0.51 sys=0.01, real=0.21 secs] 
    2018-08-26T09:54:29.092-0800: 14.803: [GC (Metadata GC Threshold) [PSYoungGen: 152523K->10729K(272896K)] 196844K->72703K(489984K), 0.0417986 secs] [Times: user=0.10 sys=0.01, real=0.04 secs] 
    2018-08-26T09:54:29.134-0800: 14.845: [Full GC (Metadata GC Threshold) [PSYoungGen: 10729K->0K(272896K)] [ParOldGen: 61974K->65037K(309760K)] 72703K->65037K(582656K), [Metaspace: 53515K->53515K(1099776K)], 0.4497831 secs] [Times: user=1.35 sys=0.02, real=0.45 secs] 
    2018-08-26T09:54:36.101-0800: 21.812: [GC (Allocation Failure) [PSYoungGen: 262144K->31714K(286720K)] 327181K->109171K(596480K), 0.0957566 secs] [Times: user=0.16 sys=0.03, real=0.09 secs] 
    2018-08-26T09:54:37.858-0800: 23.569: [GC (Metadata GC Threshold) [PSYoungGen: 119939K->38183K(297472K)] 197395K->115647K(607232K), 0.0467158 secs] [Times: user=0.12 sys=0.01, real=0.05 secs] 
    2018-08-26T09:54:37.905-0800: 23.616: [Full GC (Metadata GC Threshold) [PSYoungGen: 38183K->0K(297472K)] [ParOldGen: 77464K->89782K(433664K)] 115647K->89782K(731136K), [Metaspace: 88766K->88766K(1134592K)], 0.4243974 secs] [Times: user=1.01 sys=0.02, real=0.42 secs] 

2018-08-26T09:54:37.858-0800当前时间戳）: 
23.569（时间戳）: 
[GC（新生代 GC） (Metadata GC Threshold) 
[PSYoungGen(Parallel Scavenge 新生代收集器): 
119939K（新生代回收前的大小）->38183K（新生代回收后的大小）(297472K（新生代总大小）)] 
197395K（堆回收前的大小）->115647K（堆回收后的大小）(607232K（堆总大小）), 0.0467158 secs（回收的时间）] [Times: user=0.12（用户耗时） sys=0.01系统耗时）, real=0.05 secs实际耗时）] 

    
    