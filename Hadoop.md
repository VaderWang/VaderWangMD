---
title: Hadoop
date: 2018-10-23 20:50:11
tags:
---

## Hadoop

https://archive.apache.org/dist/hadoop/core/hadoop-2.7.3/

下载 hadoop-2.7.3.tar.gz

SSH公钥生成

```shell
ssh-keygen
```

一路enter即可

```shell
vaderwang@vaderwang-X399:~/.ssh$ ll
total 24
drwx------  2 vaderwang vaderwang 4096 Nov  9 12:47 ./
drwxr-xr-x 58 vaderwang vaderwang 4096 Nov  9 10:13 ../
-rw-r--r--  1 vaderwang vaderwang 2876 Nov  9 12:44 authorized_keys
-rw-------  1 vaderwang vaderwang 1675 Oct 27 10:18 id_rsa
-rw-r--r--  1 vaderwang vaderwang  418 Oct 27 10:18 id_rsa.pub
-rw-r--r--  1 vaderwang vaderwang 2876 Nov  9 12:44 known_hosts
```

生成SSH公钥后，把公钥的内容复制到authorized_keys文件中

```shell
vaderwang@vaderwang-X399:~/.ssh$ cat id_rsa.pub >> authorized_keys
```

修改文件权限

```shell
vaderwang@vaderwang-X399:~/.ssh$ chmod 600 authorized_keys 
```

测试SSH免密登陆

```shell
vaderwang@vaderwang-X399:~/.ssh$ ssh localhost
Welcome to Ubuntu 18.04.1 LTS (GNU/Linux 4.15.0-38-generic x86_64)
```

配置jdk

```shell
tar -zxf jdk-8u144-linux-x64.tar.gz 
```

```shell
 sudo mv jdk1.8.0_144/ /usr/local/
```

```shell
sudo vim /etc/profile
```

```
export JAVA_HOME=/usr/local/jdk1.8.0_144
export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH
```

```shell
source /etc/profile
```

配置Hadoop

```shell
tar -zxf hadoop-2.7.3.tar.gz
```

修改 hadoop-env.sh

```sh
# export JAVA_HOME=${JAVA_HOME}
```

修改 hdfs-site.xml

```xml
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>1</value>
  </property> 
  <property>
    <name>dfs.namenode.name.dir</name>
    <value>file:/home/vaderwang/hadoop_data/dfs/name</value>
  </property> 
  <property>
    <name>dfs.datanode.data.dir</name>
    <value>file:/home/vaderwang/hadoop_data/dfs/data</value>
  </property> 
</configuration>
```

修改 core-site.xml

```xml
<configuration>
  <property>
    <name>hadoop.tmp.dir</name>
    <value>file:/home/vaderwang/hadoop_data</value>
  </property> 
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://0.0.0.0:9000</value>
  </property> 
</configuration>
```

```shell
./bin/hdfs namenode -format
```

````shell
./sbin/start-dfs.sh
````





ps：gitignore

```
/dist/
/node_modules/
```

### HDFS

### MapReduce



## Hbase

https://archive.apache.org/dist/hbase/1.2.4/

下载 hbase-1.2.4-bin.tar.gz

```shell
vaderwang@vaderwang-X399:~/software$ tar zxf hbase-1.2.4-bin.tar.gz
```

hdfs-site.xml和core-site.xml移动到hbase的配置文件目录

配置 hbase-env.sh

```sh
export JAVA_HOME=/usr/local/jdk1.8.0_144/
```

```sh
# Configure PermSize. Only needed in JDK7. You can safely remove it for JDK8+
# export HBASE_MASTER_OPTS="$HBASE_MASTER_OPTS -XX:PermSize=128m -XX:MaxPermSize=128m"
# export HBASE_REGIONSERVER_OPTS="$HBASE_REGIONSERVER_OPTS -XX:PermSize=128m -XX:MaxPermSize=128m"
```

配置 hbase-site.xml

```xml
<configuration>
  <property>
    <name>hbase.rootdir</name>
    <value>hdfs://localhost:9000/hbase</value>
  </property> 
  <property>
    <name>hbase.zookeeper.property.dataDir</name>
    <value>/home/vaderwang/hadoop_data/zookeeper</value>
  </property> 
  <property>
    <name>hbase.cluster.distributed</name>
    <value>true</value>
  </property>
</configuration>
```

```shell
vaderwang@vaderwang-X399:~/software/hbase-1.2.4/bin$ ./start-hbase.sh 
```

```shell
vaderwang@vaderwang-X399:~/software/hbase-1.2.4/bin$ ./hbase shell
```





