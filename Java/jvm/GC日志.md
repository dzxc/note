日志参数列表

-XX:+PrintGC 输出GC日志
-XX:+PrintGCDetails 输出GC的详细日志
-XX:+PrintGCTimeStamps 输出GC的时间戳（以基准时间的形式）
-XX:+PrintGCDateStamps 输出GC的时间戳（以日期的形式，如 2013-05-04T21:53:59.234+0800）
-XX:+PrintHeapAtGC 在进行GC的前后打印出堆的信息
-Xloggc:../logs/gc.log 日志文件的输出路径


    1.426: [GC (Allocation Failure) [PSYoungGen: 65536K->10733K(76288K)] 65536K->20311K(251392K), 0.0349677 secs] [Times: user=0.10 sys=0.02, real=0.03 secs] 
    2.359: [GC (Allocation Failure) [PSYoungGen: 76269K->10737K(141824K)] 85847K->34793K(316928K), 0.0805612 secs] [Times: user=0.11 sys=0.01, real=0.08 secs] 
    7.059: [GC (Metadata GC Threshold) [PSYoungGen: 78716K->10746K(141824K)] 102772K->48969K(316928K), 0.0453687 secs] [Times: user=0.11 sys=0.01, real=0.04 secs] 
    7.105: [Full GC (Metadata GC Threshold) [PSYoungGen: 10746K->0K(141824K)] [ParOldGen: 38222K->35195K(175104K)] 48969K->35195K(316928K), [Metaspace: 19678K->19678K(1069056K)], 0.1590183 secs] [Times: user=0.42 sys=0.01, real=0.15 secs] 
    9.498: [GC (Metadata GC Threshold) [PSYoungGen: 71067K->10728K(219136K)] 106262K->51803K(394240K), 0.0244242 secs] [Times: user=0.05 sys=0.01, real=0.02 secs] 
    9.522: [Full GC (Metadata GC Threshold) [PSYoungGen: 10728K->0K(219136K)] [ParOldGen: 41075K->44240K(202752K)] 51803K->44240K(421888K), [Metaspace: 32264K->32264K(1081344K)], 0.1425074 secs] [Times: user=0.43 sys=0.00, real=0.15 secs] 
    14.705: [GC (Metadata GC Threshold) [PSYoungGen: 148555K->10729K(272896K)] 192795K->72662K(475648K), 0.0404918 secs] [Times: user=0.10 sys=0.02, real=0.04 secs] 
    14.746: [Full GC (Metadata GC Threshold) [PSYoungGen: 10729K->0K(272896K)] [ParOldGen: 61933K->65066K(285184K)] 72662K->65066K(558080K), [Metaspace: 53636K->53636K(1099776K)], 0.4828369 secs] [Times: user=1.39 sys=0.02, real=0.48 secs] 
    21.813: [GC (Allocation Failure) [PSYoungGen: 262144K->31723K(293888K)] 327210K->110709K(579072K), 0.0782575 secs] [Times: user=0.16 sys=0.03, real=0.08 secs] 
    23.439: [GC (Metadata GC Threshold) [PSYoungGen: 113975K->36723K(299008K)] 192961K->115718K(584192K), 0.0492312 secs] [Times: user=0.13 sys=0.01, real=0.05 secs] 
    23.488: [Full GC (Metadata GC Threshold) [PSYoungGen: 36723K->0K(299008K)] [ParOldGen: 78994K->88291K(391168K)] 115718K->88291K(690176K), [Metaspace: 88846K->88846K(1134592K)], 0.3369984 secs] [Times: user=1.02 sys=0.01, real=0.34 secs] 
    
    
14.746: [Full GC (Metadata GC Threshold) [PSYoungGen: 10729K->0K(272896K)] [ParOldGen: 61933K->65066K(285184K)] 72662K->65066K(558080K), [Metaspace: 53636K->53636K(1099776K)], 0.4828369 secs] [Times: user=1.39 sys=0.02, real=0.48 secs] 


    
    