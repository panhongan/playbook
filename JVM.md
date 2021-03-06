**[G1]**  
1.G1常用的配置参数
```
-Xms8g
-Xmx8g
-XX:+UseG1GC
-XX:MaxGCPauseMillis=200
-XX:G1HeapRegionSize=4m
-XX:InitiatingHeapOccupancyPercent=65
-XX:MaxDirectMemorySize=8g
-XX:MetaspaceSize=128m

-XX:+ExitOnOutOfMemoryError
-XX:+HeapDumpOnOutOfMemoryError

-XX:ParallelGCThreads=10
-XX:ConcGCThreads=3
-XX:+PrintGCDetails
-XX:+PrintGCDateStamps
-Xloggc:<gc file>
-XX:UseGCLogFileRotation
-XX:NumberOfGCLogFiles=10
-XX:GCLogFileSize=100m

-Djava.io.tmpdir=<tmp dir>
-Dfile.encoding=UTF-8
-Duser.timezone=UTC
```
<br></br>

2.G1配置后检查要点  
```
1. Young gc time cost 和Young gc frequency
2. 是否出现大对象分配，关键字：Humongous Allocation
3. major gc frequency
4. Humongous Allocation
5. 是否出现 Metadata space expansion, 伴随Full GC
```
<br></br>

3.常用JVM命令
```
查看默认GC: java -XX:+PrintCommandLineFlags -version
查看JVM参数默认初始值：java -XX:+PrintFlagsInitial
查看JVM参数最新值：java -XX:+PrintFlagsFinal
```
<br></br>

4.classpath覆盖  
```
覆盖默认的classpath文件（一般在resources目录）：
1). java -cp <新classpath路径>:<老的classpath> <main class> <args>
新classpath要放在老classpath之前，搜索第一个符合即可.

2). java -Xbootclasspath/a:<自定义classpath> -jar xx.jar
不建议使用 -Xbootclasspath/p，有系统风险。
```
<br></br>

5. 
