
## 默认GC - jdk8  (Parallel Scavenge+Parallel Old) 注重吞吐量

-Dsun.misc.URLClassPath.disableJarChecking=true -Xms1024m -Xmx1024m -Xss512k -XX:MetaspaceSize=256m -XX:MaxMetaspaceSize=256m
-XX:+DisableExplicitGC -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintHeapAtGC -XX:+UseGCLogFileRotation
-XX:+HeapDumpOnOutOfMemoryError -XX:-OmitStackTraceInFastThrow
-Dclient.encoding.override=UTF-8 -Dfile.encoding=UTF-8
-Djava.security.egd=file:/dev/./urandom -Xloggc:/data/logs/gc/服务名称/gc.log 
-XX:NumberOfGCLogFiles=5 -XX:GCLogFileSize=5M -XX:HeapDumpPath=/data/logs/gc/服务名称/HeapDumpOnOutOfMemoryError



## 并行GC ParNew + CMS 配置  注重响应时间

-Dsun.misc.URLClassPath.disableJarChecking=true
-Xms1024m -Xmx1024m -Xss512k -XX:MetaspaceSize=256m
-XX:MaxMetaspaceSize=256m -XX:SurvivorRatio=8
-XX:+UseParNewGC -XX:ParallelGCThreads=4 -XX:MaxTenuringThreshold=9
-XX:+UseConcMarkSweepGC -XX:+DisableExplicitGC -XX:+UseCMSInitiatingOccupancyOnly
-XX:+ScavengeBeforeFullGC -XX:+UseCMSCompactAtFullCollection
-XX:+CMSParallelRemarkEnabled -XX:CMSFullGCsBeforeCompaction=9
-XX:CMSInitiatingOccupancyFraction=60 -XX:+CMSClassUnloadingEnabled
-XX:SoftRefLRUPolicyMSPerMB=0 -XX:+CMSPermGenSweepingEnabled
-XX:CMSInitiatingPermOccupancyFraction=70 -XX:+ExplicitGCInvokesConcurrent
-XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintHeapAtGC
-XX:+UseGCLogFileRotation -XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow -Dclient.encoding.override=UTF-8
-Dfile.encoding=UTF-8 -Djava.security.egd=file:/dev/./urandom
-Xloggc:/data/logs/gc/服务名称/gc.log -XX:NumberOfGCLogFiles=5
-XX:GCLogFileSize=5M -XX:HeapDumpPath=/data/logs/gc/服务名称/HeapDumpOnOutOfMemoryError


### 年轻代UseParNewGC与UseParallelGC(Parallel Scavenge)区别
 前者为并发串行GC , 仅是多线程GC ， 除性能外它可以配置年老代CMS GC配合使用
 后者为并行GC, 多线程运行在多CPU上 ，物理上并行 ， STW时间短

### 关键参数
-XX:ParallelGCThreads    			设置并发收集器新生代收集方式为并行收集时，使用的CPU数，即并行收集线程数
-XX:+UseCMSInitiatingOccupancyOnly  CMS触发阀值开启
-XX:+UseCMSCompactAtFullCollection  CMS GC进行压缩
-XX:+CMSParallelRemarkEnabled		并发标记
-XX:CMSFullGCsBeforeCompaction		运行多少次不压缩GC后，开启一次压缩 ，即开启压缩间隔
-XX:CMSInitiatingOccupancyFraction  阀值百分比
-XX:+CMSClassUnloadingEnabled		允许对类元数据进行回收





## G1 配置

-Dsun.misc.URLClassPath.disableJarChecking=true -Xms3072m -Xmx3072m -Xss512k -XX:MetaspaceSize=256m -XX:MaxMetaspaceSize=256m
-XX:+UseG1GC -XX:MaxGCPauseMillis=300 -XX:InitiatingHeapOccupancyPercent=40
-XX:+DisableExplicitGC -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+PrintHeapAtGC
-XX:+UseGCLogFileRotation -XX:+HeapDumpOnOutOfMemoryError -XX:-OmitStackTraceInFastThrow
-Dclient.encoding.override=UTF-8 -Dfile.encoding=UTF-8 -Djava.security.egd=file:/dev/./urandom
-Xloggc:/data/logs/gc/服务名称/gc.log -XX:NumberOfGCLogFiles=5 -XX:GCLogFileSize=5M -XX:HeapDumpPath=/data/logs/gc/服务名称/HeapDumpOnOutOfMemoryError

### 同CMS相比G1有以下优势:
1、可预测的停顿模型
2、避免了CMS的垃圾碎片
3、超大堆的表现更出色


### 关键参数:
-XX:MaxGCPauseMillis=200	设置期望达到的最大GC停顿时间指标（JVM会尽力实现，但不保证达到，默认200ms）




