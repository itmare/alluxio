##### 2.1.2. [Local Mode](https://www.alluxio.org/docs/1.8/en/Running-Alluxio-Locally.html) 또는 [Cluster Mode](https://www.alluxio.org/docs/1.8/en/Running-Alluxio-on-a-Cluster.html)로 설정 - Alluxio 다운로드

-	설치

	```shell
	# ex) wget으로 다운받기
	wget http://downloads.alluxio.org/downloads/files/1.8.1/alluxio-1.8.1-hadoop-2.9-bin.tar.gz
	```

-	advanced user는 직접 [source code](https://www.alluxio.org/docs/1.8/en/Building-Alluxio-From-Source.html#compute-framework-support) 수정 할 수 있음

#### 2.2. Additional setup for HDFS

-	Alluxio가 zookeeper를 사용해 fault tolerant에서 작동한다면

	-	`${SPARK_HOME}/conf/spark-defaults.conf`에 다음을 추가

		```shell
		spark.driver.extraJavaOptions -Dalluxio.zookeeper.address=zookeeperHost1:2181,zookeeperHost2:2181 -Dalluxio.zookeeper.enabled=true
		spark.executor.extraJavaOptions -Dalluxio.zookeeper.address=zookeeperHost1:2181,zookeeperHost2:2181 -Dalluxio.zookeeper.enabled=true
		```

	-	또는 이전에 생성된 hadoop configuration file `${SPARK_HOME}/conf/core-site.xml`에 다음을 추가

		```xml
		<configuration>
		    <property>
		        <name>alluxio.zookeeper.enabled</name>
		    <value>true</value>
		    </property>
		    <property>
		        <name>alluxio.zookeeper.address</name>
		        <value>[zookeeper_hostname]:2181</value>
		    </property>
		</configuration>
		```

### 3. Check Spark with Alluxio integration (Supports Spark 2.x)

### 4. Use Alluxio as Input and Output

-	Using Data Already in Alluxio - Using Data from HDFS - Using Fault Tolerant Mode

### 5. Data Locality

-	Running Spark on YARN

### 6. `Class alluxio.hadoop.FileSystem not found` Issues with SparkSQL and Hive MetaStore

### 7. `java.io.IOException: No FileSystem for scheme: alluxio` Issue with Spark on YARN
