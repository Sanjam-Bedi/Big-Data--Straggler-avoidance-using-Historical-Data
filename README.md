# Straggler-avoidance-using-Historical-Data-in-Hadoop-multinode-cluster

## Introduction
This project implements a historical data based straggler avoidance technique in a Hadoop cluster with 3 nodes, which include 1 master node and 2 slave nodes. It has been implemented on virtual machine using Virtual Box. The aim of the project is to optimize the performance of the Hadoop cluster by identifying and mitigating stragglers.

## Installation
To use this project, you will need to have the following software installed on your machine:
- Hadoop 3.0 or later
- Python 3.x
- Java-8 or later
## Configuration
1. Before running the project, you will need to configure the Hadoop multinode cluster with 3 nodes to work with the project.
- Modify the hdfs-site.xml and core-site.xml files in the etc/hadoop directory to include the following properties:
```
<property>
   <name>mapreduce.job.reduce.slowstart.completedmaps</name>
   <value>0.7</value>
</property>
<property>
   <name>mapreduce.job.reduce.slowstart.maps</name>
   <value>3</value>
</property>
<property>
   <name>mapreduce.job.jvm.numtasks</name>
   <value>-1</value>
</property> 
```
- Modify the mapred-site.xml file in the etc/hadoop directory to include the following properties:
```
<property>
   <name>mapreduce.job.reduce.slowstart.completedmaps</name>
   <value>0.7</value>
</property>
<property>
   <name>mapreduce.job.reduce.slowstart.maps</name>
   <value>3</value>
</property>
<property>
   <name>mapreduce.job.jvm.numtasks</name>
   <value>-1</value>
</property>
```
- Configure the hadoop-env.sh file in the etc/hadoop directory to include the following lines:
```
export HADOOP_CLASSPATH=$HADOOP_CLASSPATH:/path/to/project/files
export PYTHONPATH=$PYTHONPATH:/path/to/project/files
```
## HiBench Setup and running Map Reduce 
- To simply build all modules in HiBench, use the below command. This could be time consuming because the hadoopbench relies on 3rd party tools like Mahout and Nutch. The build process automatically downloads these tools for you. If you won't run these workloads, you can only build a specific framework to speed up the build process.
```
mvn -Dspark=2.4 -Dscala=2.11 clean package
```
## Run micro bench and ML workloads in hibench
To run the micro benchmark workloads, follow these steps:
- Copy the input file to the Hadoop Distributed File System (HDFS):
```
hdfs dfs -put /path/to/input/file /input
```
- Run the Sort workload:
```
hadoop jar /path/to/hadoop-examples.jar sort /input /output
```
- Run the Wordcount workload:
```
hadoop jar /path/to/hadoop-examples.jar wordcount /input /output
```
- Run the Terasort workload:
```
hadoop jar /path/to/hadoop-examples.jar terasort /input /output
```
- Run the Sleep workload
```
hadoop jar /path/to/hadoop-examples.jar sleep -m 1 -r 1 -mt 1000 -rt 1000
```
- Run the K Means workload:
```
spark-submit /path/to/kmeans.py
```
- Run the Bayesian workload:
```
spark-submit /path/to/bayesian.py
```







