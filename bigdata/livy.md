<!---
title: Livy
header: Livy 入门
--->

[官方资料](http://livy.io/)

[官方例子](https://github.com/cloudera/livy#spark-example)

----
[参考资料](http://terrence.logdown.com/posts/1172854-zeppelin-livy-server-supports-multiple-users-review)



## 安裝步驟

先假設Hadoop環境跟Zeppelin都已經準備好了，這邊只專注在Livy的搭建

### 在Hadoop環境新增一個帳號livy
我這邊使用LDAP當作Hadoop帳號來源，因此我直接在LDAP上新增就好

修改core-site.xml
新增設定如下

```
hadoop.proxyuser.livy.groups=*
hadoop.proxyuser.livy.hosts=*
```

這是為了讓livy帳號可以代替其他帳號發起request



### 編譯Livy

```
$sudo su - livy
$git clone git@github.com:cloudera/livy.git
$cd livy
$mvn -Dspark.version=1.6.1 -DskipTests clean package
```


- vim conf/livy.conf

設定livy的conf

```
...
livy.spark.master = yarn-client
livy.impersonation.enabled = true
livy.repl.enableHiveContext = true
livy.server.host = 0.0.0.0
livy.server.port = 8998
livy.server.session.factory = yarn
livy.impersonation.enabled = true
vim conf/livy-env.sh
export HADOOP_CONF_DIR=/etc/hadoop/conf
export SPARK_HOME=${YOUR_SPARK_HOME}
export LIVY_SERVER_JAVA_OPTS="-Xms1024m -Xmx2g"
```

- vim conf/spark-blacklist.conf

註解掉spark.master的黑名單

```
#spark.master
```

- vim conf/log4j.properties

```
log4j.rootCategory=INFO, file
log4j.appender.console=org.apache.log4j.ConsoleAppender
log4j.appender.console.target=System.err
log4j.appender.console.layout=org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern=%d{yy/MM/dd HH:mm:ss} %p %c{1}: %m%n
 
log4j.appender.file=org.apache.log4j.RollingFileAppender
log4j.appender.file.File=${YOUR_LOG_DIR}/livy.log
log4j.appender.file.MaxFileSize=200MB
log4j.appender.file.MaxBackupIndex=10
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n
 
log4j.logger.org.eclipse.jetty=WARN
```

## 啟動Livy

`$bin/livy-server &`


## 從Zeppelin設定Livy interpreter
參考[Livy Interpreter](https://zeppelin.apache.org/docs/0.6.0/interpreter/livy.html)
個人的設定類似如下

```
livy.spark.driver.cores 1
livy.spark.driver.memory  2g
livy.spark.dynamicAllocation.cachedExecutorIdleTimeout  120
livy.spark.dynamicAllocation.enabled  true
livy.spark.dynamicAllocation.initialExecutors 2
livy.spark.dynamicAllocation.maxExecutors 30
livy.spark.dynamicAllocation.minExecutors 2
livy.spark.executor.memory 2g
livy.spark.executor.cores 1
livy.spark.master yarn-client
livy.spark.shuffle.service.enabled  true
zeppelin.livy.concurrentSQL true
zeppelin.livy.url http://localhost:8998
```

上面完成後，使用下面的code測試

```
%livy.spark
sc.version
```

應該可以看到一個是Zeppelin登入帳號啟動的Spark application