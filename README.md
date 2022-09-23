## Spark Cluster for OSX M1

#### Desc
This script for spark-cluster working on M1 machine.


#### Build Docker Image
build -t cluster-apache-saprk-m1:3.3.0 .

#### Excute Spark Job
docker exec -it spark-build-spark-master-1 /opt/spark/bin/spark-submit \
--driver-class-path /opt/spark-apps/mysql-connector-java-5.1.44.jar \
--class com.yg.horus.dt.topic.LdaJobMain \
--master spark://spark-master:7077 \
--num-executors 3 --executor-memory 2g --total-executor-cores 6 \
--conf spark.dynamicAllocation.enabled=false \
/opt/spark-apps/HorusDT-assembly-0.1.5-SNAPSHOT.jar LDA_TOPIC_0 spark://spark-master:7077 21 60 10 10
