---
title: Spark
date: 2018-10-25 20:50:02
tags:
---

## Scala

安装Scala

https://www.scala-lang.org/

https://www.scala-lang.org/download/2.11.8.html

设置SCALA_HOME系统变量然后把scala的bin目录添加到环境变量里面

```
SCALA_HOME	C:\Program Files\Scala
PATH		%SCALA_HOME%\bin
```

```shell
$ scala
Welcome to Scala 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_172).
Type in expressions for evaluation. Or try :help.

scala>
```

scala的lazy:没有调用的时候不使用

#### 安装Idea Scala插件

https://plugins.jetbrains.com/

选择对应版本的idea就可以了（插件对应的version是idea的version）

#### Scala的函数



#### Scala的OOP

## Spark安装

#### 安装JAVA

```
JAVA_HOME	C:\Program Files\Java\jdk1.8.0_172
PATH		%JAVA_HOME%\bin
```

#### 安装Hadoop

https://archive.apache.org/dist/hadoop/common/

```
HADOOP_HOME	D:\Software\hadoop-2.6.0
PATH		%HADOOP_HOME%\bin
```

ps: 对于windows平台需要到 https://github.com/steveloughran/winutils，下载对应版本的winutils

#### 安装Scala

https://www.scala-lang.org/download/2.11.8.html

```
SCALA_HOME	C:\Program Files\Scala
PATH		%SCALA_HOME%\bin
```

#### 安装Spark

http://spark.apache.org/downloads.html

```
SPARK_HOME	D:\Software\spark-2.1.0-bin-hadoop2.6
PATH		%SPARK_HOME%\bin
```

#### 运行Spark

```shell
spark-shell --master local[2]
```

http://localhost:4040/jobs/

这样Spark就成功运行了。

edit spark conf

```shell
cp spark-env.sh.template spark-env.sh
```

spark-env.sh

```sh
SPARK_MASTER_HOST=localhost
SPARK_WORKER_CORES=4
SPARK_WORKER_MEMORY=4g
SPARK_WORKER_INSTANCES=1
```

```shell
./sbin/start-all.sh
```

 http://localhost:8080/

config multi node

```
./sbin/stop-all.sh
```

```shell
SPARK_MASTER_HOST=localhost
SPARK_WORKER_CORES=4
SPARK_WORKER_MEMORY=4g
SPARK_WORKER_INSTANCES=2
```

```shell
spark-shell --master spark://localhost:7077
```

## Spark SQL





## Spark Streaming

Spark MLlib

Spark GraphX